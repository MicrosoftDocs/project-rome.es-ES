---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801157"
---
## <a name="preliminary-setup-for-push-notifications"></a>Instalación preliminar para las notificaciones de inserción

### <a name="register-your-app-for-push-notifications"></a>Registrar la aplicación para notificaciones de inserción

Registrar la aplicación para [notificaciones Push de Apple](https://developer.apple.com/notifications/) admite. No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante. 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a>Registrar el acceso a la plataforma de dispositivos conectados de aplicación formulario entre dispositivos

A continuación, registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se trata de un procedimiento diferente al registrar en el centro de desarrollo de Windows, que se tratan en los pasos preliminares anteriores. Se autoriza a la plataforma de dispositivos conectados para enviar notificaciones mediante el servicio de notificaciones de inserción nativa. Se requerirá el proceso de incorporación de centro de desarrollo:
* Identificador de cliente. la aplicación
* La clave de Apple Push Notification Service. Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueados o inactivos) en forma de notificaciones. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configuración de la aplicación para que sea compatible con notificaciones

Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para hacer que sean capaces de recibir notificaciones de inserción. En primer lugar, asegúrese de agregar las "notificaciones de remoto" **UIBackgroundMode** a la aplicación _Info.plist_ para permitir que la aplicación para recibir notificaciones mientras se ejecuta en segundo plano. 

TBD

En segundo lugar, cuando se inicia la aplicación, debe solicitar autorización para mostrar las notificaciones de alerta. Esto se hace llamando `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de qué versión de iOS tiene como destino. Una vez que la aplicación ha adquirido la autorización, a continuación, puede registrar para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`. 

Algunas notificaciones de la plataforma de dispositivos conectados presentan las alertas, y el texto de estas alertas es localizable y debe insertarse en recursos de cadena de la aplicación. Debe definir las siguientes etiquetas de recursos de la aplicación _en.lproj\Localizable.strings_ archivo. Es posible que deba crear este archivo. En Xcode, seleccione **New**, busque el tipo de archivo "Cadenas" y cree un archivo llamado _Localizable.strings_.

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a>Asociar el servicio de notificación de la plataforma local

Por último, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación. En los pasos anteriores, se inicializa la plataforma sin definir la *notificationProvider* parámetro. En este caso, deberá construir y pasar un objeto que implementa  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**. Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync:` método, que debe devolver un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instancia. El **MCDNotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.

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
