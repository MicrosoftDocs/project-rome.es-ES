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
## <a name="preliminary-setup-for-push-notifications"></a>Configuración preliminar para las notificaciones push

### <a name="register-your-app-for-push-notifications"></a>Registro de la aplicación para notificaciones push

Registra la aplicación con Google para la compatibilidad con las notificaciones. No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante. 

### <a name="register-your-app-for-cross-device-connected-devices-platform-access"></a>Registro de la aplicación para acceder a la plataforma de dispositivos conectados multidispositivo

A continuación, registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se sigue un procedimiento diferente al registro en el Centro de desarrollo de Windows, que se explicó en los pasos anteriores. Autoriza a la plataforma de dispositivos conectados a enviar notificaciones mediante el servicio de notificaciones push nativo. El proceso de incorporación del Centro de desarrollo necesitará:
* El id. de cliente de la aplicación
* La clave de Google Cloud Messaging Esto es necesario para entregar datos y comandos a la aplicación (en un dispositivo que puede ser bloqueado o inactivo) en forma de notificaciones push. 

### <a name="configure-your-app-to-be-notification-compatible"></a>Configuración de la aplicación para la compatibilidad con las notificaciones

Después de completar el flujo de trabajo en el panel del desarrollador, debes modificar el código real de la aplicación para que pueda recibir notificaciones push. Consulta [Configura una app cliente de Firebase Cloud Messaging en Android](https://firebase.google.com/docs/cloud-messaging/android/client) si no sabes cómo hacerlo.

### <a name="associate-the-notification-service-with-the-local-platform"></a>Asociación del servicio de notificación con la plataforma local

Por último, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados en la aplicación. En los pasos anteriores, inicializaste la plataforma con un parámetro *notificationProvider* `null`. Ahora debes construir y pasar un objeto que implemente **[NotificationProvider](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_provider)** . Lo más importante que debes tener en cuenta es el método `getNotificationRegistrationAsync`, que debe devolver una instancia de **[NotificationRegistration](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._notification_registration)** . **NotificationRegistration** es responsable de proporcionar a la plataforma de dispositivos conectados un token de acceso (y la información relacionada) para el servicio de notificación.


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

Incluye este registro en la implementación de **NotificationProvider**. A continuación, la llamada de inicialización de **Platform** debe proporcionar a la instancia de **Platform** local acceso al servicio de notificaciones push, permitiendo así que la aplicación reciba datos de la plataforma de dispositivos conectados del servidor, que transmite solicitudes de inicio y mensajes del servicio de aplicación de otros dispositivos. 

Ahora todo lo que necesitas hacer es ampliar la clase del servicio del cliente de escucha nativo ([FirebaseMessagingService](https://firebase.google.com/docs/reference/android/com/google/firebase/messaging/FirebaseMessagingService) en este caso, dado que esta guía utiliza Firebase Cloud Messaging) con una sobrecarga especial del método `onMessageReceived` (el método de administración de notificaciones).

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

La aplicación ya puede controlar las notificaciones de la plataforma de dispositivos conectados.
