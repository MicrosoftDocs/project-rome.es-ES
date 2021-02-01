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
# <a name="implementing-device-relay-for-ios"></a>Implementación de Retransmisión de dispositivo para iOS

La funcionalidad Retransmisión de dispositivo de Project Rome se compone de un conjunto de API que admiten dos características principales: el inicio remoto (también llamado comando) y los servicios de aplicaciones.

Las API de inicio remoto admiten escenarios en los que se inicia un proceso en un dispositivo remoto desde un dispositivo local. Por ejemplo, un usuario escucha la radio en su teléfono cuando está en el coche, y cuando llega a casa usa el teléfono para transferir la lista de reproducción a su Xbox, que está conectada al equipo de música de la casa.

Las API de App Services permiten a una aplicación establecer una canalización persistente entre dos dispositivos a través de la cual se pueden enviar mensajes que contienen cualquier contenido arbitrario. Por ejemplo, una aplicación para compartir fotos que se ejecuta en un dispositivo móvil podría establecer una conexión con el equipo del usuario para recuperar fotos.

Las características de Project Rome son compatibles con una plataforma subyacente, la plataforma de dispositivos conectados. En esta guía se proporcionan los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y se explica cómo usar la plataforma para implementar las características relacionadas con la retransmisión de dispositivo.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo para iOS de Project Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples), disponible en GitHub.  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuración de la plataforma de dispositivos conectados y las notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Uso de la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Detección de aplicaciones y dispositivos remotos

Una instancia de **MCDRemoteSystemWatcher** controlará la funcionalidad básica de esta sección. Declárala en la clase que se usa para detectar los sistemas remotos.

`MCDRemoteSystemWatcher* _watcher;`

Antes de crear un monitor e iniciar la detección de dispositivos, es posible que desees agregar filtros de detección para determinar los tipos de dispositivos a los que se dirigirá la aplicación. Los filtros se pueden determinar mediante una entrada del usuario, o bien se pueden codificar de forma rígida en la aplicación, según el uso.

El siguiente código de la aplicación de ejemplo muestra cómo crear e iniciar una instancia del monitor que permite a la aplicación analizar e interactuar con los dispositivos detectados.

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

Aquí se definen los métodos del controlador de eventos.

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

Se recomienda que la aplicación mantenga un conjunto de dispositivos detectados (representado por instancias de **MCDRemoteSystem**) y muestre información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el nombre para mostrar y el tipo de dispositivo) en la interfaz de usuario. 

Cuando se llama a `[_watcher start]`, comenzará por inspeccionar la actividad del sistema remoto y generará eventos cuando los dispositivos conectados se detecten, actualicen o quiten del conjunto de dispositivos detectados. Realizará un examen continuo en segundo plano, por lo que se recomienda detener el monitor (con `[_watcher stop]`) cuando ya no se necesite para evitar un consumo innecesario de batería y comunicación de red.

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Caso de uso de ejemplo: Implementación del inicio remoto y los servicios de aplicaciones remotas
A estas alturas, en el código debes tener una lista de trabajo de objetos de **MCDRemoteSystem** que hacen referencia a los dispositivos disponibles. Lo que hagas con estos dispositivos dependerá de la función de la aplicación. Los principales tipos de interacción son el inicio remoto y los servicios de aplicación remota. Estos tipos se explican en las siguientes secciones.

### <a name="a-remote-launching"></a>A) Inicio remoto

El código siguiente muestra cómo seleccionar uno de los objetos **MCDRemoteSystem** (lo ideal es que esto se realice mediante un control de interfaz de usuario) y, después, usar **MCDRemoteLauncher** para iniciar una aplicación en él al pasar un URI compatible con la aplicación.

Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema de URI) _o_ una aplicación remota específica en ese dispositivo.

Como se demostró en la sección anterior, la detección ocurre primero a nivel de dispositivo (una instancia de **MCDRemoteSystem** representa un dispositivo), pero puedes llamar al método `getApplications` en una instancia de **MCDRemoteSystem** para obtener una matriz de objetos **MCDRemoteSystemApp**, que representan aplicaciones en el dispositivo remoto que han sido registradas para usar la plataforma de dispositivos conectados (de la misma manera que registró su propia aplicación en los pasos preliminares anteriores). Tanto **MCDRemoteSystem** como **MCDRemoteSystemApp** pueden utilizarse para construir una instancia de **MCDRemoteSystemConnectionRequest**, que es lo que se necesita para lanzar un URI.

El código del ejemplo siguiente muestra el inicio remoto de un URI a través de una solicitud de conexión.

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

Dependiendo de la URI que se envíe, puedes iniciar una aplicación en un estado o configuración específicos en un dispositivo remoto. Esto proporciona la posibilidad de continuar una tarea de usuario, como ver una película, en otro dispositivo sin interrupción.

