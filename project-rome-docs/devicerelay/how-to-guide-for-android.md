---
title: Comando para dispositivos remotos y aplicaciones (Android)
description: En esta guía se muestra cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicaciones.
ms.topic: article
keywords: microsoft, windows, project rome, commanding, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: bb58b8340dcd8158a201ce670ef0b69ba0272b6f
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "76115570"
---
# <a name="implementing-device-relay-for-android"></a>Implementación de Retransmisión de dispositivos para Android

La funcionalidad Retransmisión de dispositivo de Project Rome se compone de un conjunto de API que admiten dos características principales: el inicio remoto (también llamado comando) y los servicios de aplicaciones.

Las API de inicio remoto admiten escenarios en los que se inicia un proceso en un dispositivo remoto desde un dispositivo local. Por ejemplo, un usuario escucha la radio en su teléfono cuando está en el coche, y cuando llega a casa usa el teléfono para transferir la lista de reproducción a su Xbox, que está conectada al equipo de música de la casa.

Las API de App Services permiten a una aplicación establecer una canalización persistente entre dos dispositivos a través de la cual se pueden enviar mensajes que contienen cualquier contenido arbitrario. Por ejemplo, una aplicación para compartir fotos que se ejecuta en un dispositivo móvil podría establecer una conexión con el equipo del usuario para recuperar fotos.

Las características de Project Rome son compatibles con una plataforma subyacente, la plataforma de dispositivos conectados. En esta guía se proporcionan los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y se explica cómo usar la plataforma para implementar las características relacionadas con la retransmisión de dispositivo.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Uso de la plataforma

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Detección de aplicaciones y dispositivos remotos

Una instancia de **RemoteSystemWatcher** controlará la funcionalidad básica de esta sección. Declárala en la clase que se usa para detectar los sistemas remotos.

```Java
private RemoteSystemWatcher mWatcher = null;
```

Antes de crear un monitor e iniciar la detección de dispositivos, es posible que desees agregar filtros de detección para determinar los tipos de dispositivos a los que se dirigirá la aplicación. Los filtros se pueden determinar mediante una entrada del usuario, o bien se pueden codificar de forma rígida en la aplicación, según el uso.

```Java
private void onStartWatcherClicked() {
    // RemoteSystemWatcher cannot be started unless the platform is 
    // initialized and the user is logged in. It may be helpful to use
    // methods like these to track the state of the application.
    // See the sample app for their implementations.
    if (!getMainActivity().isSignedIn()) {
        return;
    }
    if (!getMainActivity().isPlatformInitialized()) {
        return;
    }

    // create and populate a list of filters. The filter choices below are arbitrary.
    ArrayList<RemoteSystemFilter> filters = new ArrayList<>();

    /*  RemoteSystemDiscoveryType filters can be used to filter the types of Remote Systems you discover.
    Possible values:
        ANY(0),
        PROXIMAL(1),
        CLOUD(2),
        SPATIALLY_PROXIMAL(3)
    */
    filters.add(new RemoteSystemDiscoveryTypeFilter(RemoteSystemDiscoveryType.ANY));

    /*  RemoteSystemStatusType filters can be used to filter the status of Remote Systems you discover.
    Possible values:
        ANY(0),
        AVAILABLE(1)
    */
    filters.add(new RemoteSystemStatusTypeFilter(RemoteSystemStatusType.AVAILABLE));


    /*  RemoteSystemKindFilter can filter the types of devices you want to discover.
    Possible values are members of the RemoteSystemKinds class.
    */
    String[] kinds = new String[] { RemoteSystemKinds.Phone(), RemoteSystemKinds.Tablet() };

    RemoteSystemKindFilter kindFilter = new RemoteSystemKindFilter(kinds);
    filters.add(kindFilter);

    /*  RemoteSystemAuthorizationKind determines the category of user whose system(s) you want to discover.
    Possible values:
        SAME_USER(0),
        ANONYMOUS(1)
    */
    filters.add(new RemoteSystemAuthorizationKindFilter(RemoteSystemAuthorizationKind.SAME_USER)); 
    // ...
```

En este punto, la aplicación puede inicializar el objeto de monitor que determina cómo la aplicación analizará e interactuará con los dispositivos que se detecten.

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por instancias de **RemoteSystem**) y muestre información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el nombre para mostrar y el tipo de dispositivo) en la interfaz de usuario. 

