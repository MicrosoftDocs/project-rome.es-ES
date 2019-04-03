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
# <a name="implementing-device-relay-for-ios"></a>Implementación de retransmisión de dispositivo para iOS

La funcionalidad de retransmisión de dispositivo de Roma proyecto consta de un conjunto de API que admiten dos características principales: iniciar remoto (también conocido como comandos) y los servicios de aplicación.

API de inicio remoto admiten escenarios donde se inicia un proceso en un dispositivo remoto desde un dispositivo local. Por ejemplo, un usuario podría estar escuchando en la radio en su teléfono en el automóvil, pero cuando llegue a casa usan su teléfono para transferir la reproducción a su Xbox que está enlazado al equipo de música doméstico.

API de servicios de aplicaciones permiten que una aplicación establecer una canalización persistente entre los dos dispositivos a través del cual se pueden enviar los mensajes que contienen cualquier contenido arbitrario. Por ejemplo, una foto en la aplicación que se ejecuta en un dispositivo móvil para uso compartido podría establecer una conexión con el equipo del usuario con el fin de recuperar las fotos.

Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados. Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, se explica cómo usar la plataforma para implementar características relacionadas con la retransmisión de dispositivo.

Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.  

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configurar la plataforma de dispositivos conectados y notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Con la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="discover-remote-devices-and-apps"></a>Detectar aplicaciones y dispositivos remotos

Un **MCDRemoteSystemWatcher** instancia controlará la funcionalidad básica de esta sección. Declararla de la clase que se usa para detectar los sistemas remotos.

`MCDRemoteSystemWatcher* _watcher;`

Antes de crear un monitor e iniciar la detección de dispositivos, desea agregar filtros de detección para determinar qué tipos de dispositivos de destino de la aplicación. Estos se pueden determinar por usuario de entrada o codificado de forma rígida en la aplicación, según el caso de uso.

El siguiente código de la aplicación de ejemplo muestra cómo crear e iniciar una instancia de watcher que permite a su aplicación analizar e interactuar con los dispositivos detectados.

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

Aquí se definen los métodos de controlador de eventos.

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

Se recomienda que la aplicación mantener un conjunto de dispositivos detectados (representado por **MCDRemoteSystem** instancias) y mostrar información sobre los dispositivos disponibles y sus aplicaciones (por ejemplo, el tipo de nombre y el dispositivo de visualización) en la interfaz de usuario. 

Una vez `[_watcher start]` es llamado, comenzará a inspeccionando la actividad del sistema remoto y genera eventos cuando los dispositivos conectados se detectan, actualizados o quitados del conjunto de dispositivos detectados. Examinará continuamente en segundo plano, por lo que se recomienda detener el Monitor (con `[_watcher stop]`) cuando ya no necesita para evitar la purga de comunicación y la batería de red innecesario.

## <a name="example-use-case-implementing-remote-launching-and-remote-app-services"></a>Caso de uso de ejemplo: implementar el inicio remoto y los servicios de RemoteApp
En este momento en el código, debe tener una lista de trabajo de **MCDRemoteSystem** objetos que hacen referencia a los dispositivos disponibles. Qué hacer con estos dispositivos dependerá de la función de la aplicación. Los tipos principales de interacción son Inicio remoto y los servicios de aplicación remota. Se explican en las secciones siguientes.

### <a name="a-remote-launching"></a>A) iniciar remoto

El código siguiente muestra cómo seleccionar uno de los **MCDRemoteSystem** objetos (lo ideal es que esto se realiza a través de un control de interfaz de usuario) y, después, use **MCDRemoteLauncher** para iniciar una aplicación en ella, pasando de una aplicación compatible IDENTIFICADOR URI.

Es importante tener en cuenta que un inicio remoto puede tener como destino un dispositivo remoto (en cuyo caso el dispositivo de host iniciará el URI especificado con su aplicación de forma predeterminada para ese esquema URI) _o_ una aplicación remota específica en ese dispositivo.

Como se muestra la sección anterior, detección se produce en el nivel de dispositivo en primer lugar (un **MCDRemoteSystem** representa un dispositivo), pero se puede llamar a la `getApplications` método en un **MCDRemoteSystem** instancia para obtener una matriz de **MCDRemoteSystemApp** objetos que representan las aplicaciones en el dispositivo remoto que se han registrado para usar la plataforma de dispositivos conectados (tal como se registró su propia aplicación en los pasos preliminares anteriormente). Ambos **MCDRemoteSystem** y **MCDRemoteSystemApp** puede usarse para construir un **MCDRemoteSystemConnectionRequest**, que es lo que hace falta para iniciar un URI.

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

Según el URI que se envía, puede iniciar una aplicación en un estado específico o una configuración en un dispositivo remoto. Esto permite la capacidad de seguir una tarea de usuario, como ver una película en un dispositivo diferente sin interrupción.

Dependiendo de su uso, es posible que deba cubrir los casos en que no hay ninguna aplicación en el sistema de destino puede controlar el identificador URI o varias aplicaciones pueden controlarla. El **[MCDRemoteLauncher](../objectivec-api/remotesystems.commanding/MCDRemoteLauncher.md)** clase y **[MCDRemoteLauncherOptions](../objectivec-api/remotesystems.commanding/MCDRemoteLauncherOptions.md)** clase describen cómo hacer esto.

