---
title: Comando dispositivos remotos y aplicaciones (Android)
description: Esta guía le mostrará cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicación.
ms.topic: article
keywords: Microsoft, windows, proyecto Roma, comandos, android
ms.assetid: 2fd14dd0-0f1f-49ee-83e3-468737810c81
ms.localizationpriority: medium
ms.openlocfilehash: 78cb712d3b1cbbd3d613a45cd42af491eaa33afc
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907767"
---
# <a name="implementing-device-relay-for-android"></a><span data-ttu-id="5f921-104">Implementación de retransmisión de dispositivos para Android</span><span class="sxs-lookup"><span data-stu-id="5f921-104">Implementing device relay for Android</span></span>

<span data-ttu-id="5f921-105">La funcionalidad de retransmisión de dispositivo de Roma proyecto consta de un conjunto de API que admiten dos características principales: iniciar remoto (también conocido como comandos) y los servicios de aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f921-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="5f921-106">API de inicio remoto admiten escenarios donde se inicia un proceso en un dispositivo remoto desde un dispositivo local.</span><span class="sxs-lookup"><span data-stu-id="5f921-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="5f921-107">Por ejemplo, un usuario podría estar escuchando en la radio en su teléfono en el automóvil, pero cuando llegue a casa usan su teléfono para transferir la reproducción a su Xbox que está enlazado al equipo de música doméstico.</span><span class="sxs-lookup"><span data-stu-id="5f921-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="5f921-108">API de servicios de aplicaciones permiten que una aplicación establecer una canalización persistente entre los dos dispositivos a través del cual se pueden enviar los mensajes que contienen cualquier contenido arbitrario.</span><span class="sxs-lookup"><span data-stu-id="5f921-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="5f921-109">Por ejemplo, una foto en la aplicación que se ejecuta en un dispositivo móvil para uso compartido podría establecer una conexión con el equipo del usuario con el fin de recuperar las fotos.</span><span class="sxs-lookup"><span data-stu-id="5f921-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="5f921-110">Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="5f921-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="5f921-111">Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, se explica cómo usar la plataforma para implementar el dispositivo de retransmisión características relacionadas.</span><span class="sxs-lookup"><span data-stu-id="5f921-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement Device Relay related features.</span></span>

<span data-ttu-id="5f921-112">Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="5f921-112">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="5f921-113">Con la plataforma</span><span class="sxs-lookup"><span data-stu-id="5f921-113">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="5f921-114">Detectar aplicaciones y dispositivos remotos</span><span class="sxs-lookup"><span data-stu-id="5f921-114">Discover remote devices and apps</span></span>

<span data-ttu-id="5f921-115">Un **RemoteSystemWatcher** instancia controlará la funcionalidad básica de esta sección.</span><span class="sxs-lookup"><span data-stu-id="5f921-115">A **RemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="5f921-116">Declararla de la clase que se usa para detectar los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="5f921-116">Declare it in the class which is to discover remote systems.</span></span>

```Java
private RemoteSystemWatcher mWatcher = null;
```

<span data-ttu-id="5f921-117">Antes de crear un monitor e iniciar la detección de dispositivos, desea agregar filtros de detección para determinar qué tipos de dispositivos de destino de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f921-117">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="5f921-118">Estos se pueden determinar por usuario de entrada o codificado de forma rígida en la aplicación, según el caso de uso.</span><span class="sxs-lookup"><span data-stu-id="5f921-118">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

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

<span data-ttu-id="5f921-119">En este momento, la aplicación puede inicializar el objeto de monitor que determinan cómo la aplicación analizará e interactuar con dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="5f921-119">At this point, the app can initialize the watcher object which determine how your app will parse and interact with devices that are discovered.</span></span>

```Java
    // ...

    // Create a RemoteSystemWatcher
    mWatcher = new RemoteSystemWatcher(filters.toArray(new RemoteSystemFilter[filters.size()]));
    }

    // ...
```

