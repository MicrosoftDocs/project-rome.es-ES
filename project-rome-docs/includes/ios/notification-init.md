---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 195e419e-ac8d-4e96-8faa-c3659570fa27
ms.localizationpriority: medium
ms.openlocfilehash: 1780fa768475015946b5e33add55ac0f9f247f86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909667"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="2ec3a-103">Instalación preliminar para las notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="2ec3a-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="2ec3a-104">Registrar la aplicación para notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="2ec3a-104">Register your app for push notifications</span></span>

<span data-ttu-id="2ec3a-105">Registrar la aplicación para [notificaciones Push de Apple](https://developer.apple.com/notifications/) admite.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-105">Register your application for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="2ec3a-106">No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-form-cross-device-connected-devices-platform-access"></a><span data-ttu-id="2ec3a-107">Registrar el acceso a la plataforma de dispositivos conectados de aplicación formulario entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="2ec3a-107">Register your app form cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="2ec3a-108">A continuación, registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="2ec3a-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="2ec3a-109">Se trata de un procedimiento diferente al registrar en el centro de desarrollo de Windows, que se tratan en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="2ec3a-110">Se autoriza a la plataforma de dispositivos conectados para enviar notificaciones mediante el servicio de notificaciones de inserción nativa.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="2ec3a-111">Se requerirá el proceso de incorporación de centro de desarrollo:</span><span class="sxs-lookup"><span data-stu-id="2ec3a-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="2ec3a-112">Identificador de cliente. la aplicación</span><span class="sxs-lookup"><span data-stu-id="2ec3a-112">Your app's client ID.</span></span>
* <span data-ttu-id="2ec3a-113">La clave de Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-113">The Apple Push Notification Service key.</span></span> <span data-ttu-id="2ec3a-114">Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueados o inactivos) en forma de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="2ec3a-115">Configuración de la aplicación para que sea compatible con notificaciones</span><span class="sxs-lookup"><span data-stu-id="2ec3a-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="2ec3a-116">Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para hacer que sean capaces de recibir notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make capable of receiving push notifications.</span></span> <span data-ttu-id="2ec3a-117">En primer lugar, asegúrese de agregar las "notificaciones de remoto" **UIBackgroundMode** a la aplicación _Info.plist_ para permitir que la aplicación para recibir notificaciones mientras se ejecuta en segundo plano.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-117">First, make sure to add the "remote-notifications" **UIBackgroundMode** to your app's _Info.plist_ to allow the app to receive notifications while running in the background.</span></span> 

<span data-ttu-id="2ec3a-118">TBD</span><span class="sxs-lookup"><span data-stu-id="2ec3a-118">TBD</span></span>

<span data-ttu-id="2ec3a-119">En segundo lugar, cuando se inicia la aplicación, debe solicitar autorización para mostrar las notificaciones de alerta.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-119">Second, when your app starts up, you must request authorization to display alert notifications.</span></span> <span data-ttu-id="2ec3a-120">Esto se hace llamando `-[UIApplication registerUsernotificationSettings:categories:]` o `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, dependiendo de qué versión de iOS tiene como destino.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-120">This is done by calling either `-[UIApplication registerUsernotificationSettings:categories:]` or `-[UNUserNotificationCenter requestAuthorizationWithOptions:completionHandler:]`, depending on what version of iOS you're targeting.</span></span> <span data-ttu-id="2ec3a-121">Una vez que la aplicación ha adquirido la autorización, a continuación, puede registrar para recibir notificaciones remotas mediante una llamada a `-[UIApplication registerForRemoteNotifications]`.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-121">Once your app has acquired the authorization, you can then register to receive remote notifications by calling `-[UIApplication registerForRemoteNotifications]`.</span></span> 

<span data-ttu-id="2ec3a-122">Algunas notificaciones de la plataforma de dispositivos conectados presentan las alertas, y el texto de estas alertas es localizable y debe insertarse en recursos de cadena de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-122">Some notifications from the Connected Devices Platform will present alerts, and the text of these alerts is localizable and must be inserted into your application's string resources.</span></span> <span data-ttu-id="2ec3a-123">Debe definir las siguientes etiquetas de recursos de la aplicación _en.lproj\Localizable.strings_ archivo.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-123">You must define the following resource tags in your app's _en.lproj\Localizable.strings_ file.</span></span> <span data-ttu-id="2ec3a-124">Es posible que deba crear este archivo.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-124">You may need to create this file.</span></span> <span data-ttu-id="2ec3a-125">En Xcode, seleccione **New**, busque el tipo de archivo "Cadenas" y cree un archivo llamado _Localizable.strings_.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-125">In Xcode, select **New**, search for the file type "Strings", and create a file called _Localizable.strings_.</span></span>

```ObjectiveC
/* The text of the toast notification to display when a remote command is received */ 
"ROME_REMOTE_LAUNCH" = "%1$@ wants to launch this app"; 
"ROME_REMOTE_LAUNCH_FROM_APP" = "%1$@ on %2$@ wants to launch this app"; 
 
/* The text of the toast notification to display when multiple remote commands are received simultaneously */ 
"ROME_CONNECT_TEXT_MANY" = "Another device wants to launch this app"; 
```

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="2ec3a-126">Asociar el servicio de notificación de la plataforma local</span><span class="sxs-lookup"><span data-stu-id="2ec3a-126">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="2ec3a-127">Por último, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-127">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="2ec3a-128">En los pasos anteriores, se inicializa la plataforma sin definir la *notificationProvider* parámetro.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-128">In the steps above, you initialized the Platform without defining the *notificationProvider* parameter.</span></span> <span data-ttu-id="2ec3a-129">En este caso, deberá construir y pasar un objeto que implementa  **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-129">Here, you need to construct and pass in an object that implements **[MCDNotificationProvider](../../objectivec-api/core/MCDNotificationProvider.md)**.</span></span> <span data-ttu-id="2ec3a-130">Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync:` método, que debe devolver un **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instancia.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-130">The main thing to note is the `getNotificationRegistrationAsync:` method, which must return a **[MCDNotificationRegistration](../../objectivec-api/core/MCDNotificationRegistration.md)** instance.</span></span> <span data-ttu-id="2ec3a-131">El **MCDNotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-131">The **MCDNotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

<span data-ttu-id="2ec3a-132">Entregar este registro en la implementación de **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-132">Deliver this registration in your implementation of **MCDNotificationProvider**.</span></span> <span data-ttu-id="2ec3a-133">A continuación, la llamada de inicialización de la plataforma debe proporcionar una plataforma local con acceso al servicio de notificaciones de inserción, lo que permite la aplicación recibir datos de la plataforma de dispositivos conectados de lado servidor, que transmite las solicitudes de inicio y los mensajes del servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-133">Then, the Platform initialization call should provide the local Platform with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="2ec3a-134">La siguiente es una implementación de **MCDNotificationProvider** desde la aplicación de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-134">The following is an implementation of **MCDNotificationProvider** from the sample app.</span></span>

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

<span data-ttu-id="2ec3a-135">El código de ejemplo siguiente actualiza esta **MCDNotificationProvider** con un rellenado de **MCDNotificationRegistration**.</span><span class="sxs-lookup"><span data-stu-id="2ec3a-135">The following sample code updates this **MCDNotificationProvider** with a filled-in **MCDNotificationRegistration**.</span></span>

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
