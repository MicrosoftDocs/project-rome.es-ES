---
title: Implementación de las características de retransmisión de dispositivo para iOS
description: Esta guía le mostrará cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicación.
ms.topic: article
keywords: Microsoft, windows, proyecto Roma, comandos, ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 11596720d9363f0ef29fd9c7bf0ccc5b4db62fae
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907737"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="6c0e4-104">Implementación de retransmisión de dispositivo para iOS</span><span class="sxs-lookup"><span data-stu-id="6c0e4-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="6c0e4-105">La funcionalidad de retransmisión de dispositivo de Roma proyecto consta de un conjunto de API que admiten dos características principales: iniciar remoto (también conocido como comandos) y los servicios de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="6c0e4-106">API de inicio remoto admiten escenarios donde se inicia un proceso en un dispositivo remoto desde un dispositivo local.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="6c0e4-107">Por ejemplo, un usuario podría estar escuchando en la radio en su teléfono en el automóvil, pero cuando llegue a casa usan su teléfono para transferir la reproducción a su Xbox que está enlazado al equipo de música doméstico.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="6c0e4-108">API de servicios de aplicaciones permiten que una aplicación establecer una canalización persistente entre los dos dispositivos a través del cual se pueden enviar los mensajes que contienen cualquier contenido arbitrario.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="6c0e4-109">Por ejemplo, una foto en la aplicación que se ejecuta en un dispositivo móvil para uso compartido podría establecer una conexión con el equipo del usuario con el fin de recuperar las fotos.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="6c0e4-110">Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="6c0e4-111">Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, se explica cómo usar la plataforma para implementar características relacionadas con la retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="6c0e4-112">Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="6c0e4-113">Configurar la plataforma de dispositivos conectados y notificaciones</span><span class="sxs-lookup"><span data-stu-id="6c0e4-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="6c0e4-114">Con la plataforma</span><span class="sxs-lookup"><span data-stu-id="6c0e4-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="6c0e4-115">Detectar aplicaciones y dispositivos remotos</span><span class="sxs-lookup"><span data-stu-id="6c0e4-115">Discover remote devices and apps</span></span>

<span data-ttu-id="6c0e4-116">Un **MCDRemoteSystemWatcher** instancia controlará la funcionalidad básica de esta sección.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="6c0e4-117">Declararla de la clase que se usa para detectar los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="6c0e4-118">Antes de crear un monitor e iniciar la detección de dispositivos, desea agregar filtros de detección para determinar qué tipos de dispositivos de destino de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="6c0e4-119">Estos se pueden determinar por usuario de entrada o codificado de forma rígida en la aplicación, según el caso de uso.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="6c0e4-120">El siguiente código de la aplicación de ejemplo muestra cómo crear e iniciar una instancia de watcher que permite a su aplicación analizar e interactuar con los dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

```ObjectiveC
// Start watcher with filter for transport types, form factors
- (void)startWatcherWithFilter:(NSMutableArray<NSObject<MCDRemoteSystemFilter>*>*)remoteSystemFilter
{
    _discoveredSystems = [[NSMutableArray alloc] init];
    _devicesAdded = 0;
    _devicesUpdated = 0;
    _devicesRemoved = 0;

    // add filters (not defined here)
    _watcher = (remoteSystemFilter.count > 0) ? [[MCDRemoteSystemWatcher alloc] initWithFilters:remoteSystemFilter] :
        [[MCDRemoteSystemWatcher alloc] init];

    // add event handlers
    RemoteSystemViewController* __weak weakSelf = self;
    [_watcher addRemoteSystemAddedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemAdded:system]; }];

    [_watcher addRemoteSystemUpdatedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemUpdated:system]; }];

    [_watcher addRemoteSystemRemovedListener:^(
        __unused MCDRemoteSystemWatcher* watcher, MCDRemoteSystem* system) { [weakSelf _onRemoteSystemRemoved:system]; }];

    // start watcher
    [_watcher start];
}
```

<span data-ttu-id="6c0e4-121">Aquí se definen los métodos de controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-121">The event handler methods are defined here.</span></span>

