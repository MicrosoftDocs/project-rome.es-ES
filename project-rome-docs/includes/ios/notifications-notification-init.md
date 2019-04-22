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
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="8038d-103">Lista de tareas Configurar la aplicación sea compatible con notificaciones de APNs</span><span class="sxs-lookup"><span data-stu-id="8038d-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="8038d-104">Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para hacer que sean capaces de recibir notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="8038d-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="8038d-105">En primer lugar, asegúrese de agregar las "notificaciones de remoto" **UIBackgroundMode** a la aplicación _Info.plist_ para permitir que la aplicación para recibir notificaciones mientras se ejecuta en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="8038d-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="8038d-106">En segundo lugar, cuando se inicia la aplicación, debe solicitar autorización para mostrar las notificaciones de alerta.</span><span class="sxs-lookup"><span data-stu-id="8038d-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="8038d-107">Esto se hace llamando `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de qué versión de iOS tiene como destino.</span><span class="sxs-lookup"><span data-stu-id="8038d-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="8038d-108">Una vez que la aplicación ha adquirido la autorización, a continuación, puede registrar para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="8038d-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="8038d-109">Asocie la plataforma de dispositivos conectados con la notificación de inserción nativa de APNs para iOS.</span><span class="sxs-lookup"><span data-stu-id="8038d-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="8038d-110">Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de notificaciones de inserción nativa que se usa para cada plataforma móvil para el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro para permitir que el gráfico servicio de notificación para enviar notificaciones cargabilidad de salida a cada punto de conexión del cliente de aplicación cuando el servidor de la aplicación publica una notificación de destinatarios de usuario a través de MS Graph API.</span><span class="sxs-lookup"><span data-stu-id="8038d-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="8038d-111">En los pasos anteriores, se inicializa la plataforma sin definir la *notificationProvider* parámetro.</span><span class="sxs-lookup"><span data-stu-id="8038d-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="8038d-112">En este caso, deberá construir y pasar un objeto que implementa  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span><span class="sxs-lookup"><span data-stu-id="8038d-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="8038d-113">Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync:` método, que debe devolver un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instancia.</span><span class="sxs-lookup"><span data-stu-id="8038d-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="8038d-114">El **MCDNotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="8038d-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="8038d-115">Entregar este registro en la implementación de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="8038d-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="8038d-116">A continuación, la llamada de inicialización de la plataforma debe proporcionar una plataforma local con acceso al servicio de notificaciones de inserción, lo que permite la aplicación recibir datos de la plataforma de dispositivos conectados de lado servidor, que transmite las solicitudes de inicio y los mensajes del servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="8038d-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="8038d-117">La siguiente es una implementación de **MCDNotificationProvider** desde la aplicación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8038d-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="8038d-118">El código de ejemplo siguiente actualiza esta **MCDNotificationProvider** con un rellenado de **MCDNotificationRegistration**.</span><span class="sxs-lookup"><span data-stu-id="8038d-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
