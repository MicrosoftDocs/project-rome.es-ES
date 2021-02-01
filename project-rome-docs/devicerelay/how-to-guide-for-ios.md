---
title: Implementación de las características Retransmisión de dispositivo para iOS
description: En esta guía se muestra cómo detectar las aplicaciones y dispositivos remotos y, a continuación, iniciar aplicaciones o interactuar con los servicios de aplicaciones.
ms.topic: article
keywords: microsoft, windows, project rome, commanding, ios
ms.assetid: b5d426db-a0ca-4888-b2cb-cb7fdb1c6c0d
ms.localizationpriority: medium
ms.openlocfilehash: 33dd7e0148c5c7e4ff9d254b4039b95129ac6c69
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901575"
---
# <a name="implementing-device-relay-for-ios"></a><span data-ttu-id="6898c-104">Implementación de Retransmisión de dispositivo para iOS</span><span class="sxs-lookup"><span data-stu-id="6898c-104">Implementing device relay for iOS</span></span>

<span data-ttu-id="6898c-105">La funcionalidad Retransmisión de dispositivo de Project Rome se compone de un conjunto de API que admiten dos características principales: el inicio remoto (también llamado comando) y los servicios de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="6898c-105">The Device Relay functionality of Project Rome consists of a set of APIs that support two main features: remote launching (also known as commanding) and app services.</span></span>

<span data-ttu-id="6898c-106">Las API de inicio remoto admiten escenarios en los que se inicia un proceso en un dispositivo remoto desde un dispositivo local.</span><span class="sxs-lookup"><span data-stu-id="6898c-106">Remote Launching APIs support scenarios where a process on a remote device is started from a local device.</span></span> <span data-ttu-id="6898c-107">Por ejemplo, un usuario escucha la radio en su teléfono cuando está en el coche, y cuando llega a casa usa el teléfono para transferir la lista de reproducción a su Xbox, que está conectada al equipo de música de la casa.</span><span class="sxs-lookup"><span data-stu-id="6898c-107">For example, a user might be listening to the radio on their phone in the car, but when they get home they use their phone to transfer playback to their Xbox which is hooked up to the home stereo.</span></span>

<span data-ttu-id="6898c-108">Las API de App Services permiten a una aplicación establecer una canalización persistente entre dos dispositivos a través de la cual se pueden enviar mensajes que contienen cualquier contenido arbitrario.</span><span class="sxs-lookup"><span data-stu-id="6898c-108">App Services APIs allow an application to establish a persistent pipeline between two devices through which messages containing any arbitrary content can be sent.</span></span> <span data-ttu-id="6898c-109">Por ejemplo, una aplicación para compartir fotos que se ejecuta en un dispositivo móvil podría establecer una conexión con el equipo del usuario para recuperar fotos.</span><span class="sxs-lookup"><span data-stu-id="6898c-109">For example, a photo sharing app running on a mobile device could establish a connection with the user's PC in order to retrieve photos.</span></span>

<span data-ttu-id="6898c-110">Las características de Project Rome son compatibles con una plataforma subyacente, la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6898c-110">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="6898c-111">En esta guía se proporcionan los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y se explica cómo usar la plataforma para implementar las características relacionadas con la retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6898c-111">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement device relay related features.</span></span>

<span data-ttu-id="6898c-112">Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo para iOS de Project Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples), disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="6898c-112">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="6898c-113">Configuración de la plataforma de dispositivos conectados y las notificaciones</span><span class="sxs-lookup"><span data-stu-id="6898c-113">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="6898c-114">Uso de la plataforma</span><span class="sxs-lookup"><span data-stu-id="6898c-114">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a><span data-ttu-id="6898c-115">Detección de aplicaciones y dispositivos remotos</span><span class="sxs-lookup"><span data-stu-id="6898c-115">Discover remote devices and apps</span></span>

<span data-ttu-id="6898c-116">Una instancia de **MCDRemoteSystemWatcher** controlará la funcionalidad básica de esta sección.</span><span class="sxs-lookup"><span data-stu-id="6898c-116">An **MCDRemoteSystemWatcher** instance will handle the core functionality of this section.</span></span> <span data-ttu-id="6898c-117">Declárala en la clase que se usa para detectar los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="6898c-117">Declare it in the class which is to discover remote systems.</span></span>

`MCDRemoteSystemWatcher* _watcher;`

