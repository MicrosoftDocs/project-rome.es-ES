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
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="a5999-103">Configuración preliminar para las notificaciones push</span><span class="sxs-lookup"><span data-stu-id="a5999-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="a5999-104">Registro de la aplicación para notificaciones push</span><span class="sxs-lookup"><span data-stu-id="a5999-104">Register your app for push notifications</span></span>

<span data-ttu-id="a5999-105">Registra la aplicación para conseguir la compatibilidad con [Apple Push Notification](https://developer.apple.com/notifications/).</span><span class="sxs-lookup"><span data-stu-id="a5999-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="a5999-106">No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante.</span><span class="sxs-lookup"><span data-stu-id="a5999-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="a5999-107">Registro de la aplicación para acceder a la plataforma de dispositivos conectados multidispositivo</span><span class="sxs-lookup"><span data-stu-id="a5999-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="a5999-108">A continuación, registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="a5999-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="a5999-109">Se sigue un procedimiento diferente al registro en el Centro de desarrollo de Windows, que se explicó en los pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="a5999-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="a5999-110">Autoriza a la plataforma de dispositivos conectados a enviar notificaciones mediante el servicio de notificaciones push nativo.</span><span class="sxs-lookup"><span data-stu-id="a5999-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="a5999-111">El proceso de incorporación del Centro de desarrollo necesitará:</span><span class="sxs-lookup"><span data-stu-id="a5999-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="a5999-112">El id. de cliente de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a5999-112">Your app's client ID.</span></span>
* <span data-ttu-id="a5999-113">La clave de Apple Push Notification Service</span><span class="sxs-lookup"><span data-stu-id="a5999-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="a5999-114">Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueado o inactivo) en forma de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="a5999-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="a5999-115">Configuración de la aplicación para la compatibilidad con las notificaciones</span><span class="sxs-lookup"><span data-stu-id="a5999-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="a5999-116">Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="a5999-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="a5999-117">En primer lugar, asegúrate de agregar el valor "remote-notifications" en **UIBackgroundMode** en el archivo _Info.plist_ de la aplicación, para que esta reciba notificaciones mientras se ejecuta en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="a5999-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="a5999-118">TBD</span><span class="sxs-lookup"><span data-stu-id="a5999-118">TBD</span></span>

<span data-ttu-id="a5999-119">En segundo lugar, cuando se inicia la aplicación, debes solicitar autorización para mostrar notificaciones de alerta.</span><span class="sxs-lookup"><span data-stu-id="a5999-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="a5999-120">Esto se hace llamando a `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de cuál es la versión de iOS destinataria.</span><span class="sxs-lookup"><span data-stu-id="a5999-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="a5999-121">Una vez que la aplicación ha obtenido la autorización, puedes realizar el registro para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="a5999-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="a5999-122">Algunas notificaciones de la plataforma de dispositivos conectados presentarán alertas; el texto de estas alertas es localizable y debe insertarse en recursos de cadena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5999-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="a5999-123">Debes definir las siguientes etiquetas de recursos en el archivo _en.lproj\Localizable.strings_ de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5999-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="a5999-124">Es posible que debas crear este archivo.</span><span class="sxs-lookup"><span data-stu-id="a5999-124">You may need to create this file.</span></span> <span data-ttu-id="a5999-125">En Xcode, selecciona **New** (Nuevo), busque el tipo de archivo "Strings" (Cadenas) y crea un archivo llamado _Localizable.strings_.</span><span class="sxs-lookup"><span data-stu-id="a5999-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="a5999-126">Asociación del servicio de notificación con la plataforma local</span><span class="sxs-lookup"><span data-stu-id="a5999-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="a5999-127">Por último, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a5999-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="a5999-128">En los pasos anteriores, inicializaste la plataforma sin definir el parámetro *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="a5999-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="a5999-129">Ahora debes construir y pasar un objeto que implemente **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)** .</span><span class="sxs-lookup"><span data-stu-id="a5999-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="a5999-130">Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync:`, que debe devolver una instancia de **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** .</span><span class="sxs-lookup"><span data-stu-id="a5999-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="a5999-131">**MCDNotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="a5999-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="a5999-132">Incluye este registro en la implementación de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="a5999-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="a5999-133">A continuación, la llamada de inicialización de Platform debe proporcionar a la plataforma local acceso al servicio de notificaciones push, permitiendo así que la aplicación reciba datos de la plataforma de dispositivos conectados del servidor, que transmite solicitudes de inicio y mensajes del servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a5999-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="a5999-134">A continuación se muestra una implementación de **MCDNotificationProvider** de la aplicación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a5999-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="a5999-135">El siguiente código de ejemplo actualiza esta clase **MCDNotificationProvider** con **MCDNotificationRegistration** rellenado.</span><span class="sxs-lookup"><span data-stu-id="a5999-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
