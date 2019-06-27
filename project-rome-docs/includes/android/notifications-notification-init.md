---
title: include file
description: include file
ms.topic: include
ms.assetid: 9fb27596-e9a3-443a-9c12-9e02a893e32c
ms.localizationpriority: medium
ms.openlocfilehash: 27ff12ef8b0773f1bd0e1960c285012f7e62fdc9
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801805"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>Asociación de la plataforma de dispositivos conectados a la notificación push nativa para cada plataforma móvil 

Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de las notificaciones push nativas que se usa para cada plataforma móvil en el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro, de forma que el servicio de notificaciones de Graph pueda realizar la distribución ramificada de las notificaciones a cada punto de conexión cliente de la aplicación cuando el servidor de aplicaciones publique una notificación destinada al usuario a través de las API de Microsoft Graph.

En los pasos anteriores, inicializaste la plataforma con un parámetro *notificationProvider* `null`. Ahora debes construir y pasar un objeto que implemente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** . Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync`, que debe devolver una instancia de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** . **NotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.

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

Incluye este registro en la implementación de **NotificationProvider**. A continuación, la llamada de inicialización de **Platform** debe proporcionar a la instancia de **Platform** local el acceso al servicio de notificaciones push, lo que permite que la aplicación reciba datos de las notificaciones de Microsoft Graph en el servidor. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Paso de notificaciones push entrantes al SDK de cliente
Ahora, amplía la clase del servicio del cliente de escucha nativo ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que este tutorial utiliza Firebase Cloud Messaging) con una sobrecarga especial del método `onMessageReceived` (el método de administración de notificaciones).

Por motivos de cumplimiento, seguridad y posibles optimizaciones, la notificación entrante de Google Cloud Messaging procedente de las notificaciones de Graph en el servidor podría ser un simple toque, que no contenga ningún dato inicialmente publicado por el servidor de aplicaciones. La recuperación del contenido real de la notificación publicada por el servidor de aplicaciones se oculta detrás de las API del SDK de cliente. Por este motivo, el SDK puede proporcionar un modelo de programación coherente en el que el cliente de la aplicación siempre pase la carga entrante de Google Cloud Messaging al SDK. Esto permite que el SDK determine si se trata de una notificación para escenarios de la plataforma de dispositivos conectados o no (en caso de que el cliente de la aplicación utilice el canal de Google Cloud Messaging nativo de Android para otros fines) y a qué escenario o capacidad corresponde esta notificación entrante (Notificaciones de Graph, Actividad del usuario, etc.). Tras esto, el cliente de la aplicación puede ejecutar lógicas específicas al tratar con diferentes tipos de escenarios. 

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

Ahora la aplicación puede controlar notificaciones de la plataforma de dispositivos conectados.