<span data-ttu-id="6898c-118">Antes de crear un monitor e iniciar la detección de dispositivos, es posible que desees agregar filtros de detección para determinar los tipos de dispositivos a los que se dirigirá la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6898c-118">Before you create a watcher and start discovering devices, you may wish to add discovery filters to determine which kinds of devices your app will target.</span></span> <span data-ttu-id="6898c-119">Los filtros se pueden determinar mediante una entrada del usuario, o bien se pueden codificar de forma rígida en la aplicación, según el uso.</span><span class="sxs-lookup"><span data-stu-id="6898c-119">These can be determined by user input or hard-coded into the app, depending on your use case.</span></span>

<span data-ttu-id="6898c-120">El siguiente código de la aplicación de ejemplo muestra cómo crear e iniciar una instancia del monitor que permite a la aplicación analizar e interactuar con los dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="6898c-120">The following code from the sample app demonstrates how to create and start a watcher instance allowing your app to parse and interact with the devices that are discovered.</span></span>

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

<span data-ttu-id="6898c-121">Aquí se definen los métodos del controlador de eventos.</span><span class="sxs-lookup"><span data-stu-id="6898c-121">The event handler methods are defined here.</span></span>

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

<span data-ttu-id="6898c-122">Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por instancias de **MCDRemoteSystem**) y muestre información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el nombre para mostrar y el tipo de dispositivo) en la interfaz de usuario.</span><span class="sxs-lookup"><span data-stu-id="6898c-122">We recommend that your app maintain a set of discovered devices (represented by **MCDRemoteSystem** instances) and display information about available devices and their apps (such as display name and device type) on the UI.</span></span> 

<span data-ttu-id="6898c-123">Cuando se llama a `[_watcher start]`, comenzará por inspeccionar la actividad del sistema remoto y generará eventos cuando los dispositivos conectados se detecten, actualicen o quiten del conjunto de dispositivos detectados.</span><span class="sxs-lookup"><span data-stu-id="6898c-123">Once `[_watcher start]` is called, it will begin watching for remote system activity and will raise events when connected devices are discovered, updated, or removed from the set of detected devices.</span></span> <span data-ttu-id="6898c-124">Realizará un examen continuo en segundo plano, por lo que se recomienda detener el monitor (con `[_watcher stop]`) cuando ya no se necesite para evitar un consumo innecesario de batería y comunicación de red.</span><span class="sxs-lookup"><span data-stu-id="6898c-124">It will scan continuously in the background, so it is recommended that you stop the watcher (with `[_watcher stop]`) when you no longer need it to avoid unnecessary network communication and battery drain.</span></span>

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a><span data-ttu-id="6898c-125">Caso de uso de ejemplo: Implementación del inicio remoto y los servicios de aplicaciones remotas</span><span class="sxs-lookup"><span data-stu-id="6898c-125">Example use case: implementing remote launching and remote app services</span></span>
<span data-ttu-id="6898c-126">A estas alturas, en el código debes tener una lista de trabajo de objetos de **MCDRemoteSystem** que hacen referencia a los dispositivos disponibles.</span><span class="sxs-lookup"><span data-stu-id="6898c-126">At this point in your code, you should have a working list of **MCDRemoteSystem** objects that refer to available devices.</span></span> <span data-ttu-id="6898c-127">Lo que hagas con estos dispositivos dependerá de la función de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6898c-127">What you do with these devices will depend on the function of your app.</span></span> <span data-ttu-id="6898c-128">Los principales tipos de interacción son el inicio remoto y los servicios de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="6898c-128">The main types of interaction are remote launching and remote app services.</span></span> <span data-ttu-id="6898c-129">Estos tipos se explican en las siguientes secciones.</span><span class="sxs-lookup"><span data-stu-id="6898c-129">They are explained in the following sections.</span></span>

### <a name="a-remote-launching"></a><span data-ttu-id="6898c-130">A) Inicio remoto</span><span class="sxs-lookup"><span data-stu-id="6898c-130">A) Remote launching</span></span>

<span data-ttu-id="6898c-131">El código siguiente muestra cómo seleccionar uno de los objetos **MCDRemoteSystem** (lo ideal es que esto se realice mediante un control de interfaz de usuario) y, después, usar **MCDRemoteLauncher** para iniciar una aplicación en él al pasar un URI compatible con la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6898c-131">The following code shows how to select one of the **MCDRemoteSystem** objects (ideally this is done through a UI control) and then use **MCDRemoteLauncher** to launch an app on it by passing an app-compatible URI.</span></span>

<span data-ttu-id="6898c-132">Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema de URI) _o_ una aplicación remota específica en ese dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6898c-132">It's important to note that a remote launch can target a remote device (in which case the host device will launch the given URI with its default app for that URI scheme) _or_ a specific remote application on that device.</span></span>

