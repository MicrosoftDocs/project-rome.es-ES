---
title: Comando para dispositivos remotos y aplicaciones (Android)
description: En esta guía se muestra cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicaciones.
ms.topic: article
keywords: microsoft, windows, project rome, commanding, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: ce261c6571e4606ddcb8e1c2b75d989db51d8d9f
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901583"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="811de-104">Implementación de Retransmisión de dispositivos para Android</span><span class="sxs-lookup"><span data-stu-id="811de-104">Implementing device relay for Android</span></span>

<span data-ttu-id="811de-105">La funcionalidad Retransmisión de dispositivo de Project Rome se compone de un conjunto de API que admiten dos características principales: el inicio remoto (también llamado comando) y los servicios de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="811de-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="811de-106">Las API de inicio remoto admiten escenarios en los que se inicia un proceso en un dispositivo remoto desde un dispositivo local.</span><span class="sxs-lookup"><span data-stu-id="811de-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="811de-107">Por ejemplo, un usuario escucha la radio en su teléfono cuando está en el coche, y cuando llega a casa usa el teléfono para transferir la lista de reproducción a su Xbox, que está conectada al equipo de música de la casa.</span><span class="sxs-lookup"><span data-stu-id="811de-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="811de-108">Las API de App Services permiten a una aplicación establecer una canalización persistente entre dos dispositivos a través de la cual se pueden enviar mensajes que contienen cualquier contenido arbitrario.</span><span class="sxs-lookup"><span data-stu-id="811de-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="811de-109">Por ejemplo, una aplicación para compartir fotos que se ejecuta en un dispositivo móvil podría establecer una conexión con el equipo del usuario para recuperar fotos.</span><span class="sxs-lookup"><span data-stu-id="811de-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="811de-110">Las características de Project Rome son compatibles con una plataforma subyacente, la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="811de-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="811de-111">En esta guía se proporcionan los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y se explica cómo usar la plataforma para implementar las características relacionadas con la retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="811de-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="811de-112">Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="811de-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="811de-113">Uso de la plataforma</span><span class="sxs-lookup"><span data-stu-id="811de-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="811de-114">Detección de aplicaciones y dispositivos remotos</span><span class="sxs-lookup"><span data-stu-id="811de-114">Discover remote devices and apps</span></span>

<span data-ttu-id="811de-115">Una instancia de **RemoteSystemWatcher** controlará la funcionalidad básica de esta sección.</span><span class="sxs-lookup"><span data-stu-id="811de-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="811de-116">Declárala en la clase que se usa para detectar los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="811de-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="811de-117">Antes de crear un monitor e iniciar la detección de dispositivos, es posible que desees agregar filtros de detección para determinar los tipos de dispositivos a los que se dirigirá la aplicación.</span><span class="sxs-lookup"><span data-stu-id="811de-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="811de-118">Los filtros se pueden determinar mediante una entrada del usuario, o bien se pueden codificar de forma rígida en la aplicación, según el uso.</span><span class="sxs-lookup"><span data-stu-id="811de-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

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

<span data-ttu-id="811de-119">En este punto, la aplicación puede inicializar el objeto de monitor que determina cómo la aplicación analizará e interactuará con los dispositivos que se detecten.</span><span class="sxs-lookup"><span data-stu-id="811de-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="811de-120">Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por instancias de **RemoteSystem**) y muestre información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el nombre para mostrar y el tipo de dispositivo) en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="811de-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="811de-121">Los siguientes códigos auxiliares de clase pueden utilizarse como agentes de escucha de eventos para la instancia del monitor.</span><span class="sxs-lookup"><span data-stu-id="811de-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

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

<span data-ttu-id="811de-122">Cuando se llama a `mWatcher.start`, comenzará por inspeccionar la actividad del sistema remoto y generará eventos cuando los dispositivos se detecten, actualicen o quiten del conjunto de dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="811de-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="811de-123">Realizará un examen continuo en segundo plano, por lo que se recomienda detener el monitor cuando ya no se necesite para evitar un consumo innecesario de batería y comunicación de red.</span><span class="sxs-lookup"><span data-stu-id="811de-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="811de-124">Caso de uso de ejemplo: Implementación del inicio remoto y los servicios de aplicaciones remotas</span><span class="sxs-lookup"><span data-stu-id="811de-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="811de-125">A estas alturas, en el código debes tener una lista de trabajo de objetos de **RemoteSystem** que hacen referencia a los dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="811de-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="811de-126">Lo que hagas con estos dispositivos dependerá de la función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="811de-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="811de-127">Los principales tipos de interacción son el inicio remoto y los servicios de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="811de-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="811de-128">Estos tipos se explican en las siguientes secciones.</span><span class="sxs-lookup"><span data-stu-id="811de-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="811de-129">A) Inicio remoto</span><span class="sxs-lookup"><span data-stu-id="811de-129">A) Remote launching</span></span>

