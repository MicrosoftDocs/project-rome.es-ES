---
title: include file
description: include file
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801805"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="6b07a-103">Asociación de la plataforma de dispositivos conectados a la notificación push nativa para cada plataforma móvil</span><span class="sxs-lookup"><span data-stu-id="6b07a-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="6b07a-104">Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de las notificaciones push nativas que se usa para cada plataforma móvil en el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro, de forma que el servicio de notificaciones de Graph pueda realizar la distribución ramificada de las notificaciones a cada punto de conexión cliente de la aplicación cuando el servidor de aplicaciones publique una notificación destinada al usuario a través de las API de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="6b07a-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="6b07a-105">En los pasos anteriores, inicializaste la plataforma con un parámetro `null` *notificationProvider*.</span><span class="sxs-lookup"><span data-stu-id="6b07a-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="6b07a-106">Ahora debes construir y pasar un objeto que implemente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** .</span><span class="sxs-lookup"><span data-stu-id="6b07a-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="6b07a-107">Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync`, que debe devolver una instancia de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** .</span><span class="sxs-lookup"><span data-stu-id="6b07a-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="6b07a-108">**NotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="6b07a-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

```java
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

<span data-ttu-id="6b07a-109">Incluye este registro en la implementación de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="6b07a-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="6b07a-110">A continuación, la llamada de inicialización de **Platform** debe proporcionar a la instancia de **Platform** local el acceso al servicio de notificaciones push, lo que permite que la aplicación reciba datos de las notificaciones de Microsoft Graph en el servidor.</span><span class="sxs-lookup"><span data-stu-id="6b07a-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="6b07a-111">Paso de notificaciones push entrantes al SDK de cliente</span><span class="sxs-lookup"><span data-stu-id="6b07a-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="6b07a-112">Ahora, amplía la clase del servicio del cliente de escucha nativo ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que este tutorial utiliza Firebase Cloud Messaging) con una sobrecarga especial del método `onMessageReceived` (el método de administración de notificaciones).</span><span class="sxs-lookup"><span data-stu-id="6b07a-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="6b07a-113">Por motivos de cumplimiento, seguridad y posibles optimizaciones, la notificación entrante de Google Cloud Messaging procedente de las notificaciones de Graph en el servidor podría ser un simple toque, que no contenga ningún dato inicialmente publicado por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="6b07a-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="6b07a-114">La recuperación del contenido real de la notificación publicada por el servidor de aplicaciones se oculta detrás de las API del SDK de cliente.</span><span class="sxs-lookup"><span data-stu-id="6b07a-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="6b07a-115">Por este motivo, el SDK puede proporcionar un modelo de programación coherente en el que el cliente de la aplicación siempre pase la carga entrante de Google Cloud Messaging al SDK.</span><span class="sxs-lookup"><span data-stu-id="6b07a-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="6b07a-116">Esto permite que el SDK determine si se trata de una notificación para escenarios de la plataforma de dispositivos conectados o no (en caso de que el cliente de la aplicación utilice el canal de Google Cloud Messaging nativo de Android para otros fines) y a qué escenario o capacidad corresponde esta notificación entrante (Notificaciones de Graph, Actividad del usuario, etc.).</span><span class="sxs-lookup"><span data-stu-id="6b07a-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="6b07a-117">Tras esto, el cliente de la aplicación puede ejecutar lógicas específicas al tratar con diferentes tipos de escenarios.</span><span class="sxs-lookup"><span data-stu-id="6b07a-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

```java
/**
* Check whether it's a Connected Devices Platform notification or not.
* If it is a Connected Devices Platform notification, it will notify the apps with the information in the notification.
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

<span data-ttu-id="6b07a-118">Ahora la aplicación puede controlar notificaciones de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="6b07a-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>