<span data-ttu-id="6898c-133">Como se demostró en la sección anterior, la detección ocurre primero a nivel de dispositivo (una instancia de **MCDRemoteSystem** representa un dispositivo), pero puedes llamar al método `getApplications` en una instancia de **MCDRemoteSystem** para obtener una matriz de objetos **MCDRemoteSystemApp**, que representan aplicaciones en el dispositivo remoto que han sido registradas para usar la plataforma de dispositivos conectados (de la misma manera que registró su propia aplicación en los pasos preliminares anteriores).</span><span class="sxs-lookup"><span data-stu-id="6898c-133">As the previous section demonstrated, discovery happens at the device level first (an **MCDRemoteSystem** represents a device), but you can call the `getApplications` method on an **MCDRemoteSystem** instance to get an array of **MCDRemoteSystemApp** objects, which represent apps on the remote device that have been registered to use the Connected Devices Platform (just as you registered your own app in the preliminary steps above).</span></span> <span data-ttu-id="6898c-134">Tanto **MCDRemoteSystem** como **MCDRemoteSystemApp** pueden utilizarse para construir una instancia de **MCDRemoteSystemConnectionRequest**, que es lo que se necesita para lanzar un URI.</span><span class="sxs-lookup"><span data-stu-id="6898c-134">Both **MCDRemoteSystem** and **MCDRemoteSystemApp** can be used to construct a **MCDRemoteSystemConnectionRequest**, which is what is needed to launch a URI.</span></span>

<span data-ttu-id="6898c-135">El código del ejemplo siguiente muestra el inicio remoto de un URI a través de una solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="6898c-135">The following code from the sample shows the remote launching of a URI over a connection request.</span></span>

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

<span data-ttu-id="6898c-136">Dependiendo de la URI que se envíe, puedes iniciar una aplicación en un estado o configuración específicos en un dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="6898c-136">Depending on the URI that is sent, you can launch an app in a specific state or configuration on a remote device.</span></span> <span data-ttu-id="6898c-137">Esto proporciona la posibilidad de continuar una tarea de usuario, como ver una película, en otro dispositivo sin interrupción.</span><span class="sxs-lookup"><span data-stu-id="6898c-137">This allows for the ability to continue a user task, like watching a movie, on a different device without interruption.</span></span>

<span data-ttu-id="6898c-138">Según el uso, es posible que tengas que cubrir casos en los que ninguna aplicación del sistema de destino puede manejar el URI o en los que varias aplicaciones pueden manejarlo.</span><span class="sxs-lookup"><span data-stu-id="6898c-138">Depending on your use, you may need to cover the cases in which no apps on the targeted system can handle the URI, or multiple apps can handle it.</span></span> <span data-ttu-id="6898c-139">Las clases **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** y **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** describen cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="6898c-139">The **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** class and **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** class describe how to do this.</span></span>

### <a name="b-remote-app-services"></a><span data-ttu-id="6898c-140">B) Servicios de aplicaciones remotas</span><span class="sxs-lookup"><span data-stu-id="6898c-140">B) Remote app services</span></span>

<span data-ttu-id="6898c-141">La aplicación de iOS puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicación en otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6898c-141">Your iOS app can use the Connected Devices Portal to interact with app services on other devices.</span></span> <span data-ttu-id="6898c-142">Esto proporciona muchas maneras de comunicarse con otros dispositivos; todas ellas sin necesidad de traer una aplicación al primer plano del dispositivo host.</span><span class="sxs-lookup"><span data-stu-id="6898c-142">This provides many ways to communicate with other devices&mdash;all without needing to bring an app to the foreground of the host device.</span></span>

