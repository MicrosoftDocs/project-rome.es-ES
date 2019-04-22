---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801578"
---
## <a name="preliminary-setup-for-push-notifications"></a><span data-ttu-id="6f7bb-103">Instalación preliminar para las notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="6f7bb-103">Preliminary setup for push notifications</span></span>

### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="6f7bb-104">Registrar la aplicación para notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="6f7bb-104">Register your app for push notifications</span></span>

<span data-ttu-id="6f7bb-105">Registrar la aplicación con Google para la compatibilidad con las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-105">Register your application with Google for notification support.</span></span> <span data-ttu-id="6f7bb-106">No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-106">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span> 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a><span data-ttu-id="6f7bb-107">Registrar la aplicación obtener acceso a la plataforma de dispositivos conectados entre dispositivos</span><span class="sxs-lookup"><span data-stu-id="6f7bb-107">Register your app for cross-device Connected Devices Platform access</span></span>

<span data-ttu-id="6f7bb-108">A continuación, registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="6f7bb-108">Next, register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="6f7bb-109">Se trata de un procedimiento diferente al registrar en el centro de desarrollo de Windows, que se tratan en los pasos preliminares anteriores.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-109">This is a different procedure from registering on the Windows Dev Center, which was covered in the preliminary steps above.</span></span> <span data-ttu-id="6f7bb-110">Se autoriza a la plataforma de dispositivos conectados para enviar notificaciones mediante el servicio de notificaciones de inserción nativa.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-110">It authorizes the Connected Devices Platform to send notifications using the native push notification service.</span></span> <span data-ttu-id="6f7bb-111">Se requerirá el proceso de incorporación de centro de desarrollo:</span><span class="sxs-lookup"><span data-stu-id="6f7bb-111">The Dev Center on-boarding process will require:</span></span>
* <span data-ttu-id="6f7bb-112">Identificador de cliente. la aplicación</span><span class="sxs-lookup"><span data-stu-id="6f7bb-112">Your app's client ID.</span></span>
* <span data-ttu-id="6f7bb-113">The Google Cloud Messaging key.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-113">The Google Cloud Messaging key.</span></span> <span data-ttu-id="6f7bb-114">Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueados o inactivos) en forma de notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-114">This is needed in order to deliver data and commands to the app (on a device which may be locked or asleep) in the form of push notifications.</span></span> 

### <a name="configure-your-app-to-be-notification-compatible"></a><span data-ttu-id="6f7bb-115">Configuración de la aplicación para que sea compatible con notificaciones</span><span class="sxs-lookup"><span data-stu-id="6f7bb-115">Configure your app to be notification-compatible</span></span>

<span data-ttu-id="6f7bb-116">Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para que sea capaz de recibir notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-116">After you complete the workflow on the Developer dashboard, you must modify the actual code of your app to make it capable of receiving push notifications.</span></span> <span data-ttu-id="6f7bb-117">Consulte [establecer seguridad unas Firebase Cloud mensajería aplicación cliente en Android](https://firebase.google.com/docs/cloud-messaging/android/client) si no está seguro de cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-117">See [Set Up a Firebase Cloud Messaging Client App on Android](https://firebase.google.com/docs/cloud-messaging/android/client) if you are unsure how to do this.</span></span>

### <a name="associate-the-notification-service-with-the-local-platform"></a><span data-ttu-id="6f7bb-118">Asociar el servicio de notificación de la plataforma local</span><span class="sxs-lookup"><span data-stu-id="6f7bb-118">Associate the notification service with the local Platform</span></span>

<span data-ttu-id="6f7bb-119">Por último, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-119">Finally, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span> <span data-ttu-id="6f7bb-120">En los pasos anteriores, se inicializa la plataforma con una `null` *notificationProvider* parámetro.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-120">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="6f7bb-121">En este caso, deberá construir y pasar un objeto que implementa  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-121">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="6f7bb-122">Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync` método, que debe devolver un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instancia.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-122">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="6f7bb-123">El **NotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-123">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>


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

<span data-ttu-id="6f7bb-124">Entregar este registro en la implementación de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-124">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="6f7bb-125">A continuación, la **plataforma** llamada de inicialización debe proporcionar local **plataforma** con el acceso al servicio de notificaciones de inserción, lo que permite la aplicación recibir datos de los dispositivos conectados de lado servidor Plataforma, que retransmite solicitudes de inicio y los mensajes de servicio de aplicación de otros dispositivos.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-125">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the server-side Connected Devices Platform, which relays launch requests and app service messages from other devices.</span></span> 

<span data-ttu-id="6f7bb-126">Ahora todo lo que necesita hacer es ampliar el agente de escucha nativa clase de servicio ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que esta guía usa Firebase Cloud Messaging) con una sobrecarga de especial la `onMessageReceived` método (el método de control de notificación).</span><span class="sxs-lookup"><span data-stu-id="6f7bb-126">All you need to do now is extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this guide used Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

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

<span data-ttu-id="6f7bb-127">La aplicación ahora es capaz de controlar las notificaciones de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6f7bb-127">Your app is now able to handle notifications from the Connected Devices Platform.</span></span>
