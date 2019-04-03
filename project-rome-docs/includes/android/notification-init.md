---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: fcbcfd8f-6eea-421a-97bb-31ea3c987728
ms.localizationpriority: medium
ms.openlocfilehash: 57115d59657d91200d969e2bb05154c3d2499dc7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909457"
---
## <a name="preliminary-setup-for-push-notifications"></a>Instalación preliminar para las notificaciones de inserción

### <a name="register-your-app-for-push-notifications"></a>Registrar la aplicación para notificaciones de inserción

Registrar la aplicación con Google para la compatibilidad con las notificaciones. No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante. 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>Registrar la aplicación obtener acceso a la plataforma de dispositivos conectados entre dispositivos

A continuación, registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se trata de un procedimiento diferente al registrar en el centro de desarrollo de Windows, que se tratan en los pasos preliminares anteriores. Se autoriza a la plataforma de dispositivos conectados para enviar notificaciones mediante el servicio de notificaciones de inserción nativa. Se requerirá el proceso de incorporación de centro de desarrollo:
* Identificador de cliente. la aplicación
* The Google Cloud Messaging key. Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueados o inactivos) en forma de notificaciones de inserción. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configuración de la aplicación para que sea compatible con notificaciones

Después de completar el flujo de trabajo en el panel del desarrollador, debe modificar el código real de la aplicación para que sea capaz de recibir notificaciones de inserción. Consulte [establecer seguridad unas Firebase Cloud mensajería aplicación cliente en Android](https://firebase.google.com/docs/cloud-messaging/android/client) si no está seguro de cómo hacerlo.

### <a name="associate-the-notification-service-with-the-local-platform"></a>Asociar el servicio de notificación de la plataforma local

Por último, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación. En los pasos anteriores, se inicializa la plataforma con una `null` *notificationProvider* parámetro. En este caso, deberá construir y pasar un objeto que implementa  **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)**. Es lo más importante a tener en cuenta la `getNotificationRegistrationAsync` método, que debe devolver un **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** instancia. El **NotificationRegistration** es responsable de proporcionar la plataforma de dispositivos conectados con un token de acceso (y la información relacionada) para el servicio de notificación.


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

Entregar este registro en la implementación de **NotificationProvider**. A continuación, la **plataforma** llamada de inicialización debe proporcionar local **plataforma** con el acceso al servicio de notificaciones de inserción, lo que permite la aplicación recibir datos de los dispositivos conectados de lado servidor Plataforma, que retransmite solicitudes de inicio y los mensajes de servicio de aplicación de otros dispositivos. 

Ahora todo lo que necesita hacer es ampliar el agente de escucha nativa clase de servicio ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que esta guía usa Firebase Cloud Messaging) con una sobrecarga de especial la `onMessageReceived` método (el método de control de notificación).

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

La aplicación ahora es capaz de controlar las notificaciones de la plataforma de dispositivos conectados.