#### <a name="set-up-the-app-service-on-the-target-device"></a><span data-ttu-id="6898c-143">Configuración del servicio de aplicaciones en el dispositivo de destino</span><span class="sxs-lookup"><span data-stu-id="6898c-143">Set up the app service on the target device</span></span>
<span data-ttu-id="6898c-144">En esta guía se utiliza [Roman Test App para Windows](https://aka.ms/romeapp) como servicio de aplicación de destino.</span><span class="sxs-lookup"><span data-stu-id="6898c-144">This guide will use the [Roman Test App for Windows](https://aka.ms/romeapp) as its target app service.</span></span> <span data-ttu-id="6898c-145">Por lo tanto, el siguiente código hará que una aplicación de iOS busque ese servicio de aplicación específico en el sistema remoto indicado.</span><span class="sxs-lookup"><span data-stu-id="6898c-145">Therefore, the code below will cause an iOS app to look for that specific app service on the given remote system.</span></span> <span data-ttu-id="6898c-146">Si deseas probar este escenario, descarga la aplicación Roman Test App en un dispositivo Windows y asegúrate de haber iniciado sesión con la misma MSA que en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="6898c-146">If you wish to test this scenario, download the Roman Test App on a Windows device and make sure you are signed in with the same MSA that you used in the preliminary steps above.</span></span>

<span data-ttu-id="6898c-147">Para obtener instrucciones sobre cómo escribir tu propio servicio de aplicación para UWP, consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="6898c-147">For instructions on how to write your own UWP app service, see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span> <span data-ttu-id="6898c-148">Tendrás que hacer algunos cambios para que el servicio sea compatible con los dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6898c-148">You will need to make a few changes in order to make the service compatible with Connected Devices.</span></span> <span data-ttu-id="6898c-149">Consulta la [guía UWP para los servicios de aplicaciones remotas](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="6898c-149">See the [UWP guide for remote app services](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) for instructions on how to do this.</span></span> 

#### <a name="open-an-app-service-connection-on-the-client-device"></a><span data-ttu-id="6898c-150">Apertura de una conexión del servicio de aplicación en el dispositivo cliente</span><span class="sxs-lookup"><span data-stu-id="6898c-150">Open an app service connection on the client device</span></span>
<span data-ttu-id="6898c-151">La aplicación de iOS debe adquirir una referencia a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="6898c-151">Your iOS app must acquire a reference to a remote device or application.</span></span> <span data-ttu-id="6898c-152">Al igual que la sección de inicio, este escenario requiere el uso de una instancia de **MCDRemoteSystemConnectionRequest**, que puede construirse a partir de instancia de **MCDRemoteSystem** o de **MCDRemoteSystemApp** que represente una aplicación disponible en el sistema.</span><span class="sxs-lookup"><span data-stu-id="6898c-152">Like the launch section, this scenario requires the use of a **MCDRemoteSystemConnectionRequest**, which can be constructed from either a **MCDRemoteSystem** or a **MCDRemoteSystemApp** representing an available app on the system.</span></span>

<span data-ttu-id="6898c-153">Además, tu aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre del servicio de aplicación* y el *identificador del paquete*.</span><span class="sxs-lookup"><span data-stu-id="6898c-153">Additionally, your app will need to identify its targeted app service by two strings: the *app service name* and *package identifier*.</span></span> <span data-ttu-id="6898c-154">Estas cadenas se encuentran en el código fuente del proveedor de servicios de aplicaciones; consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para ver más detalles.</span><span class="sxs-lookup"><span data-stu-id="6898c-154">These are found in the source code of the app service provider (see [Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) for details).</span></span> <span data-ttu-id="6898c-155">Juntas, estas cadenas construyen **MCDAppServiceDescription**, que se introduce en una instancia de **MCDAppServiceConnection**.</span><span class="sxs-lookup"><span data-stu-id="6898c-155">Together these strings construct the **MCDAppServiceDescription**, which is fed into an **MCDAppServiceConnection** instance.</span></span>

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


#### <a name="create-a-message-to-send-to-the-app-service"></a><span data-ttu-id="6898c-156">Creación de un mensaje para enviar al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6898c-156">Create a message to send to the app service</span></span>

<span data-ttu-id="6898c-157">Declara una variable para almacenar el mensaje que se va a enviar.</span><span class="sxs-lookup"><span data-stu-id="6898c-157">Declare a variable to store the message to send.</span></span> <span data-ttu-id="6898c-158">En iOS, los mensajes que se envían a los servicios de aplicación remota serán del tipo **NSDictionary**.</span><span class="sxs-lookup"><span data-stu-id="6898c-158">On iOS, the messages that you send to remote app services will be of the **NSDictionary** type.</span></span>

> [!NOTE]
> <span data-ttu-id="6898c-159">Cuando la aplicación se comunica con servicios de aplicación en otras plataformas, la plataforma de dispositivos conectados convierte **NSDictionary** a la construcción equivalente en la plataforma de recepción.</span><span class="sxs-lookup"><span data-stu-id="6898c-159">When your app communicates with app services on other platforms, the Connected Devices Platform translates the **NSDictionary** into the equivalent construct on the receiving platform.</span></span> <span data-ttu-id="6898c-160">Por ejemplo, un objeto **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** enviada desde esta aplicación a un servicio de aplicación de Windows se convierte en un objeto [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) (de .NET Framework), que luego el servicio de aplicación puede interpretar.</span><span class="sxs-lookup"><span data-stu-id="6898c-160">For example, a **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** sent from this app to a Windows app service gets translated into a [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) object (of the .NET Framework), which can then be interpreted by the app service.</span></span> <span data-ttu-id="6898c-161">La información pasada en la otra dirección sufre una conversión inversa.</span><span class="sxs-lookup"><span data-stu-id="6898c-161">Information passed in the other direction undergoes the reverse translation.</span></span>

<span data-ttu-id="6898c-162">El siguiente método compone un mensaje que puede ser interpretado por el servicio de aplicación de Roman Test App para Windows.</span><span class="sxs-lookup"><span data-stu-id="6898c-162">The following method crafts a message that can be interpreted by the Roman Test App's app service for Windows.</span></span>

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
> <span data-ttu-id="6898c-163">Los objetos **NSDictionary** que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben seguir el siguiente formato: Las claves deben ser **NSString**, y los valores pueden ser: **NSString**, tipos numéricos con conversión boxing (enteros o de punto flotante), booleanos con conversión boxing, **NSDate**, **NSUUID**, matrices homogéneas de cualquiera de estos tipos u otros objetos **NSDictionary** que cumplan esta especificación.</span><span class="sxs-lookup"><span data-stu-id="6898c-163">The **NSDictionary** objects that are passed between apps and services in the remote app services scenario must adhere to the following format: Keys must be **NSString** s, and the values may be: **NSString**, boxed numeric types (integers or floating points), boxed booleans, **NSDate**, **NSUUID**, homogeneous arrays of any of these types, or other **NSDictionary** objects that meet this specification.</span></span> 

#### <a name="send-messages-to-the-app-service"></a><span data-ttu-id="6898c-164">Envío de mensajes al servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6898c-164">Send messages to the app service</span></span>

<span data-ttu-id="6898c-165">Una vez establecida la conexión al servicio de aplicación y creado el mensaje, enviarlo al servicio de aplicación es sencillo y puede realizarse desde cualquier lugar de la aplicación que tenga una referencia a la instancia de conexión y al mensaje.</span><span class="sxs-lookup"><span data-stu-id="6898c-165">Once the app service connection is established and the message is created, sending it to the app service is simple and can be done from anywhere in the app that has a reference to the connection instance and the message.</span></span>

<span data-ttu-id="6898c-166">El siguiente código de ejemplo muestra el envío de un mensaje a un servicio de aplicación y el tratamiento de la respuesta.</span><span class="sxs-lookup"><span data-stu-id="6898c-166">The following code from the sample shows the sending of a message to an app service and the handling of the response.</span></span>

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

<span data-ttu-id="6898c-167">En el caso de Roman App, la respuesta contiene la fecha en que fue creada, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo total de tránsito de la respuesta del mensaje.</span><span class="sxs-lookup"><span data-stu-id="6898c-167">In the Roman App case, the response contains the date it was created, so in this very simple use case, we can compare the dates to get the total transit time of the message response.</span></span>

<span data-ttu-id="6898c-168">Esto concluye un intercambio de un solo mensaje con un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="6898c-168">That concludes a single message exchange with a remote app service.</span></span>

#### <a name="finish-app-service-communication"></a><span data-ttu-id="6898c-169">Finalización de la comunicación del servicio de aplicación</span><span class="sxs-lookup"><span data-stu-id="6898c-169">Finish app service communication</span></span>

<span data-ttu-id="6898c-170">Cuando la aplicación termine de interactuar con el servicio de aplicación del dispositivo de destino, cierra la conexión entre los dos dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6898c-170">When your app is finished interacting with the target device's app service, close the connection between the two devices.</span></span>

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a><span data-ttu-id="6898c-171">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="6898c-171">Related topics</span></span>
* [<span data-ttu-id="6898c-172">Página de referencia de API</span><span class="sxs-lookup"><span data-stu-id="6898c-172">API reference page</span></span>](api-reference-for-ios.md) 
* [<span data-ttu-id="6898c-173">Aplicación de ejemplo de iOS</span><span class="sxs-lookup"><span data-stu-id="6898c-173">iOS sample app</span></span>](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [<span data-ttu-id="6898c-174">Comunicación con un servicio de aplicación remota (UWP)</span><span class="sxs-lookup"><span data-stu-id="6898c-174">Communicate with a remote app service (UWP)</span></span>](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* <span data-ttu-id="6898c-175">[Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span><span class="sxs-lookup"><span data-stu-id="6898c-175">[Create and consume an app service (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).</span></span>