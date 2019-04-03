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
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-mobile-platform"></a>Asociar la plataforma de dispositivos conectados a la notificación de inserción nativa para cada plataforma móvil. 

Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de notificaciones de inserción nativa que se usa para cada plataforma móvil para el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro para permitir que el gráfico servicio de notificación para enviar notificaciones cargabilidad de salida a cada punto de conexión del cliente de aplicación cuando el servidor de la aplicación publica una notificación de destinatarios de usuario a través de Microsoft Graph API.

En los pasos anteriores, se inicializa la plataforma con una `null` *notificationProvider* parámetro. En este caso, deberá construir y pasar un objeto que implementa  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**. Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync` método, que debe devolver un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instancia. El **NotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.

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

Entregar este registro en la implementación de **NotificationProvider**. A continuación, la **plataforma** llamada de inicialización debe proporcionar local **plataforma** con acceso al servicio de notificaciones de inserción, que permite a su aplicación recibir datos de las notificaciones de Microsoft Graph en el servidor. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Pasar notificaciones entrantes de inserción para el SDK de cliente
Ahora, ampliar el agente de escucha nativa clase de servicio ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que este tutorial se usa Firebase Cloud Messaging) con una sobrecarga especial de la `onMessageReceived` método (la notificación de control método).

Debido a posibles optimizaciones, seguridad y cumplimiento de normas, la notificación de Google Cloud Messaging entrante procedentes de las notificaciones de gráfico en el servidor podría ser una derivación de hombros, que no contiene ningún dato que se publica inicialmente por el servidor de aplicaciones. La recuperación de la notificación real contenida publicada por el servidor de aplicaciones está oculta detrás de la API del SDK de cliente. Por este motivo, el SDK puede proporcionar un modelo de programación coherente en el que el cliente de aplicación siempre pasa la carga entrante de Google Cloud Messaging al SDK. Esto permite que el SDK determinar si se trata de una notificación para escenarios de la plataforma de dispositivo conectado o no (en caso de Android native Google Cloud Messaging canal se utiliza el cliente de aplicación para otros fines) y qué entrantes en este escenario/capacidad notificación se corresponde con (notificaciones de Graph, actividad del usuario, etcetera.). A continuación, se puede ejecutar lógica específica en otro tipo de escenarios de control por el cliente de aplicación después de eso. 

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

La aplicación ahora puede controlar las notificaciones de la plataforma de dispositivos conectados.