```ObjectiveC
// Handle when RemoteSystems are added
- (void)_onRemoteSystemAdded:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesAdded++;
        [_discoveredSystems addObject:system];
        [_delegate remoteSystemsDidUpdate];
    }
}

// Handle when RemoteSystems are updated
- (void)_onRemoteSystemUpdated:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesUpdated++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems replaceObjectAtIndex:i withObject:system];
                break;
            }
        }
    }
}

// Handle when RemoteSystems are removed
- (void)_onRemoteSystemRemoved:(MCDRemoteSystem*)system
{
    @synchronized(self)
    {
        _devicesRemoved++;

        for (unsigned i = 0; i < _discoveredSystems.count; i++)
        {
            MCDRemoteSystem* cachedSystem = [_discoveredSystems objectAtIndex:i];
            if ([cachedSystem.displayName isEqualToString:system.displayName])
            {
                [_discoveredSystems removeObjectAtIndex:i];
                break;
            }
        }
    }
}
```

<span data-ttu-id="6c0e4-122">Se recomienda que la aplicación mantener un conjunto de dispositivos detectados (representado por **MCDRemoteSystem** instancias) y mostrar información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el tipo de nombre y el dispositivo de visualización) en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="6c0e4-123">Una vez `[_watcher start]` es llamado, comenzará a inspeccionando la actividad del sistema remoto y genera eventos cuando los dispositivos conectados se detectan, actualizados o quitados del conjunto de dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="6c0e4-124">Examinará continuamente en segundo plano, por lo que se recomienda detener el Monitor (con `[_watcher stop]`) cuando ya no necesita para evitar la purga de comunicación y la batería de red innecesario.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="6c0e4-125">Caso de uso de ejemplo: implementar el inicio remoto y los servicios de RemoteApp</span><span class="sxs-lookup"><span data-stu-id="6c0e4-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="6c0e4-126">En este momento en el código, debe tener una lista de trabajo de **MCDRemoteSystem** objetos que hacen referencia a los dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="6c0e4-127">Qué hacer con estos dispositivos dependerá de la función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="6c0e4-128">Los tipos principales de interacción son Inicio remoto y los servicios de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="6c0e4-129">Se explican en las secciones siguientes.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="6c0e4-130">A) iniciar remoto</span><span class="sxs-lookup"><span data-stu-id="6c0e4-130">A) Remote launching</span></span>

<span data-ttu-id="6c0e4-131">El código siguiente muestra cómo seleccionar uno de los **MCDRemoteSystem** objetos (lo ideal es que esto se realiza a través de un control de interfaz de usuario) y, después, use **MCDRemoteLauncher** para iniciar una aplicación en ella, pasando de una aplicación compatible IDENTIFICADOR URI.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="6c0e4-132">Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo de host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema URI) _o_ una aplicación remota específica en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="6c0e4-133">Como se muestra la sección anterior, detección se produce en el nivel de dispositivo en primer lugar (un **MCDRemoteSystem** representa un dispositivo), pero se puede llamar a la `getApplications` método en un **MCDRemoteSystem** instancia para obtener una matriz de **MCDRemoteSystemApp** objetos que representan las aplicaciones en el dispositivo remoto que se han registrado para usar la plataforma de dispositivos conectados (tal como se registró su propia aplicación en los pasos preliminares anteriormente).</span><span class="sxs-lookup"><span data-stu-id="6c0e4-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="6c0e4-134">Ambos **MCDRemoteSystem** y **MCDRemoteSystemApp** puede usarse para construir un **MCDRemoteSystemConnectionRequest**, que es lo que hace falta para iniciar un URI.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="6c0e4-135">El código del ejemplo siguiente muestra el inicio remoto de un URI a través de una solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

```ObjectiveC
// Send a remote launch of a uri to RemoteSystemApplication
- (IBAction)launchUriButton:(id)sender
{
    NSString* uri = self.uriField.text;
    MCDRemoteLauncher* remoteLauncher = [[MCDRemoteLauncher alloc] init];
    MCDRemoteSystemConnectionRequest* connectionRequest =
        [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
    [remoteLauncher launchUriAsync:uri
        withConnectionRequest:connectionRequest
            completion:^(MCDRemoteLaunchUriStatus result, NSError* _Nullable error) {
                if (error)
                {
                    NSLog(@"LaunchURI [%@]: ERROR: %@", uri, error);
                    return;
                }

                if (result == MCDRemoteLaunchUriStatusSuccess)
                {
                    NSLog(@"LaunchURI [%@]: Success!", uri);
                }
                else
                {
                    NSLog(@"LaunchURI [%@]: Failed with code %d", uri, (int)result);
                }
            }];
}
```

