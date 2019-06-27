---
title: include file
description: include file
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801157"
---
## <a name="preliminary-setup-for-push-notifications"></a>Configuración preliminar para las notificaciones push

### <a name="register-your-app-for-push-notifications"></a>Registro de la aplicación para notificaciones push

Registra la aplicación para conseguir la compatibilidad con [Apple Push Notification](https://developer.apple.com/notifications/). No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante. 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>Registro de la aplicación para acceder a la plataforma de dispositivos conectados multidispositivo

A continuación, registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se sigue un procedimiento diferente al registro en el Centro de desarrollo de Windows, que se explicó en los pasos anteriores. Autoriza a la plataforma de dispositivos conectados a enviar notificaciones mediante el servicio de notificaciones push nativo. El proceso de incorporación del Centro de desarrollo necesitará:
* El id. de cliente de la aplicación
* La clave de Apple Push Notification Service Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueado o inactivo) en forma de notificaciones. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configuración de la aplicación para la compatibilidad con las notificaciones

Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push. En primer lugar, asegúrate de agregar el valor "remote-notifications" en **UIBackgroundMode** en el archivo _Info.plist_ de la aplicación, para que esta reciba notificaciones mientras se ejecuta en segundo plano. 

TBD

En segundo lugar, cuando se inicia la aplicación, debes solicitar autorización para mostrar notificaciones de alerta. Esto se hace llamando a `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de cuál es la versión de iOS destinataria. Una vez que la aplicación ha obtenido la autorización, puedes realizar el registro para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`. 

Algunas notificaciones de la plataforma de dispositivos conectados presentarán alertas; el texto de estas alertas es localizable y debe insertarse en recursos de cadena de la aplicación. Debes definir las siguientes etiquetas de recursos en el archivo _en.lproj\Localizable.strings_ de la aplicación. Es posible que debas crear este archivo. En Xcode, selecciona **New** (Nuevo), busque el tipo de archivo "Strings" (Cadenas) y crea un archivo llamado _Localizable.strings_.

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>Asociación del servicio de notificación con la plataforma local

Por último, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados en la aplicación. En los pasos anteriores, inicializaste la plataforma sin definir el parámetro *notificationProvider*. Ahora debes construir y pasar un objeto que implemente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** . Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync:`, que debe devolver una instancia de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** . **MCDNotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.

Incluye este registro en la implementación de **MCDNotificationProvider**. A continuación, la llamada de inicialización de Platform debe proporcionar a la plataforma local acceso al servicio de notificaciones push, permitiendo así que la aplicación reciba datos de la plataforma de dispositivos conectados del servidor, que transmite solicitudes de inicio y mensajes del servicio de aplicación de otros dispositivos. 

A continuación se muestra una implementación de **MCDNotificationProvider** de la aplicación de ejemplo.

```ObjectiveC
@implementation NotificationProvider
{
    MCDRegistrationUpdatedEvent* _registrationUpdated;
    MCDNotificationRegistration* _notificationRegistration;
}

+ (instancetype)sharedInstance
{
    static NotificationProvider* sharedInstance = nil;

    static dispatch_once_t onceToken;
    dispatch_once(&onceToken, ^{ sharedInstance = [[NotificationProvider alloc] init]; });

    return sharedInstance;
}

+ (void)updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0),
        ^{ [[NotificationProvider sharedInstance] _updateNotificationRegistration:notificationRegistration]; });
}

// MCDNotificationProvider
@synthesize registrationUpdated = _registrationUpdated;

- (void)getNotificationRegistrationAsync:(nonnull void (^)(MCDNotificationRegistration* _Nullable, NSError* _Nullable))completionBlock
{
    dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), ^{ completionBlock(_notificationRegistration, nil); });
}

- (instancetype)init
{
    if (self = [super init])
    {
        _registrationUpdated = [MCDRegistrationUpdatedEvent new];
    }

    return self;
}

- (void)_updateNotificationRegistration:(MCDNotificationRegistration*)notificationRegistration
{
    _notificationRegistration = notificationRegistration;

    [_registrationUpdated raiseWithNotificationRegistration:notificationRegistration];
}
@end
```

El siguiente código de ejemplo actualiza esta clase **MCDNotificationProvider** con **MCDNotificationRegistration** rellenado.

```ObjectiveC
/*
* NotificationRegistration is constructed with four parameters:
* Type: This is GCM or FCM or APN (the notification platform type).
* Token: This is the NSData that APNs sends to your app delegate's didRegisterForRemoteNotificationsWithDeviceToken: method. You must convert the NSData into a string by hex-encoding it.
* SenderId: This is your app’s bundle identifier. 
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
[NotificationProvider
    updateNotificationRegistration:[[MCDNotificationRegistration alloc]
        initWithNotificationType:MCDNotificationTypeAPN
        token:deviceTokenStr
        appId:[[NSBundle mainBundle] bundleIdentifier]
        appDisplayName:(NSString*)[[NSBundle mainBundle]
            objectForInfoDictionaryKey:@"CFBundleDisplayName"]]];
```