<span data-ttu-id="5f921-120">Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por **RemoteSystem** instancias) y mostrar información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el tipo de nombre y el dispositivo de visualización) en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="5f921-120">It is recommended that your app maintain a set of discovered devices (represented by **RemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="5f921-121">Los siguientes códigos auxiliares de clase pueden utilizarse como agentes de escucha de eventos para la instancia del monitor.</span><span class="sxs-lookup"><span data-stu-id="5f921-121">The following class stubs can be used as event listeners for the watcher instance.</span></span>

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

<span data-ttu-id="5f921-122">Una vez `mWatcher.start` es llamado, comenzará a inspeccionando la actividad del sistema remoto y genera eventos cuando los dispositivos se detectan, actualizados o quitados del conjunto de los dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="5f921-122">Once `mWatcher.start` is called, it will begin watching for remote system activity and will raise events when devices are discovered, updated, or removed from the set of discovered devices.</span></span> <span data-ttu-id="5f921-123">Examinará continuamente en segundo plano, por lo que se recomienda detener el monitor cuando ya no necesite para evitar la purga de comunicación y la batería de red innecesario.</span><span class="sxs-lookup"><span data-stu-id="5f921-123">It will scan continuously in the background, so it is recommended that you stop the watcher when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

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
## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="5f921-124">Caso de uso de ejemplo: implementar el inicio remoto y los servicios de RemoteApp</span><span class="sxs-lookup"><span data-stu-id="5f921-124">Example use case: implementing remote launching and remote app services</span></span>

<span data-ttu-id="5f921-125">En este momento en el código, debe tener una lista de trabajo de **RemoteSystem** objetos que hacen referencia a los dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="5f921-125">At this point in your code, you should have a working list of **RemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="5f921-126">Qué hacer con estos dispositivos dependerá de la función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f921-126">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="5f921-127">Los tipos principales de interacción son Inicio remoto y los servicios de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="5f921-127">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="5f921-128">Se explican en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="5f921-128">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="5f921-129">A) iniciar remoto</span><span class="sxs-lookup"><span data-stu-id="5f921-129">A) Remote launching</span></span>

<span data-ttu-id="5f921-130">El código siguiente muestra cómo seleccionar uno de estos dispositivos (lo ideal es que esto se realiza a través de un control de interfaz de usuario) y, a continuación, usar **RemoteLauncher** para iniciar una aplicación en ella pasando un identificador URI de la aplicación compatible.</span><span class="sxs-lookup"><span data-stu-id="5f921-130">The following code shows how to select one of these devices (ideally this is done through a UI control) and then use **RemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span> 

<span data-ttu-id="5f921-131">Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo de host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema URI) _o_ una aplicación remota específica en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5f921-131">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span> 

<span data-ttu-id="5f921-132">Como se muestra la sección anterior, detección se produce en el nivel de dispositivo en primer lugar (un **RemoteSystem** representa un dispositivo), pero se puede llamar a la `getApplications` método en un **RemoteSystem** instancia para obtener una matriz de **RemoteSystemApp** objetos que representan las aplicaciones en el dispositivo remoto que se han registrado para usar la plataforma de dispositivos conectados (tal como se registró su propia aplicación en los pasos preliminares anteriores).</span><span class="sxs-lookup"><span data-stu-id="5f921-132">As the previous section demonstrated, discovery happens at the device level first (a **RemoteSystem** represents a device), but you can call the `getApplications` method on a **RemoteSystem** instance to get an array of **RemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="5f921-133">Ambos **RemoteSystem** y **RemoteSystemApp** puede usarse para construir un **RemoteSystemConnectionRequest**, que es lo que hace falta para iniciar un URI.</span><span class="sxs-lookup"><span data-stu-id="5f921-133">Both **RemoteSystem** and **RemoteSystemApp** can be used to construct a **RemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

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
<span data-ttu-id="5f921-134">Utilice el valor devuelto **AsyncOperation** para controlar el resultado del intento de inicio.</span><span class="sxs-lookup"><span data-stu-id="5f921-134">Use the returned **AsyncOperation** to handle the result of the launch attempt.</span></span>

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
<span data-ttu-id="5f921-135">Según el URI que se envía, puede iniciar una aplicación en un estado específico o una configuración en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="5f921-135">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="5f921-136">Esto permite la capacidad de seguir una tarea de usuario, como ver una película en un dispositivo diferente sin interrupción.</span><span class="sxs-lookup"><span data-stu-id="5f921-136">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span> 

<span data-ttu-id="5f921-137">Según el caso de uso, es posible que deba cubrir los casos en que no hay ninguna aplicación en el sistema de destino puede controlar el identificador URI o varias aplicaciones pueden controlarla.</span><span class="sxs-lookup"><span data-stu-id="5f921-137">Depending on your use case, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="5f921-138">El **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** clase y **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** clase describen cómo hacer esto.</span><span class="sxs-lookup"><span data-stu-id="5f921-138">The **[RemoteLauncher](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher)** class and **[RemoteLauncherOptions](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.commanding._remote_launcher_options)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="5f921-139">B) servicios de aplicación remoto</span><span class="sxs-lookup"><span data-stu-id="5f921-139">B) Remote app services</span></span>