<span data-ttu-id="6c0e4-136">Según el URI que se envía, puede iniciar una aplicación en un estado específico o una configuración en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="6c0e4-137">Esto permite la capacidad de seguir una tarea de usuario, como ver una película en un dispositivo diferente sin interrupción.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="6c0e4-138">Dependiendo de su uso, es posible que deba cubrir los casos en que no hay ninguna aplicación en el sistema de destino puede controlar el identificador URI o varias aplicaciones pueden controlarla.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="6c0e4-139">El **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** clase y **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** clase describen cómo hacer esto.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="6c0e4-140">B) servicios de aplicación remoto</span><span class="sxs-lookup"><span data-stu-id="6c0e4-140">B) Remote app services</span></span>

<span data-ttu-id="6c0e4-141">La aplicación de iOS puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicación en otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="6c0e4-142">Esto proporciona muchas formas de comunicarse con otros dispositivos&mdash;todo ello sin necesidad de llevar una aplicación en primer plano del dispositivo host.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="6c0e4-143">Configurar el servicio de aplicaciones en el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="6c0e4-143">Set up the app service on the target device</span></span>
<span data-ttu-id="6c0e4-144">Esta guía utilizará el [Roman prueba de aplicaciones para Windows](http://aka.ms/romeapp) como servicio de aplicación de destino.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-144">This guide will use the [Roman Test App for Windows](http://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="6c0e4-145">Por lo tanto, el código siguiente hará que una aplicación de iOS buscar ese servicio de aplicación específica en el sistema remoto determinado.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="6c0e4-146">Si desea probar este escenario, descargue la aplicación de prueba romanos en un dispositivo de Windows y asegúrese de que haya iniciado sesión con el mismo MSA o AAD que usó en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA or AAD that you used in the preliminary steps above.</span></span>

<span data-ttu-id="6c0e4-147">Para obtener instrucciones sobre cómo escribir su propio servicio de aplicación para UWP, consulte [crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="6c0e4-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="6c0e4-148">Deberá realizar algunos cambios con el fin de que el servicio sea compatible con dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="6c0e4-149">Consulte la [guía UWP para los servicios de aplicación remota](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-149">See the [UWP guide for remote app services](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="6c0e4-150">Abrir una conexión de servicio de aplicación en el dispositivo de cliente</span><span class="sxs-lookup"><span data-stu-id="6c0e4-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="6c0e4-151">La aplicación de iOS debe adquirir una referencia a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="6c0e4-152">Al igual que la sección de inicio, este escenario requiere el uso de un **MCDRemoteSystemConnectionRequest**, que puede crearse desde un **MCDRemoteSystem** o un **MCDRemoteSystemApp**  que representa una aplicación disponible en el sistema.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="6c0e4-153">Además, la aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre de app service* y *identificador de paquete*.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="6c0e4-154">Estos se encuentran en el código fuente del proveedor de servicios de aplicación (consulte [crear y consumir un servicio de aplicación (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener más información).</span><span class="sxs-lookup"><span data-stu-id="6c0e4-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="6c0e4-155">Juntas construyen estas cadenas el **MCDAppServiceDescription**, que se introducen en un **MCDAppServiceConnection** instancia.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

```ObjectiveC
// Step #1:  Establish an app service connection
- (IBAction)connectAppServiceButton:(id)sender
{
    MCDAppServiceConnection* connection = nil;
    @synchronized(self)
    {
        connection = _appServiceConnection;
        if (!connection)
        {
            connection = _appServiceConnection = [MCDAppServiceConnection new];
            connection.appServiceDescription =
                [MCDAppServiceDescription descriptionWithName:g_appServiceName packageId:g_packageIdentifier];
            _serviceClosedRegistration = [connection addServiceClosedListener:^(__unused MCDAppServiceConnection* connection,
                MCDAppServiceClosedStatus status) { [self appServiceConnection:connection closedWithStatus:status]; }];
        }
    }

    @try
    {
        MCDRemoteSystemConnectionRequest* connectionRequest =
            [MCDRemoteSystemConnectionRequest requestWithRemoteSystemApplication:self.selectedApplication];
        [connection openRemoteAsync:connectionRequest
            completion:^(MCDAppServiceConnectionStatus status, NSError* error) {
                if (error)
                {
                    NSLog(@"ConnectAppService: ERROR: %@", error);
                    return;
                }
                if (status != MCDAppServiceConnectionStatusSuccess)
                {
                    NSLog(@"ConnectAppService: Failed with code %d", (int)status);
                    return;
                }
                NSLog(@"Successfully connected!");
                dispatch_async(
                    dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = @"App service connected! no ping sent"; });
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"ConnectAppService: EXCEPTION! %@", ex);
    }
}
```


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="6c0e4-156">Crear un mensaje para enviar al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6c0e4-156">Create a message to send to the app service</span></span>

<span data-ttu-id="6c0e4-157">Declare una variable para almacenar el mensaje para enviar.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="6c0e4-158">En iOS, los mensajes que se envían a los servicios de aplicación remota será de la **NSDictionary** tipo.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="6c0e4-159">Cuando la aplicación se comunica con servicios de aplicaciones en otras plataformas, la plataforma de dispositivos conectados traduce el **NSDictionary** en la construcción equivalente en la plataforma de destino.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="6c0e4-160">Por ejemplo, un **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** enviados desde esta aplicación a un Windows servicio de aplicación se traduce en un [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objeto (de .NET Marco de trabajo), que, a continuación, se puede interpretar el servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="6c0e4-161">Información que se pasa en la otra dirección se somete a la traducción inversa.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="6c0e4-162">El siguiente método elabora un mensaje que se puede interpretar por servicio de aplicación de la aplicación de prueba Roman para Windows.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

```ObjectiveC
// Create a message to send
- (NSDictionary*)_createPingMessage
{
    return @{
        @"Type" : @"ping",
        @"CreationDate" : [_dateFormatter stringFromDate:[NSDate date]],
        @"TargetId" : _selectedApplication.applicationId
    };
}
```

> [!IMPORTANT]
> <span data-ttu-id="6c0e4-163">El **NSDictionary** objetos que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben cumplir el formato siguiente: Las claves deben ser **NSString**s y los valores pueden ser: **NSString**, conversión boxing a tipos numéricos (enteros o punto flotante), aplicar la conversión boxing de valores booleanos, **NSDate**, **NSUUID**, matrices homogéneas de cualquiera de estos tipos u otros **NSDictionary**  objetos que cumplen esta especificación.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString**s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="6c0e4-164">Enviar mensajes al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6c0e4-164">Send messages to the app service</span></span>

<span data-ttu-id="6c0e4-165">Una vez establecida la conexión de servicio de aplicación y se crea el mensaje, enviarlo a app service es sencillo y se puede realizar desde cualquier lugar en la aplicación que tiene una referencia a la instancia de la conexión y el mensaje.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="6c0e4-166">El código del ejemplo siguiente muestra el envío de un mensaje a un servicio de aplicaciones y el control de la respuesta.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

```ObjectiveC
//  Send a message using the app service connection
- (IBAction)sendAppServiceButton:(id)sender
{
    if (!_appServiceConnection)
    {
        return;
    }

    // Send the message and get a response
    @try
    {
        [_appServiceConnection sendMessageAsync:[self _createPingMessage]
            completion:^(MCDAppServiceResponse* response, NSError* error) {
                if (error)
                {
                    NSLog(@"SendPing: ERROR: %@", error);
                    return;
                }

                if (response.status != MCDAppServiceResponseStatusSuccess)
                {
                    NSLog(@"SendPing: Response received with bad status code %d", (int)response.status);
                    return;
                }

                NSString* creationDateString = response.message[@"CreationDate"];
                if (creationDateString)
                {
                    NSDate* date = [_dateFormatter dateFromString:creationDateString];
                    if (date)
                    {
                        NSTimeInterval diff = [[NSDate date] timeIntervalSinceDate:date];
                        dispatch_async(dispatch_get_main_queue(),
                            ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"%g", diff]; });
                    }
                }
            }];
    }
    @catch (NSException* ex)
    {
        NSLog(@"SendPing: EXCEPTION! %@", ex);
    }
}
```

<span data-ttu-id="6c0e4-167">En el caso de romano App, la respuesta contiene la fecha de creación, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo de tránsito total de la respuesta del mensaje.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="6c0e4-168">Esto concluye un intercambio de mensajes solo con un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="6c0e4-169">Finalizar la comunicación del servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6c0e4-169">Finish app service communication</span></span>

<span data-ttu-id="6c0e4-170">Cuando finalice la aplicación interactúa con el servicio de aplicación del dispositivo de destino, cierre la conexión entre los dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6c0e4-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="6c0e4-171">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="6c0e4-171">Related topics</span></span>
* [<span data-ttu-id="6c0e4-172">Página de referencia de API</span><span class="sxs-lookup"><span data-stu-id="6c0e4-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="6c0e4-173">aplicación de ejemplo de iOS</span><span class="sxs-lookup"><span data-stu-id="6c0e4-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="6c0e4-174">Comunicarse con un servicio de aplicación remota (UWP)</span><span class="sxs-lookup"><span data-stu-id="6c0e4-174">Communicate with a remote app service (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="6c0e4-175">[Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="6c0e4-175">[Create and consume an app service (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>