Los siguientes códigos auxiliares de clase pueden utilizarse como agentes de escucha de eventos para la instancia del monitor.

```Java
private class RemoteSystemAddedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // add instance "remoteSystem" to program memory. See sample for full implementation.
    }
}

private class RemoteSystemUpdatedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // update instance "remoteSystem" in program memory. See sample for full implementation.
    }
}

private class RemoteSystemRemovedListener implements EventListener<RemoteSystemWatcher, RemoteSystem> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystem remoteSystem) {
        // remove instance "remoteSystem" from program memory. See sample for full implementation.
    }
}

private class RemoteSystemWatcherErrorOccurredListener implements EventListener<RemoteSystemWatcher, RemoteSystemWatcherError> {
    @Override
    public void onEvent(RemoteSystemWatcher remoteSystemWatcher, RemoteSystemWatcherError remoteSystemWatcherError) {
        // handle the error
    }
}
```

Cuando se llama a `mWatcher.start`, comenzará por inspeccionar la actividad del sistema remoto y generará eventos cuando los dispositivos se detecten, actualicen o quiten del conjunto de dispositivos detectados. Realizará un examen continuo en segundo plano, por lo que se recomienda detener el monitor cuando ya no se necesite para evitar un consumo innecesario de batería y comunicación de red.

```Java
// if you call this from the activity's onPause method, you ensure that
// it will stop when the activity exits the foreground.
public void stopWatcher() {
    if (mWatcher == null) {
        return;
    }
    mWatcher.stop();
}
```
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Caso de uso de ejemplo: Implementación del inicio remoto y los servicios de aplicaciones remotas

A estas alturas, en el código debes tener una lista de trabajo de objetos de **RemoteSystem** que hacen referencia a los dispositivos disponibles. Lo que hagas con estos dispositivos dependerá de la función de la aplicación. Los principales tipos de interacción son el inicio remoto y los servicios de aplicación remota. Estos tipos se explican en las siguientes secciones.

### <a name="a-remote-launching"></a>A) Inicio remoto

El código siguiente muestra cómo seleccionar uno de los dispositivos (lo ideal es que esto se realice mediante un control de interfaz de usuario) y, después, usar **RemoteLauncher** para iniciar una aplicación en él al pasar un URI compatible con la aplicación. 

Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema de URI) _o_ una aplicación remota específica en ese dispositivo. 

Como se demostró en la sección anterior, la detección ocurre primero a nivel de dispositivo (una instancia de **RemoteSystem** representa un dispositivo), pero puedes llamar al método `getApplications` en una instancia de **RemoteSystem** para obtener una matriz de objetos **RemoteSystemApp**, que representan aplicaciones en el dispositivo remoto que han sido registradas para usar la plataforma de dispositivos conectados (de la misma manera que registró su propia aplicación en los pasos preliminares anteriores). Tanto **RemoteSystem**como **RemoteSystemApp** pueden utilizarse para construir una instancia de **RemoteSystemConnectionRequest**, que es lo que se necesita para lanzar un URI.

```java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the launch operation
// is called.
private RemoteSystem target; 

// ...

/**
* Responsible for calling into the Rome API to launch the given URI and provides
* the logic to handle the RemoteLaunchUriStatus response.
* @param uri URI to launch
* @param target The target for the launch URI request
*/
private void launchUri(final String uri, final RemoteSystem target, final long messageId)
{
    RemoteLauncher remoteLauncher = new RemoteLauncher();

    AsyncOperation<RemoteLaunchUriStatus> resultOperation = remoteLauncher.launchUriAsync(new RemoteSystemConnectionRequest(target), uri);
    // ...
```
Utilice la instancia de **AsyncOperation** devuelta para controlar el resultado del intento de inicio.

```Java
    // ...
    resultOperation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<RemoteLaunchUriStatus, Throwable>() {
        @Override
        public void accept(RemoteLaunchUriStatus status, Throwable throwable) throws Throwable {
            if (throwable != null) {
                // handle the exception, referencing "throwable"
            } else {
                if (status == RemoteLaunchUriStatus.SUCCESS) {
                    // report the success case
                } else {
                    // report the non-success case, referencing "status"
                }
            }
        }
    });
}
```
Dependiendo de la URI que se envíe, puedes iniciar una aplicación en un estado o configuración específicos en un dispositivo remoto. Esto proporciona la posibilidad de continuar una tarea de usuario, como ver una película, en otro dispositivo sin interrupción. 

