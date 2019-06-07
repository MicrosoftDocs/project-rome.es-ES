---
title: Comando dispositivos remotos y aplicaciones (Android)
description: Esta guía le mostrará cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicación.
ms.topic: article
keywords: Microsoft, windows, proyecto Roma, comandos, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 9ca9caf60c59c619d1f7ec4e7b3af529acbb2ffc
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755746"
---
# <a name="implementing-device-relay-for-android"></a>Implementación de retransmisión de dispositivos para Android

La funcionalidad de retransmisión de dispositivo de Roma proyecto consta de un conjunto de API que admiten dos características principales: iniciar remoto (también conocido como comandos) y los servicios de aplicación.

API de inicio remoto admiten escenarios donde se inicia un proceso en un dispositivo remoto desde un dispositivo local. Por ejemplo, un usuario podría estar escuchando en la radio en su teléfono en el automóvil, pero cuando llegue a casa usan su teléfono para transferir la reproducción a su Xbox que está enlazado al equipo de música doméstico.

API de servicios de aplicaciones permiten que una aplicación establecer una canalización persistente entre los dos dispositivos a través del cual se pueden enviar los mensajes que contienen cualquier contenido arbitrario. Por ejemplo, una foto en la aplicación que se ejecuta en un dispositivo móvil para uso compartido podría establecer una conexión con el equipo del usuario con el fin de recuperar las fotos.

Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados. Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, se explica cómo usar la plataforma para implementar el dispositivo de retransmisión características relacionadas.

Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Con la plataforma

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Detectar aplicaciones y dispositivos remotos

Un **RemoteSystemWatcher** instancia controlará la funcionalidad básica de esta sección. Declararla de la clase que se usa para detectar los sistemas remotos.

```Java
private RemoteSystemWatcher mWatcher = null;
```

Antes de crear un monitor e iniciar la detección de dispositivos, desea agregar filtros de detección para determinar qué tipos de dispositivos de destino de la aplicación. Estos se pueden determinar por usuario de entrada o codificado de forma rígida en la aplicación, según el caso de uso.

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

En este momento, la aplicación puede inicializar el objeto de monitor que determinan cómo la aplicación analizará e interactuar con dispositivos detectados.

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por **RemoteSystem** instancias) y mostrar información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el tipo de nombre y el dispositivo de visualización) en la interfaz de usuario. 

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

Una vez `mWatcher.start` es llamado, comenzará a inspeccionando la actividad del sistema remoto y genera eventos cuando los dispositivos se detectan, actualizados o quitados del conjunto de los dispositivos detectados. Examinará continuamente en segundo plano, por lo que se recomienda detener el monitor cuando ya no necesite para evitar la purga de comunicación y la batería de red innecesario.

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Caso de uso de ejemplo: implementar el inicio remoto y los servicios de RemoteApp

En este momento en el código, debe tener una lista de trabajo de **RemoteSystem** objetos que hacen referencia a los dispositivos disponibles. Qué hacer con estos dispositivos dependerá de la función de la aplicación. Los tipos principales de interacción son Inicio remoto y los servicios de aplicación remota. Se explican en las secciones siguientes.

### <a name="a-remote-launching"></a>A) iniciar remoto

El código siguiente muestra cómo seleccionar uno de estos dispositivos (lo ideal es que esto se realiza a través de un control de interfaz de usuario) y, a continuación, usar **RemoteLauncher** para iniciar una aplicación en ella pasando un identificador URI de la aplicación compatible. 

Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo de host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema URI) _o_ una aplicación remota específica en ese dispositivo. 

Como se muestra la sección anterior, detección se produce en el nivel de dispositivo en primer lugar (un **RemoteSystem** representa un dispositivo), pero se puede llamar a la `getApplications` método en un **RemoteSystem** instancia para obtener una matriz de **RemoteSystemApp** objetos que representan las aplicaciones en el dispositivo remoto que se han registrado para usar la plataforma de dispositivos conectados (tal como se registró su propia aplicación en los pasos preliminares anteriores). Ambos **RemoteSystem** y **RemoteSystemApp** puede usarse para construir un **RemoteSystemConnectionRequest**, que es lo que hace falta para iniciar un URI.

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
Utilice el valor devuelto **AsyncOperation** para controlar el resultado del intento de inicio.

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
Según el URI que se envía, puede iniciar una aplicación en un estado específico o una configuración en un dispositivo remoto. Esto permite la capacidad de seguir una tarea de usuario, como ver una película en un dispositivo diferente sin interrupción. 