<span data-ttu-id="5f921-140">La aplicación Android puede usar el Portal de dispositivos conectados interactuar con los servicios de aplicación en otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5f921-140">Your Android app can use the Connected Devices Portal interact with app services on other devices.</span></span> <span data-ttu-id="5f921-141">Esto proporciona muchas formas de comunicarse con otros dispositivos&mdash;todo ello sin necesidad de llevar una aplicación en primer plano del dispositivo host.</span><span class="sxs-lookup"><span data-stu-id="5f921-141">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span> 

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="5f921-142">Configurar el servicio de aplicaciones en el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="5f921-142">Set up the app service on the target device</span></span>
<span data-ttu-id="5f921-143">Esta guía utilizará el [Roman prueba de aplicaciones para Windows](http://aka.ms/romeapp) como servicio de aplicación de destino.</span><span class="sxs-lookup"><span data-stu-id="5f921-143">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="5f921-144">Por lo tanto, el código siguiente hará que una aplicación Android para buscar dicho servicio de aplicación específica en el sistema remoto determinado.</span><span class="sxs-lookup"><span data-stu-id="5f921-144">Therefore, the code below will cause an Android app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="5f921-145">Si desea probar este escenario, descargue la aplicación de prueba romanos en un dispositivo de Windows y asegúrese de que haya iniciado sesión con el mismo MSA o AAD que usó en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="5f921-145">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA or AAD that you used in the preliminary steps above.</span></span> 

<span data-ttu-id="5f921-146">Para obtener instrucciones sobre cómo escribir su propio servicio de aplicación para UWP, consulte [crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="5f921-146">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="5f921-147">Deberá realizar algunos cambios con el fin de que el servicio sea compatible con dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="5f921-147">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="5f921-148">Consulte la [guía UWP para los servicios de aplicación remota](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="5f921-148">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="5f921-149">Abrir una conexión de servicio de aplicación en el dispositivo de cliente</span><span class="sxs-lookup"><span data-stu-id="5f921-149">Open an app service connection on the client device</span></span>
<span data-ttu-id="5f921-150">La aplicación Android debe adquirir una referencia a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="5f921-150">Your Android app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="5f921-151">Al igual que la sección de inicio, este escenario requiere el uso de un **RemoteSystemConnectionRequest**, que puede crearse desde un **RemoteSystem** o un **RemoteSystemApp**que representa una aplicación disponible en el sistema.</span><span class="sxs-lookup"><span data-stu-id="5f921-151">Like the launch section, this scenario requires the use of a **RemoteSystemConnectionRequest**, which can be constructed from either a **RemoteSystem** or a **RemoteSystemApp** representing an available app on the system.</span></span>


```Java
// this could be a RemoteSystemApp instead. Either way, it 
// must be defined somewhere in the application before the app service
// connection is opened.
private RemoteSystem target = null;
```
<span data-ttu-id="5f921-152">Además, la aplicación necesitará identificar su servicio de aplicación de destino utilizando dos cadenas: el *nombre de app service* y *identificador de paquete*.</span><span class="sxs-lookup"><span data-stu-id="5f921-152">Additionally, your app will need to identify its targeted app service using two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="5f921-153">Estos se encuentran en el código fuente del proveedor de servicios de aplicación (consulte [crear y consumir un servicio de aplicación (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener más información sobre cómo obtener esto cadenas para los servicios de aplicación de Windows).</span><span class="sxs-lookup"><span data-stu-id="5f921-153">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details on how to get this strings for Windows app services).</span></span> <span data-ttu-id="5f921-154">Juntas construyen estas cadenas el **AppServiceDescription**, que se introducen en un **AppServiceConnection** instancia.</span><span class="sxs-lookup"><span data-stu-id="5f921-154">Together these strings construct the **AppServiceDescription**, which is fed into an **AppServiceConnection** instance.</span></span>

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

#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="5f921-155">Crear un mensaje para enviar al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="5f921-155">Create a message to send to the app service</span></span>

<span data-ttu-id="5f921-156">Declare una variable para almacenar el mensaje para enviar.</span><span class="sxs-lookup"><span data-stu-id="5f921-156">Declare a variable to store the message to send.</span></span> <span data-ttu-id="5f921-157">En Android, los mensajes que se envían a los servicios de aplicación remota será de la **mapa** tipo.</span><span class="sxs-lookup"><span data-stu-id="5f921-157">On Android, the messages that you send to remote app services will be of the **Map** type.</span></span>

```Java
private Map<String, Object> mMessagePayload = null;
```
> [!NOTE]
> <span data-ttu-id="5f921-158">Cuando la aplicación se comunica con servicios de aplicaciones en otras plataformas, la plataforma de dispositivos conectados traduce el **mapa** en la construcción coincidente en la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="5f921-158">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **Map** into the matching construct on the receiving platform.</span></span> <span data-ttu-id="5f921-159">Por ejemplo, un **[mapa](https://developer.android.com/reference/java/util/Map)** enviados desde esta aplicación a un Windows servicio de aplicación se traduce en un [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objeto (de .NET Framework), que, a continuación, se puede interpretar el servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f921-159">For example, a **[Map](https://developer.android.com/reference/java/util/Map)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="5f921-160">Información que se pasa en la otra dirección se somete a la traducción inversa.</span><span class="sxs-lookup"><span data-stu-id="5f921-160">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="5f921-161">El siguiente método redacta un mensaje que se puede interpretar por servicio de aplicación de la aplicación de prueba Roman para Windows.</span><span class="sxs-lookup"><span data-stu-id="5f921-161">The following method composes a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="5f921-162">El **mapa**s que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota debe cumplir el formato siguiente: Las claves deben ser cadenas, y los valores pueden ser: Cadenas, caja de conversión boxing de tipos numéricos (enteros o punto flotante), valores booleanos, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, matrices homogéneas de cualquiera de estos tipos u otros **mapa** objetos que cumple esta especificación.</span><span class="sxs-lookup"><span data-stu-id="5f921-162">The **Map**s that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be Strings, and the values may be: Strings, boxed numeric types (integers or floating points), boxed booleans, android.graphics.Point, android.graphics.Rect, java.util.Date, java.util.UUID, homogeneous arrays of any of these types, or other **Map** objects that meet this specification.</span></span>

#### <a name="send-message-to-the-app-service"></a><span data-ttu-id="5f921-163">Enviar mensaje al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="5f921-163">Send message to the app service</span></span>

<span data-ttu-id="5f921-164">Una vez establecida la conexión de servicio de aplicación y se crea el mensaje, enviarlo a app service es sencillo y se puede realizar desde cualquier lugar en la aplicación que tiene una referencia a la instancia de conexión de servicio de aplicación y el mensaje.</span><span class="sxs-lookup"><span data-stu-id="5f921-164">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the app service connection instance and the message.</span></span>


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

<span data-ttu-id="5f921-165">Se recibió respuesta del servicio de aplicación e interpretada por el método siguiente.</span><span class="sxs-lookup"><span data-stu-id="5f921-165">The app service's response will be received and interpreted by the following method.</span></span>

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
<span data-ttu-id="5f921-166">En el caso de romano App, la respuesta contiene la fecha de creación, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo de tránsito total de la respuesta del mensaje.</span><span class="sxs-lookup"><span data-stu-id="5f921-166">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="5f921-167">Esto concluye un intercambio de mensajes solo con un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="5f921-167">This concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="5f921-168">Finalizar la comunicación del servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="5f921-168">Finish app service communication</span></span>

<span data-ttu-id="5f921-169">Cuando finalice la aplicación interactúa con el servicio de aplicación del dispositivo de destino, cierre la conexión entre los dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5f921-169">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```java
// Close the given AppService connection
private void closeAppServiceConnection()
{
    connection.close();
}
```

### <a name="related-topics"></a><span data-ttu-id="5f921-170">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="5f921-170">Related topics</span></span>
* [<span data-ttu-id="5f921-171">Página de referencia de API</span><span class="sxs-lookup"><span data-stu-id="5f921-171">API reference page</span></span>](api-reference-for-android.md) 
* [<span data-ttu-id="5f921-172">Aplicación de ejemplo de Android</span><span class="sxs-lookup"><span data-stu-id="5f921-172">Android sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/Android/samples) 
* [<span data-ttu-id="5f921-173">Comunicarse con un servicio de aplicación remota (UWP)</span><span class="sxs-lookup"><span data-stu-id="5f921-173">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="5f921-174">[Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="5f921-174">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