<span data-ttu-id="811de-130">El código siguiente muestra cómo seleccionar uno de los dispositivos (lo ideal es que esto se realice mediante un control de interfaz de usuario) y, después, usar **RemoteLauncher** para iniciar una aplicación en él al pasar un URI compatible con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="811de-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="811de-131">Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema de URI) _o_ una aplicación remota específica en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="811de-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="811de-132">Como se demostró en la sección anterior, la detección ocurre primero a nivel de dispositivo (una instancia de **RemoteSystem** representa un dispositivo), pero puedes llamar al método `getApplications` en una instancia de **RemoteSystem** para obtener una matriz de objetos **RemoteSystemApp**, que representan aplicaciones en el dispositivo remoto que han sido registradas para usar la plataforma de dispositivos conectados (de la misma manera que registró su propia aplicación en los pasos preliminares anteriores).</span><span class="sxs-lookup"><span data-stu-id="811de-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="811de-133">Tanto **RemoteSystem** como **RemoteSystemApp** pueden utilizarse para construir una instancia de **RemoteSystemConnectionRequest**, que es lo que se necesita para lanzar un URI.</span><span class="sxs-lookup"><span data-stu-id="811de-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

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
<span data-ttu-id="811de-134">Utilice la instancia de **AsyncOperation** devuelta para controlar el resultado del intento de inicio.</span><span class="sxs-lookup"><span data-stu-id="811de-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

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
<span data-ttu-id="811de-135">Dependiendo de la URI que se envíe, puedes iniciar una aplicación en un estado o configuración específicos en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="811de-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="811de-136">Esto proporciona la posibilidad de continuar una tarea de usuario, como ver una película, en otro dispositivo sin interrupción.</span><span class="sxs-lookup"><span data-stu-id="811de-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="811de-137">Según el caso de uso, es posible que tengas que cubrir casos en los que ninguna aplicación del sistema de destino puede manejar el URI o en los que varias aplicaciones pueden manejarlo.</span><span class="sxs-lookup"><span data-stu-id="811de-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="811de-138">Las clases **[RemoteLauncher](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** y **[RemoteLauncherOptions](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** describen cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="811de-138">The **[RemoteLauncher](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="811de-139">B) Servicios de aplicaciones remotas</span><span class="sxs-lookup"><span data-stu-id="811de-139">B) Remote app services</span></span>

