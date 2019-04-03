---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907227"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a><span data-ttu-id="2b4d9-103">Asociar la plataforma de dispositivos conectados a la notificación de inserción nativa para cada plataforma móvil.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-103">Associate the Connected Devices Platform with the native push notification for each mobile platform.</span></span> 

<span data-ttu-id="2b4d9-104">Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de notificaciones de inserción nativa que se usa para cada plataforma móvil para el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro para permitir que el gráfico servicio de notificación para enviar notificaciones cargabilidad de salida a cada punto de conexión del cliente de aplicación cuando el servidor de la aplicación publica una notificación de destinatarios de usuario a través de Microsoft Graph API.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-104">Like previously mentioned, the app clients need to provide knowledge about the native push notification pipeline being used for each mobile platform to the client-side SDK and the Connected Devices Platform during the registration process, to allow Graph notification service to fan-out notifications to each app client endpoint when your app server publishes a user-targeting notification via Microsoft Graph APIs.</span></span>

<span data-ttu-id="2b4d9-105">En los pasos anteriores, se inicializa la plataforma con una `null` *notificationProvider* parámetro.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-105">In the steps above, you initialized the Platform with a `null` *notificationProvider* parameter.</span></span> <span data-ttu-id="2b4d9-106">En este caso, deberá construir y pasar un objeto que implementa  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-106">Here, you need to construct and pass in an object that implements **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**.</span></span> <span data-ttu-id="2b4d9-107">Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync` método, que debe devolver un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instancia.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-107">The main thing to note is the `getNotificationRegistrationAsync` method, which must return a **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instance.</span></span> <span data-ttu-id="2b4d9-108">El **NotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-108">The **NotificationRegistration** is responsible for supplying the Connected Devices Platform with an access token (and related information) for the notification service.</span></span>

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

<span data-ttu-id="2b4d9-109">Entregar este registro en la implementación de **NotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-109">Deliver this registration in your implementation of **NotificationProvider**.</span></span> <span data-ttu-id="2b4d9-110">A continuación, la **plataforma** llamada de inicialización debe proporcionar local **plataforma** con acceso al servicio de notificaciones de inserción, que permite a su aplicación recibir datos de las notificaciones de Microsoft Graph en el servidor.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-110">Then, the **Platform** initialization call should provide the local **Platform** with access to the push notification service, allowing your app to receive data from the Microsoft Graph Notifications server-side.</span></span> 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a><span data-ttu-id="2b4d9-111">Pasar notificaciones entrantes de inserción para el SDK de cliente</span><span class="sxs-lookup"><span data-stu-id="2b4d9-111">Pass incoming push notifications to the client SDK</span></span>
<span data-ttu-id="2b4d9-112">Ahora, ampliar el agente de escucha nativa clase de servicio ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que este tutorial se usa Firebase Cloud Messaging) con una sobrecarga especial de la `onMessageReceived` método (la notificación de control método).</span><span class="sxs-lookup"><span data-stu-id="2b4d9-112">Now, extend your native listener service class ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) in this case, because this tutorial uses Firebase Cloud Messaging) with a special overload of the `onMessageReceived` method (the notification-handling method).</span></span>

<span data-ttu-id="2b4d9-113">Debido a posibles optimizaciones, seguridad y cumplimiento de normas, la notificación de Google Cloud Messaging entrante procedentes de las notificaciones de gráfico en el servidor podría ser una derivación de hombros, que no contiene ningún dato que se publica inicialmente por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-113">Due to compliance, security, and potential optimizations, the incoming Google Cloud Messaging notification coming from Graph Notifications server-side could be a shoulder tap, which doesn’t contain any data that is initially published by the app server.</span></span> <span data-ttu-id="2b4d9-114">La recuperación de la notificación real contenida publicada por el servidor de aplicaciones está oculta detrás de la API del SDK de cliente.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-114">The retrieval of the actual notification content published by the app server is hidden behind client-side SDK APIs.</span></span> <span data-ttu-id="2b4d9-115">Por este motivo, el SDK puede proporcionar un modelo de programación coherente en el que el cliente de aplicación siempre pasa la carga entrante de Google Cloud Messaging al SDK.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-115">Because of this, the SDK can provide a consistent programming pattern in which the app client always passes the incoming Google Cloud Messaging payload to the SDK.</span></span> <span data-ttu-id="2b4d9-116">Esto permite que el SDK determinar si se trata de una notificación para escenarios de la plataforma de dispositivo conectado o no (en caso de Android native Google Cloud Messaging canal se utiliza el cliente de aplicación para otros fines) y qué entrantes en este escenario/capacidad notificación se corresponde con (notificaciones de Graph, actividad del usuario, etcetera.).</span><span class="sxs-lookup"><span data-stu-id="2b4d9-116">This allows the SDK to determine whether this is a notification for Connected Device Platform scenarios or not (in case Android’s native Google Cloud Messaging channel is used by the app client for other purposes), and which scenario/capability this incoming notification is corresponding to (Graph Notifications, User Activity, etc.).</span></span> <span data-ttu-id="2b4d9-117">A continuación, se puede ejecutar lógica específica en otro tipo de escenarios de control por el cliente de aplicación después de eso.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-117">Specific logics on handling different type of scenarios can then be executed by the app client after that.</span></span> 

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

<span data-ttu-id="2b4d9-118">La aplicación ahora puede controlar las notificaciones de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="2b4d9-118">Your app can now handle notifications from the Connected Devices Platform.</span></span>

