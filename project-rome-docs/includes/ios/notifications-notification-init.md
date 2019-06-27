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
### <a name="todo-configure-your-app-to-be-apns-notification-compatible"></a><span data-ttu-id="3fd93-103">TAREA: configuración de la aplicación para que sea compatible con las notificaciones de APNS</span><span class="sxs-lookup"><span data-stu-id="3fd93-103">TODO Configure your app to be APNs notification-compatible</span></span>

<span data-ttu-id="3fd93-104">Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="3fd93-104">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="3fd93-105">En primer lugar, asegúrate de agregar el valor "remote-notifications" en **UIBackgroundMode** en el archivo _Info.plist_ de la aplicación, para que esta reciba notificaciones mientras se ejecuta en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="3fd93-105">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="3fd93-106">En segundo lugar, cuando se inicia la aplicación, debes solicitar autorización para mostrar notificaciones de alerta.</span><span class="sxs-lookup"><span data-stu-id="3fd93-106">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="3fd93-107">Esto se hace llamando a `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de cuál es la versión de iOS destinataria.</span><span class="sxs-lookup"><span data-stu-id="3fd93-107">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="3fd93-108">Una vez que la aplicación ha obtenido la autorización, puedes realizar el registro para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="3fd93-108">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

### <a name="associate-the-connected-devices-platform-with-apns-native-push-notification-for-ios"></a><span data-ttu-id="3fd93-109">Asociación de la plataforma de dispositivos conectados con la notificación push nativa de APNS para iOS</span><span class="sxs-lookup"><span data-stu-id="3fd93-109">Associate the Connected Devices Platform with APNs native push notification for iOS.</span></span> 
<span data-ttu-id="3fd93-110">Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de las notificaciones push nativas que se usa para cada plataforma móvil en el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro, de forma que el servicio de notificaciones de Graph pueda realizar la distribución ramificada de las notificaciones a cada punto de conexión cliente de la aplicación cuando el servidor de aplicaciones publique una notificación destinada al usuario a través de las API de MS Graph.</span><span class="sxs-lookup"><span data-stu-id="3fd93-110">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via MS Graph APIs.</span></span>

<span data-ttu-id="3fd93-111">En los pasos anteriores, inicializaste la plataforma sin definir el parámetro *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="3fd93-111">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="3fd93-112">Ahora debes construir y pasar un objeto que implemente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** .</span><span class="sxs-lookup"><span data-stu-id="3fd93-112">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="3fd93-113">Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync:`, que debe devolver una instancia de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** .</span><span class="sxs-lookup"><span data-stu-id="3fd93-113">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="3fd93-114">**MCDNotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="3fd93-114">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="3fd93-115">Incluye este registro en la implementación de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="3fd93-115">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="3fd93-116">A continuación, la llamada de inicialización de Platform debe proporcionar a la plataforma local acceso al servicio de notificaciones push, permitiendo así que la aplicación reciba datos de la plataforma de dispositivos conectados del servidor, que transmite solicitudes de inicio y mensajes del servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3fd93-116">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="3fd93-117">A continuación se muestra una implementación de **MCDNotificationProvider** de la aplicación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="3fd93-117">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="3fd93-118">El siguiente código de ejemplo actualiza esta clase **MCDNotificationProvider** con **MCDNotificationRegistration** rellenado.</span><span class="sxs-lookup"><span data-stu-id="3fd93-118">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