<span data-ttu-id="811de-140">La aplicación de Android puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicaciones en otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="811de-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="811de-141">Esto proporciona muchas maneras de comunicarse con otros dispositivos; todas ellas sin necesidad de traer una aplicación al primer plano del dispositivo host.</span><span class="sxs-lookup"><span data-stu-id="811de-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="811de-142">Configuración del servicio de aplicaciones en el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="811de-142">Set up the app service on the target device</span></span>
<span data-ttu-id="811de-143">En esta guía se utiliza [Roman Test App para Windows](https://aka.ms/romeapp) como servicio de aplicación de destino.</span><span class="sxs-lookup"><span data-stu-id="811de-143">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="811de-144">Por lo tanto, el siguiente código hará que una aplicación de Android busque ese servicio de aplicación específico en el sistema remoto indicado.</span><span class="sxs-lookup"><span data-stu-id="811de-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="811de-145">Si deseas probar este escenario, descarga la aplicación Roman Test App en un dispositivo Windows y asegúrate de haber iniciado sesión con la misma MSA que en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="811de-145">If you wish to test this scenario,download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="811de-146">Para obtener instrucciones sobre cómo escribir tu propio servicio de aplicación para UWP, consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="811de-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="811de-147">Tendrás que hacer algunos cambios para que el servicio sea compatible con los dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="811de-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="811de-148">Consulta la [guía UWP para los servicios de aplicaciones remotas](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="811de-148">See the [UWP guide for remote app services](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="811de-149">Apertura de una conexión del servicio de aplicación en el dispositivo cliente</span><span class="sxs-lookup"><span data-stu-id="811de-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="811de-150">La aplicación de Android debe adquirir una referencia a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="811de-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="811de-151">Al igual que la sección de inicio, este escenario requiere el uso de una instancia de **RemoteSystemConnectionRequest**, que puede construirse a partir de instancia de **RemoteSystem** o de **RemoteSystemApp** que represente una aplicación disponible en el sistema.</span><span class="sxs-lookup"><span data-stu-id="811de-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="811de-152">Además, tu aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre del servicio de aplicación* y el *identificador del paquete*.</span><span class="sxs-lookup"><span data-stu-id="811de-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="811de-153">Estas cadenas se encuentran en el código fuente del proveedor de servicios de aplicaciones; consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para ver más información sobre cómo obtenerlas para los servicios de aplicaciones de Windows.</span><span class="sxs-lookup"><span data-stu-id="811de-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="811de-154">Juntas, estas cadenas construyen **AppServiceDescription**, que se introduce en una instancia de **AppServiceConnection**.</span><span class="sxs-lookup"><span data-stu-id="811de-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

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

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="811de-155">Creación de un mensaje para enviar al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="811de-155">Create a message to send to the app service</span></span>

<span data-ttu-id="811de-156">Declara una variable para almacenar el mensaje que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="811de-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="811de-157">En Android, los mensajes que se envían a los servicios de aplicación remota serán del tipo **Map**.</span><span class="sxs-lookup"><span data-stu-id="811de-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="811de-158">Cuando la aplicación se comunica con servicios de aplicación en otras plataformas, la plataforma de dispositivos conectados convierte el objeto **Map** a la construcción correspondiente en la plataforma de recepción.</span><span class="sxs-lookup"><span data-stu-id="811de-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="811de-159">Por ejemplo, un objeto **[Map](https://developer.android.com/reference/java/util/Map)** enviada desde esta aplicación a un servicio de aplicación de Windows se convierte en un objeto [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) (de .NET Framework), que luego el servicio de aplicación puede interpretar.</span><span class="sxs-lookup"><span data-stu-id="811de-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="811de-160">La información pasada en la otra dirección sufre una conversión inversa.</span><span class="sxs-lookup"><span data-stu-id="811de-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="811de-161">El siguiente método compone un mensaje que puede ser interpretado por el servicio de aplicación de Roman Test App para Windows.</span><span class="sxs-lookup"><span data-stu-id="811de-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="811de-162">Los objetos **Map** que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben seguir el siguiente formato: Las claves deben ser cadenas, y los valores pueden ser: Cadenas, tipos numéricos con conversión boxing (enteros o de punto flotante), booleanos con conversión boxing, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, matrices homogéneas de cualquiera de estos tipos u otros objetos **Map** que cumplan esta especificación.</span><span class="sxs-lookup"><span data-stu-id="811de-162">The **Map** s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="811de-163">Envío de un mensaje al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="811de-163">Send message to the app service</span></span>

<span data-ttu-id="811de-164">Una vez establecida la conexión al servicio de aplicación y creado el mensaje, enviarlo al servicio de aplicación es sencillo y puede realizarse desde cualquier lugar de la aplicación que tenga una referencia a la instancia de conexión del servicio de aplicación y al mensaje.</span><span class="sxs-lookup"><span data-stu-id="811de-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


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

<span data-ttu-id="811de-165">La respuesta del servicio de aplicación se recibirá e interpretará con el siguiente método.</span><span class="sxs-lookup"><span data-stu-id="811de-165">The app service's response will be received and interpreted by the following method.</span></span>

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
<span data-ttu-id="811de-166">En el caso de Roman App, la respuesta contiene la fecha en que fue creada, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo total de tránsito de la respuesta del mensaje.</span><span class="sxs-lookup"><span data-stu-id="811de-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="811de-167">Esto concluye un intercambio de un solo mensaje con un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="811de-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="811de-168">Finalización de la comunicación del servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="811de-168">Finish app service communication</span></span>

<span data-ttu-id="811de-169">Cuando la aplicación termine de interactuar con el servicio de aplicación del dispositivo de destino, cierra la conexión entre los dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="811de-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="811de-170">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="811de-170">Related topics</span></span>
* [<span data-ttu-id="811de-171">Página de referencia de API</span><span class="sxs-lookup"><span data-stu-id="811de-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="811de-172">Aplicación de ejemplo de Android</span><span class="sxs-lookup"><span data-stu-id="811de-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="811de-173">Comunicación con un servicio de aplicación remota (UWP)</span><span class="sxs-lookup"><span data-stu-id="811de-173">Communicate with a remote app service (UWP)</span></span>](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="811de-174">[Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="811de-174">[Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>