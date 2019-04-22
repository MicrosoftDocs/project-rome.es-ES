---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 30df8538-1c1f-498f-af25-0be0aed687c8
ms.localizationpriority: medium
ms.openlocfilehash: 95b6dd68706a1582a91718a48ba7961cd8d07ddf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801507"
---
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a>Lista de tareas Configurar la aplicación sea compatible con notificaciones de APNs

Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para hacer que sean capaces de recibir notificaciones de inserción. En primer lugar, asegúrese de agregar las "notificaciones de remoto" **UIBackgroundMode** a la aplicación _Info.plist_ para permitir que la aplicación para recibir notificaciones mientras se ejecuta en segundo plano. 

En segundo lugar, cuando se inicia la aplicación, debe solicitar autorización para mostrar las notificaciones de alerta. Esto se hace llamando `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de qué versión de iOS tiene como destino. Una vez que la aplicación ha adquirido la autorización, a continuación, puede registrar para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`. 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a>Asocie la plataforma de dispositivos conectados con la notificación de inserción nativa de APNs para iOS. 
Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de notificaciones de inserción nativa que se usa para cada plataforma móvil para el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro para permitir que el gráfico servicio de notificación para enviar notificaciones cargabilidad de salida a cada punto de conexión del cliente de aplicación cuando el servidor de la aplicación publica una notificación de destinatarios de usuario a través de MS Graph API.

En los pasos anteriores, se inicializa la plataforma sin definir la *notificationProvider* parámetro. En este caso, deberá construir y pasar un objeto que implementa  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**. Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync:` método, que debe devolver un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instancia. El **MCDNotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.

Entregar este registro en la implementación de **MCDNotificationProvider**. A continuación, la llamada de inicialización de la plataforma debe proporcionar una plataforma local con acceso al servicio de notificaciones de inserción, lo que permite la aplicación recibir datos de la plataforma de dispositivos conectados de lado servidor, que transmite las solicitudes de inicio y los mensajes del servicio de aplicación de otros dispositivos. 

La siguiente es una implementación de **MCDNotificationProvider** desde la aplicación de ejemplo.

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

El código de ejemplo siguiente actualiza esta **MCDNotificationProvider** con un rellenado de **MCDNotificationRegistration**.

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