### <a name="b-remote-app-services"></a>B) servicios de aplicación remoto

La aplicación de iOS puede usar el Portal de dispositivos conectados para interactuar con los servicios de aplicación en otros dispositivos. Esto proporciona muchas formas de comunicarse con otros dispositivos&mdash;todo ello sin necesidad de llevar una aplicación en primer plano del dispositivo host.

#### <a name="set-up-the-app-service-on-the-target-device"></a>Configurar el servicio de aplicaciones en el dispositivo de destino
Esta guía utilizará el [Roman prueba de aplicaciones para Windows](http://aka.ms/romeapp) como servicio de aplicación de destino. Por lo tanto, el código siguiente hará que una aplicación de iOS buscar ese servicio de aplicación específica en el sistema remoto determinado. Si desea probar este escenario, descargue la aplicación de prueba romanos en un dispositivo de Windows y asegúrese de que haya iniciado sesión con el mismo MSA o AAD que usó en los pasos preliminares anteriores.

Para obtener instrucciones sobre cómo escribir su propio servicio de aplicación para UWP, consulte [crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service). Deberá realizar algunos cambios con el fin de que el servicio sea compatible con dispositivos conectados. Consulte la [guía UWP para los servicios de aplicación remota](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service) para obtener instrucciones sobre cómo hacerlo. 

#### <a name="open-an-app-service-connection-on-the-client-device"></a>Abrir una conexión de servicio de aplicación en el dispositivo de cliente
La aplicación de iOS debe adquirir una referencia a una aplicación o dispositivo remoto. Al igual que la sección de inicio, este escenario requiere el uso de un **MCDRemoteSystemConnectionRequest**, que puede crearse desde un **MCDRemoteSystem** o un **MCDRemoteSystemApp**  que representa una aplicación disponible en el sistema.

Además, la aplicación necesitará identificar su servicio de aplicación de destino mediante dos cadenas: el *nombre de app service* y *identificador de paquete*. Estos se encuentran en el código fuente del proveedor de servicios de aplicación (consulte [crear y consumir un servicio de aplicación (UWP)](https://msdn.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener más información). Juntas construyen estas cadenas el **MCDAppServiceDescription**, que se introducen en un **MCDAppServiceConnection** instancia.

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


#### <a name="create-a-message-to-send-to-the-app-service"></a>Crear un mensaje para enviar al servicio de aplicación

Declare una variable para almacenar el mensaje para enviar. En iOS, los mensajes que se envían a los servicios de aplicación remota será de la **NSDictionary** tipo.

> [!NOTE]
> Cuando la aplicación se comunica con servicios de aplicaciones en otras plataformas, la plataforma de dispositivos conectados traduce el **NSDictionary** en la construcción equivalente en la plataforma de destino. Por ejemplo, un **[NSDictionary](https://developer.apple.com/documentation/foundation/nsdictionary)** enviados desde esta aplicación a un Windows servicio de aplicación se traduce en un [ **ValueSet** ](https://msdn.microsoft.com/library/windows/apps/windows.foundation.collections.valueset) objeto (de .NET Marco de trabajo), que, a continuación, se puede interpretar el servicio de aplicación. Información que se pasa en la otra dirección se somete a la traducción inversa.

El siguiente método elabora un mensaje que se puede interpretar por servicio de aplicación de la aplicación de prueba Roman para Windows.

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
> El **NSDictionary** objetos que se pasan entre aplicaciones y servicios en el escenario de servicios de aplicación remota deben cumplir el formato siguiente: Las claves deben ser **NSString**s y los valores pueden ser: **NSString**, conversión boxing a tipos numéricos (enteros o punto flotante), aplicar la conversión boxing de valores booleanos, **NSDate**, **NSUUID**, matrices homogéneas de cualquiera de estos tipos u otros **NSDictionary**  objetos que cumplen esta especificación. 

#### <a name="send-messages-to-the-app-service"></a>Enviar mensajes al servicio de aplicación

Una vez establecida la conexión de servicio de aplicación y se crea el mensaje, enviarlo a app service es sencillo y se puede realizar desde cualquier lugar en la aplicación que tiene una referencia a la instancia de la conexión y el mensaje.

El código del ejemplo siguiente muestra el envío de un mensaje a un servicio de aplicaciones y el control de la respuesta.

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

En el caso de romano App, la respuesta contiene la fecha de creación, por lo que en este caso de uso muy sencillo, podemos comparar las fechas para obtener el tiempo de tránsito total de la respuesta del mensaje.

Esto concluye un intercambio de mensajes solo con un servicio de aplicación remota.

#### <a name="finish-app-service-communication"></a>Finalizar la comunicación del servicio de aplicación

Cuando finalice la aplicación interactúa con el servicio de aplicación del dispositivo de destino, cierre la conexión entre los dos dispositivos.

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
* [aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) 
* [Comunicarse con un servicio de aplicación remota (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/communicate-with-a-remote-app-service)
* [Crear y consumir un servicio de aplicación (UWP)](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service).
