---
title: include file
description: include file
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801507"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>TAREA: configuración de la aplicación para que sea compatible con las notificaciones de APNS

Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push. En primer lugar, asegúrate de agregar el valor "remote-notifications" en **UIBackgroundMode** en el archivo _Info.plist_ de la aplicación, para que esta reciba notificaciones mientras se ejecuta en segundo plano. 

En segundo lugar, cuando se inicia la aplicación, debes solicitar autorización para mostrar notificaciones de alerta. Esto se hace llamando a `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de cuál es la versión de iOS destinataria. Una vez que la aplicación ha obtenido la autorización, puedes realizar el registro para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`. 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>Asociación de la plataforma de dispositivos conectados con la notificación push nativa de APNS para iOS 
Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de las notificaciones push nativas que se usa para cada plataforma móvil en el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro, de forma que el servicio de notificaciones de Graph pueda realizar la distribución ramificada de las notificaciones a cada punto de conexión cliente de la aplicación cuando el servidor de aplicaciones publique una notificación destinada al usuario a través de las API de MS Graph.

En los pasos anteriores, inicializaste la plataforma sin definir el parámetro *notificationProvider*. Ahora debes construir y pasar un objeto que implemente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** . Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync:`, que debe devolver una instancia de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** . **MCDNotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.

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