Según el caso de uso, es posible que tengas que cubrir casos en los que ninguna aplicación del sistema de destino puede manejar el URI o en los que varias aplicaciones pueden manejarlo. Las clases **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** y **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** describen cómo hacerlo.

### <a name="b-remote-app-services"></a>B) Servicios de aplicaciones remotas

La aplicación de Android puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicaciones en otros dispositivos. Esto proporciona muchas maneras de comunicarse con otros dispositivos; todas ellas sin necesidad de traer una aplicación al primer plano del dispositivo host. 

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configuración del servicio de aplicaciones en el dispositivo de destino
En esta guía se utiliza [Roman Test App para Windows](https://aka.ms/romeapp) como servicio de aplicación de destino. Por lo tanto, el siguiente código hará que una aplicación de Android busque ese servicio de aplicación específico en el sistema remoto indicado. Si deseas probar este escenario, descarga la aplicación Roman Test App en un dispositivo Windows y asegúrate de haber iniciado sesión con la misma MSA que en los pasos preliminares anteriores. 

Para obtener instrucciones sobre cómo escribir tu propio servicio de aplicación UWP, consulta [Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Tendrás que hacer algunos cambios para que el servicio sea compatible con los dispositivos conectados. Consulta la [guía UWP para los servicios de aplicaciones remotas](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Apertura de una conexión del servicio de aplicación en el dispositivo cliente
La aplicación de Android debe adquirir una referencia a una aplicación o dispositivo remoto. Al igual que la sección de inicio, este escenario requiere el uso de una instancia de **RemoteSystemConnectionRequest**, que puede construirse a partir de instancia de **RemoteSystem** o de **RemoteSystemApp** que represente una aplicación disponible en el sistema.


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
Además, tu aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre del servicio de aplicación* y el *identificador del paquete*. Estas cadenas se encuentran en el código fuente del proveedor de servicios de aplicaciones; consulta [Crear y consumir un servicio de aplicación (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para ver más información sobre cómo obtenerlas para los servicios de aplicaciones de Windows. Juntas, estas cadenas construyen **AppServiceDescription**, que se introduce en una instancia de **AppServiceConnection**.

```Java
// this is defined below
private AppServiceConnection connection = null; 


/**
* Creates an AppService connection with the current identifier and service name and opens the
* app service connection.
*/
private void onNewConnectionButtonClicked()
{
    connection = new AppServiceConnection();

    // these hard-coded strings must be defined elsewhere in the app
    connection.setAppServiceDescription(new AppServiceDescription(mAppServiceName, mPackageIdentifier));

    // this method is defined below
    openAppServiceConnection();
}
```
```Java
/**
* Establish an app service connection.
* Opens the given AppService connection using the connection request. Once the connection is
* opened, it adds the listeners for request-received and close. Catches all exceptions
* to show behavior of API surface exceptions.
*/
private void openAppServiceConnection()
{
    // optionally report outbound request
    // ...

    RemoteSystemConnectionRequest connectionRequest = new RemoteSystemConnectionRequest(target));

    /* Will asynchronously open the app service connection using the given connection request
    * When this is done, we log the traffic in the UI for visibility to the user (for sample purposes)
    * We can check the status of the connection to determine whether or not it was successful, and show 
    * some UI if it wasn't (in this case it is part of the list item).
    */
    connection.openRemoteAsync(connectionRequest)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceConnectionStatus>() {
            @Override
            public void accept(AppServiceConnectionStatus appServiceConnectionStatus) throws Throwable {
                // optionally report inbound response
                // ...

                if (appServiceConnectionStatus != AppServiceConnectionStatus.SUCCESS) {
                    // report the error, referencing "appServiceConnectionStatus"
                    return;
                }
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception
                return null;
            }
        });
}
```

#### <a name="create-a-message-to-send-to-the-app-service"></a>Creación de un mensaje para enviar al servicio de aplicación

Declara una variable para almacenar el mensaje que se va a enviar. En Android, los mensajes que se envían a los servicios de aplicación remota serán del tipo **Map**.

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> Cuando la aplicación se comunica con servicios de aplicación en otras plataformas, la plataforma de dispositivos conectados convierte el objeto **Map** a la construcción correspondiente en la plataforma de recepción. Por ejemplo, un objeto **[Map](https://developer.android.com/reference/java/util/Map)** enviada desde esta aplicación a un servicio de aplicación de Windows se convierte en un objeto [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) (de .NET Framework), que luego el servicio de aplicación puede interpretar. La información pasada en la otra dirección sufre una conversión inversa.

El siguiente método compone un mensaje que puede ser interpretado por el servicio de aplicación de Roman Test App para Windows.

```Java
/**
* Send the current message payload through all selected AppService connections on a non-UI
* thread as to not block user interaction, a result of the delay between API calls.
*/
private void onMessageButtonClicked()
{
    mMessagePayload = new HashMap<>();
    // Add the required fields of RomanApp on Windows
    DateFormat df = new SimpleDateFormat(DATE_FORMAT);
    mMessagePayload.put("Type", "ping");
    mMessagePayload.put("CreationDate", df.format(new Date()));
    mMessagePayload.put("TargetId", "check if this field needs to be included");

    // this method is defined below.
    sendMessage(connection, mMessagePayload);
}
```

> [!IMPORTANT]
> Los objetos **Map** que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben seguir el siguiente formato: Las claves deben ser cadenas, y los valores pueden ser: Cadenas, tipos numéricos con conversión boxing (enteros o de punto flotante), booleanos con conversión boxing, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, matrices homogéneas de cualquiera de estos tipos u otros objetos **Map** que cumplan esta especificación.

#### <a name="send-message-to-the-app-service"></a>Envío de un mensaje al servicio de aplicación

Una vez establecida la conexión al servicio de aplicación y creado el mensaje, enviarlo al servicio de aplicación es sencillo y puede realizarse desde cualquier lugar de la aplicación que tenga una referencia a la instancia de conexión del servicio de aplicación y al mensaje.


```java

// When assigning message IDs, use an incremental counter
private AtomicInteger mMessageIdAppServices = new AtomicInteger(0);

// ...

/**
* Send a message using the app service connection
* Send the given Map object through the given AppServiceConnection. Uses an internal messageId
* for logging purposes.
* @param connection AppServiceConnection to send the Map payload
* @param message Payload to be translated to a ValueSet
*/
private void sendMessage(final AppServiceConnection connection, Map<String, Object> message)
{
    final long messageId = mMessageIdAppServices.incrementAndGet();

    connection.sendMessageAsync(message)
        .thenAcceptAsync(new AsyncOperation.ResultConsumer<AppServiceResponse>() {
            @Override
            public void accept(AppServiceResponse appServiceResponse) throws Throwable {
                // optionally report an inbound response

                // this method is defined below
                handleAppServiceResponse(appServiceResponse, messageId);
            }
        })
        .exceptionally(new AsyncOperation.ResultFunction<Throwable, Void>() {
            @Override
            public Void apply(Throwable throwable) throws Throwable {
                // report the exception, referencing "throwable"

                return null;
            }
        });

    // optionally log the outbound message request here, referencing 
    // connection.getAppServiceDescription().getName() as the recipient.
}
```

La respuesta del servicio de aplicación se recibirá e interpretará con el siguiente método.

```Java
private void handleAppServiceResponse(AppServiceResponse appServiceResponse, long messageId)
{
    AppServiceResponseStatus status = appServiceResponse.getStatus();
    if (status == AppServiceResponseStatus.SUCCESS)
    {
        // the message was delivered successfully; interpret the response.
        Map<String, Object> response;
        response = appServiceResponse.getMessage();

        // in the Roman App case, the response contains the date it was created.
        String dateStr = (String)response.get("CreationDate");
        DateFormat df = new SimpleDateFormat(DATE_FORMAT, Locale.getDefault());

        // in this very simple use case, we compare the dates to get the total
        // transit time of the message response.
        try {
            Date startDate = df.parse(dateStr);
            Date nowDate = new Date();
            long diff = nowDate.getTime() - startDate.getTime();
            // do something with "diff"
        } catch (ParseException e) { e.printStackTrace(); }
    }
}
```
En el caso de Roman App, la respuesta contiene la fecha en que fue creada, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo total de tránsito de la respuesta del mensaje.

Esto concluye un intercambio de un solo mensaje con un servicio de aplicación remota.

#### <a name="finish-app-service-communication"></a>Finalización de la comunicación del servicio de aplicación

Cuando la aplicación termine de interactuar con el servicio de aplicación del dispositivo de destino, cierra la conexión entre los dos dispositivos.

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a>Temas relacionados
* [Página de referencia de API](api-reference-for-android.md) 
* [Aplicación de ejemplo de Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [Comunicación con un servicio de aplicación remota (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).