Según el caso de uso, es posible que deba cubrir los casos en que no hay ninguna aplicación en el sistema de destino puede controlar el identificador URI o varias aplicaciones pueden controlarla. El **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** clase y **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** clase describen cómo hacer esto.

### <a name="b-remote-app-services"></a>B) servicios de aplicación remoto

La aplicación Android puede usar el Portal de dispositivos conectados interactuar con los servicios de aplicación en otros dispositivos. Esto proporciona muchas formas de comunicarse con otros dispositivos&mdash;todo ello sin necesidad de llevar una aplicación en primer plano del dispositivo host. 

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurar el servicio de aplicaciones en el dispositivo de destino
Esta guía utilizará el [Roman prueba de aplicaciones para Windows](http://aka.ms/romeapp) como servicio de aplicación de destino. Por lo tanto, el código siguiente hará que una aplicación Android para buscar dicho servicio de aplicación específica en el sistema remoto determinado. Si desea probar este escenario, descargue la aplicación de prueba romanos en un dispositivo de Windows y asegúrese de que ha iniciado sesión con el mismo MSA que usó en los pasos preliminares anteriores. 

Para obtener instrucciones sobre cómo escribir su propio servicio de aplicación para UWP, consulte [crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Deberá realizar algunos cambios con el fin de que el servicio sea compatible con dispositivos conectados. Consulte la [guía UWP para los servicios de aplicación remota](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Abrir una conexión de servicio de aplicación en el dispositivo de cliente
La aplicación Android debe adquirir una referencia a una aplicación o dispositivo remoto. Al igual que la sección de inicio, este escenario requiere el uso de un **RemoteSystemConnectionRequest**, que puede crearse desde un **RemoteSystem** o un **RemoteSystemApp**que representa una aplicación disponible en el sistema.


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
Además, la aplicación necesitará identificar su servicio de aplicación de destino utilizando dos cadenas: el *nombre de app service* y *identificador de paquete*. Estos se encuentran en el código fuente del proveedor de servicios de aplicación (consulte [crear y consumir un servicio de aplicación (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener más información sobre cómo obtener esto cadenas para los servicios de aplicación de Windows). Juntas construyen estas cadenas el **AppServiceDescription**, que se introducen en un **AppServiceConnection** instancia.

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

#### <a name="create-a-message-to-send-to-the-app-service"></a>Crear un mensaje para enviar al servicio de aplicación

Declare una variable para almacenar el mensaje para enviar. En Android, los mensajes que se envían a los servicios de aplicación remota será de la **mapa** tipo.

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> Cuando la aplicación se comunica con servicios de aplicaciones en otras plataformas, la plataforma de dispositivos conectados traduce el **mapa** en la construcción coincidente en la plataforma de destino. Por ejemplo, un **[mapa](https://developer.android.com/reference/java/util/Map)** enviados desde esta aplicación a un Windows servicio de aplicación se traduce en un [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objeto (de .NET Framework), que, a continuación, se puede interpretar el servicio de aplicación. Información que se pasa en la otra dirección se somete a la traducción inversa.

El siguiente método redacta un mensaje que se puede interpretar por servicio de aplicación de la aplicación de prueba Roman para Windows.

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
> El **mapa**s que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota debe cumplir el formato siguiente: Las claves deben ser cadenas, y los valores pueden ser: Cadenas, caja de conversión boxing de tipos numéricos (enteros o punto flotante), valores booleanos, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, matrices homogéneas de cualquiera de estos tipos u otros **mapa** objetos que cumple esta especificación.

#### <a name="send-message-to-the-app-service"></a>Enviar mensaje al servicio de aplicación

Una vez establecida la conexión de servicio de aplicación y se crea el mensaje, enviarlo a app service es sencillo y se puede realizar desde cualquier lugar en la aplicación que tiene una referencia a la instancia de conexión de servicio de aplicación y el mensaje.


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

Se recibió respuesta del servicio de aplicación e interpretada por el método siguiente.

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
En el caso de romano App, la respuesta contiene la fecha de creación, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo de tránsito total de la respuesta del mensaje.

Esto concluye un intercambio de mensajes solo con un servicio de aplicación remota.

#### <a name="finish-app-service-communication"></a>Finalizar la comunicación del servicio de aplicación

Cuando finalice la aplicación interactúa con el servicio de aplicación del dispositivo de destino, cierre la conexión entre los dos dispositivos.

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
* [Comunicarse con un servicio de aplicación remota (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).
