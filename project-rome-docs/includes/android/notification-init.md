---
title: include file
description: include file
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801578"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="158bd-103">Configuración preliminar para las notificaciones push</span><span class="sxs-lookup"><span data-stu-id="158bd-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="158bd-104">Registro de la aplicación para notificaciones push</span><span class="sxs-lookup"><span data-stu-id="158bd-104">Register your app for push notifications</span></span>

<span data-ttu-id="158bd-105">Registra la aplicación con Google para la compatibilidad con las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="158bd-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="158bd-106">No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante.</span><span class="sxs-lookup"><span data-stu-id="158bd-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="158bd-107">Registro de la aplicación para acceder a la plataforma de dispositivos conectados multidispositivo</span><span class="sxs-lookup"><span data-stu-id="158bd-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="158bd-108">A continuación, registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="158bd-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="158bd-109">Se sigue un procedimiento diferente al registro en el Centro de desarrollo de Windows, que se explicó en los pasos anteriores.</span><span class="sxs-lookup"><span data-stu-id="158bd-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="158bd-110">Autoriza a la plataforma de dispositivos conectados a enviar notificaciones mediante el servicio de notificaciones push nativo.</span><span class="sxs-lookup"><span data-stu-id="158bd-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="158bd-111">El proceso de incorporación del Centro de desarrollo necesitará:</span><span class="sxs-lookup"><span data-stu-id="158bd-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="158bd-112">El id. de cliente de la aplicación</span><span class="sxs-lookup"><span data-stu-id="158bd-112">Your app's client ID.</span></span>
* <span data-ttu-id="158bd-113">La clave de Google Cloud Messaging</span><span class="sxs-lookup"><span data-stu-id="158bd-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="158bd-114">Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueado o inactivo) en forma de notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="158bd-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="158bd-115">Configuración de la aplicación para la compatibilidad con las notificaciones</span><span class="sxs-lookup"><span data-stu-id="158bd-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="158bd-116">Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="158bd-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="158bd-117">Consulta [Configura una app cliente de Firebase Cloud Messaging en Android](https://firebase.google.com/docs/cloud-messaging/android/client) si no sabes cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="158bd-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="158bd-118">Asociación del servicio de notificación con la plataforma local</span><span class="sxs-lookup"><span data-stu-id="158bd-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="158bd-119">Por último, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="158bd-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="158bd-120">En los pasos anteriores, inicializaste la plataforma con un parámetro *notificationProvider* `null`.</span><span class="sxs-lookup"><span data-stu-id="158bd-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="158bd-121">Ahora debes construir y pasar un objeto que implemente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** .</span><span class="sxs-lookup"><span data-stu-id="158bd-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="158bd-122">Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync`, que debe devolver una instancia de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** .</span><span class="sxs-lookup"><span data-stu-id="158bd-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="158bd-123">**NotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="158bd-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


```Java
private NotificationRegistration mNotificationRegistration;

// ...

/**
* NotificationRegistration is constructed with four parameters:
* Type: This is the notification platform type.
* Token: This is the string that GCM or FCM sends to your registration intent service.
* SenderId: This is the numeric Sender ID that you received when you registered your app for push notifications.
* DisplayName: This should be the name of the app that you used when you registered it on the Microsoft dev portal. 
*/
mNotificationRegistration = new NotificationRegistration(NotificationType.FCM, token, FCM_SENDER_ID, "MyAppName");
```

<span data-ttu-id="158bd-124">Incluye este registro en la implementación de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="158bd-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="158bd-125">A continuación, la llamada de inicialización de **Platform** debe proporcionar a la instancia de **Platform** local acceso al servicio de notificaciones push, permitiendo así que la aplicación reciba datos de la plataforma de dispositivos conectados del servidor, que transmite solicitudes de inicio y mensajes del servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="158bd-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="158bd-126">Ahora todo lo que necesitas hacer es ampliar la clase del servicio del cliente de escucha nativo ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que esta guía utiliza Firebase Cloud Messaging) con una sobrecarga especial del método `onMessageReceived` (el método de administración de notificaciones).</span><span class="sxs-lookup"><span data-stu-id="158bd-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

```Java
/**
* Check whether it's a rome notification or not.
* If it is a rome notification, it will notify the apps with the information in the notification.
* @param from describes message sender.
* @param data message data as String key/value pairs.
*/
@Override
public void onMessageReceived(String from, Bundle data) {
    Log.d(TAG, "From: " + from);

    // Ensure that the Platform is initialized here before going on
    // ...

    // This method passes the data to the Connected Devices Platform if is compatible.
    if (!NotificationReceiver.Receive(data)) {
        // a value of false indicates a non-Rome notification
        Log.d(TAG, "GCM client received a message that was not a Rome notification");
    }
}
```

<span data-ttu-id="158bd-127">La aplicación ya puede controlar las notificaciones de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="158bd-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
