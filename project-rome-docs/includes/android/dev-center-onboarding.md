---
title: include file
description: include file
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907927"
---
## <a name="preliminary-setup-for-push-notifications"></a>Configuración preliminar para las notificaciones push

### <a name="register-your-app-for-push-notifications"></a>Registro de la aplicación para notificaciones push

Registra la aplicación con Google para la compatibilidad con [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client). No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante. 

Una vez efectuado el registro, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados de tu aplicación.

```Java
notificationRegistration = new ConnectedDevicesNotificationRegistration();
notificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
notificationRegistration.setToken(token);
notificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
notificationRegistration.setAppDisplayName("SampleApp");

mConnectedDevicesPlatform.getNotificationRegistrationManager().registerForAccountAsync(mConnectedDevicesAccount).whenComplete(() -> {
  // Now that notifications are registered, this account can receive replies to commands and incoming commands.
});
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registro de la aplicación en el Centro de desarrollo de Microsoft Windows para experiencias multidispositivo
Si necesitas comunicación con el dispositivo Android, debes registrar la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se sigue un procedimiento diferente al registro de la aplicación con MSA y AAD anterior.  El objetivo principal de este proceso consiste en asignar las identidades de la aplicación específicas de la plataforma a una identidad de aplicación multiplataforma que se reconozca en la plataforma de dispositivos conectados y, al mismo tiempo, autorizar a la plataforma a enviar notificaciones con los servicios de notificación push nativos correspondiente a cada plataforma móvil. En este caso, permite la comunicación a los puntos de conexión de la aplicación iOS mediante Firebase Cloud Messaging.

Ve al Panel del Centro de desarrollo y allí, a Cross-Device Experiences (Experiencias multidispositivo) en el panel de navegación del lado izquierdo; selecciona la opción de configuración de una nueva aplicación multidispositivo, tal como se muestra a continuación.
![Panel del Centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación del Centro de desarrollo requiere los siguientes pasos:
* Select supported platforms (Seleccionar plataformas compatibles): selecciona las plataformas donde la aplicación estará presente y habilitada para experiencias multidispositivo. Puedes seleccionar Windows, Android o iOS.
![Experiencias multidispositivo: plataformas compatibles](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Provide app IDs (Proporcionar id. de la aplicación): proporciona los id. de la aplicación para cada una de las plataformas donde la aplicación estará presente. 
![Experiencias multidispositivo: id. de la aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Puedes agregar varios id. (hasta diez) por plataforma; esto se aplica en el caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, que quieres que reciban las mismas notificaciones enviadas por el servidor de aplicaciones destinadas al mismo usuario. 
> [!TIP] 
> En las aplicaciones Android, es el nombre del paquete que asignaste a la aplicación al crear el proyecto. Puedes encontrar el nombre del paquete en la consola de Firebase, en Project Overview (Información general del proyecto) -> General.
![Consola de Firebase: información general del proyecto](../../notifications/media/dev_center_portal/firebase_overview.png)

* Proporciona o selecciona los id. de la aplicación de los registros de la aplicación con MSA o AAD. Estas identificaciones de cliente correspondientes al registro de la aplicación con AAD o MSA se obtuvieron en los pasos de registro de la aplicación con MSA o AAD anteriores, indicados más arriba. 
![Experiencias multidispositivo: registros de la aplicación con MSA y AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Las funcionalidades de la plataforma de dispositivos conectados aprovechan cada una de las plataformas de notificación nativas de las principales plataformas para enviar notificaciones hasta los puntos de conexión cliente de la aplicación, es decir, WNS (para Windows UWP), GCM (para Android) y APNS (para iOS). Proporciona tus credenciales para estas plataformas de notificación para permitir que la plataforma entregue las notificaciones para el servidor de aplicaciones al publicar notificaciones destinadas al usuario.
![Experiencias multidispositivo: credenciales de notificaciones push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> En el caso de Android, habilitar Cloud Messaging es un requisito previo para comunicarse con un dispositivo Android. Consulta [Configura una app cliente de Firebase Cloud Messaging en Android](https://firebase.google.com/docs/cloud-messaging/android/client) para ver más detalles. Cuando hayas completado la incorporación, puedes proporcionar las credenciales de notificaciones push para la plataforma de dispositivos conectados a través del Centro de desarrollo de Windows. 
> [!TIP] 
> El id. del remitente requerido se corresponde con el valor de Sender ID (id. del remitente) de Firebase Cloud Messaging y la clave de API se corresponde con el valor de Legacy Server Key (Clave del servidor heredado). Ambos pueden encontrarse en la consola de Firebase -> Project (Proyecto) -> Settings (Configuración), en la pestaña Cloud Messaging (Mensajería en la nube), tal como se muestra en la captura de pantalla.
![Consola de Firebase: credenciales de notificaciones push de Android](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* El último paso consiste en comprobar el dominio de la aplicación multidispositivo; sirve como proceso de verificación para confirmar que la aplicación tiene la propiedad de este dominio, que actúa como identidad de aplicación multidispositivo para la aplicación que registraste.
![Experiencias multidispositivo: verificación del dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Proceso de notificaciones a medida que se reciben en la aplicación

Después de validar la experiencia multidispositivo en el Centro de desarrollo de Microsoft Windows, asegúrate de que la aplicación puede procesar las notificaciones a medida que llegan. 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