Según el uso, es posible que tengas que cubrir casos en los que ninguna aplicación del sistema de destino puede manejar el URI o en los que varias aplicaciones pueden manejarlo. Las clases **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** y **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** describen cómo hacerlo.

### <a name="b-remote-app-services"></a>B) Servicios de aplicaciones remotas

La aplicación de iOS puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicación en otros dispositivos. Esto proporciona muchas maneras de comunicarse con otros dispositivos; todas ellas sin necesidad de traer una aplicación al primer plano del dispositivo host.

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configuración del servicio de aplicaciones en el dispositivo de destino
En esta guía se utiliza [Roman Test App para Windows](https://aka.ms/romeapp) como servicio de aplicación de destino. Por lo tanto, el siguiente código hará que una aplicación de iOS busque ese servicio de aplicación específico en el sistema remoto indicado. Si deseas probar este escenario, descarga la aplicación Roman Test App en un dispositivo Windows y asegúrate de haber iniciado sesión con la misma MSA que en los pasos preliminares anteriores.

Para obtener instrucciones sobre cómo escribir tu propio servicio de aplicación para UWP, consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Tendrás que hacer algunos cambios para que el servicio sea compatible con los dispositivos conectados. Consulta la [guía UWP para los servicios de aplicaciones remotas](/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Apertura de una conexión del servicio de aplicación en el dispositivo cliente
La aplicación de iOS debe adquirir una referencia a una aplicación o dispositivo remoto. Al igual que la sección de inicio, este escenario requiere el uso de una instancia de **MCDRemoteSystemConnectionRequest**, que puede construirse a partir de instancia de **MCDRemoteSystem** o de **MCDRemoteSystemApp** que represente una aplicación disponible en el sistema.

Además, tu aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre del servicio de aplicación* y el *identificador del paquete*. Estas cadenas se encuentran en el código fuente del proveedor de servicios de aplicaciones; consulta [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para ver más detalles. Juntas, estas cadenas construyen **MCDAppServiceDescription**, que se introduce en una instancia de **MCDAppServiceConnection**.

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


#### <a name="create-a-message-to-send-to-the-app-service"></a>Creación de un mensaje para enviar al servicio de aplicación

Declara una variable para almacenar el mensaje que se va a enviar. En iOS, los mensajes que se envían a los servicios de aplicación remota serán del tipo **NSDictionary**.

> [!NOTE]
> Cuando la aplicación se comunica con servicios de aplicación en otras plataformas, la plataforma de dispositivos conectados convierte **NSDictionary** a la construcción equivalente en la plataforma de recepción. Por ejemplo, un objeto **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** enviada desde esta aplicación a un servicio de aplicación de Windows se convierte en un objeto [**ValueSet**](/uwp/api/Windows.Foundation.Collections.ValueSet) (de .NET Framework), que luego el servicio de aplicación puede interpretar. La información pasada en la otra dirección sufre una conversión inversa.

El siguiente método compone un mensaje que puede ser interpretado por el servicio de aplicación de Roman Test App para Windows.

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
> Los objetos **NSDictionary** que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben seguir el siguiente formato: Las claves deben ser **NSString**, y los valores pueden ser: **NSString**, tipos numéricos con conversión boxing (enteros o de punto flotante), booleanos con conversión boxing, **NSDate**, **NSUUID**, matrices homogéneas de cualquiera de estos tipos u otros objetos **NSDictionary** que cumplan esta especificación. 

#### <a name="send-messages-to-the-app-service"></a>Envío de mensajes al servicio de aplicación

Una vez establecida la conexión al servicio de aplicación y creado el mensaje, enviarlo al servicio de aplicación es sencillo y puede realizarse desde cualquier lugar de la aplicación que tenga una referencia a la instancia de conexión y al mensaje.

El siguiente código de ejemplo muestra el envío de un mensaje a un servicio de aplicación y el tratamiento de la respuesta.

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

En el caso de Roman App, la respuesta contiene la fecha en que fue creada, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo total de tránsito de la respuesta del mensaje.

Esto concluye un intercambio de un solo mensaje con un servicio de aplicación remota.

#### <a name="finish-app-service-communication"></a>Finalización de la comunicación del servicio de aplicación

Cuando la aplicación termine de interactuar con el servicio de aplicación del dispositivo de destino, cierra la conexión entre los dos dispositivos.

```ObjectiveC
- (void)appServiceConnection:(__unused MCDAppServiceConnection*)connection closedWithStatus:(MCDAppServiceClosedStatus)status
{
    NSLog(@"AppService closed with status %d", (int)status);
    dispatch_async(
        dispatch_get_main_queue(), ^{ self.appServiceStatusLabel.text = [NSString stringWithFormat:@"disconnected (%d)", (int)status]; });
}
```

## <a name="related-topics"></a>Temas relacionados
* [Página de referencia de API](api-reference-for-ios.md) 
* [Aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [Comunicación con un servicio de aplicación remota (UWP)](/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Crear y consumir un servicio de aplicación (UWP)](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).