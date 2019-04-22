---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: d8e94884c742015b08d87e83a9384cbb577695c4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907927"
---
## <a name="preliminary-setup-for-push-notifications"></a>Instalación preliminar para las notificaciones de inserción

### <a name="register-your-app-for-push-notifications"></a>Registrar la aplicación para notificaciones de inserción

Registrar la aplicación con Google para [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) admite. No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante. 

Una vez registrado, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registrar la aplicación en Microsoft Windows Dev Center para experiencias multidispositivo
Si necesita comunicación al dispositivo Android, deberá registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se trata de un procedimiento diferente MSA y AAD del registro de aplicación anterior.  El objetivo principal de este proceso consiste en asignar las identidades de aplicación específico de plataforma con una identidad de aplicación multiplataforma que es reconocido por la plataforma de dispositivos conectados y, al mismo tiempo se autoriza la plataforma para enviar notificaciones mediante la notificación de inserción nativa servicios correspondientes a cada plataforma móvil. En este caso, se permite a los extremos de aplicación de iOS a través de Firebase Cloud Messaging permite la comunicación.

Ir al panel del centro de desarrollo, vaya a experiencias multidispositivo desde el panel de navegación del lado izquierdo y seleccione Configurar una nueva aplicación entre dispositivos, que se muestra a continuación.
![Panel del centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación de centro de desarrollo requiere los siguientes pasos:
* Seleccione las plataformas admitidas: seleccione las plataformas donde la aplicación tendrá una presencia y habilitarse para experiencias multidispositivo. Puede seleccionar desde Windows, Android o iOS.
![Plataformas compatibles con experiencias multidispositivo:](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Proporcione los identificadores de aplicación: proporcione los identificadores de aplicación para cada uno de la plataforma donde la aplicación tiene una presencia. 
![Experiencias multidispositivo: identificadores de aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Puede agregar distintos identificadores (hasta diez) por plataforma, que es en caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, lo que quiere que sea capaz de recibir las mismas notificaciones enviadas por el servidor de aplicaciones de destino en el mismo usuario. 
> [!TIP] 
> Las aplicaciones Android, esto es el nombre de paquete asignada a la aplicación cuando creó el proyecto. El nombre del paquete puede encontrarse en la consola de Firebase en información general del proyecto -> General.
![Consola de firebase: información general del proyecto](../../notifications/media/dev_center_portal/firebase_overview.png)

* Proporcione o seleccione la aplicación de los identificadores de MSA o AAD registros de aplicaciones. Estos identificadores de cliente correspondientes al registro de aplicación AAD o de MSA se obtuvieron en los pasos de registro de aplicación AAD/MSA anteriores desde arriba. 
![Experiencias multidispositivo – MSA y registros de aplicaciones AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Conectar dispositivos plataforma capacidades aprovechar cada de las plataformas de notificación nativa en las plataformas principales para enviar notificaciones hasta que el cliente de aplicación de extremos, es decir, WNS (para Windows UWP), GCM (para Android) y Apple Push Notification Service (para iOS). Proporcione sus credenciales para estas plataformas de notificación para habilitar la plataforma para entregar las notificaciones para el servidor de aplicaciones, al publicar las notificaciones de usuario de destino.
![Experiencias multidispositivo: credenciales de inserción](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> Para Android, habilitar el servicio de mensajería en la nube es un requisito previo para comunicarse con un dispositivo Android. Consulte [establecer seguridad unas Firebase Cloud mensajería aplicación cliente en Android](https://firebase.google.com/docs/cloud-messaging/android/client) para obtener más detalles. Cuando haya completado la incorporación, a continuación, puede proporcionar las credenciales de inserción a través del centro de desarrollo de Windows para la plataforma de dispositivos conectados. 
> [!TIP] 
> El identificador de remitente requerido se corresponde con el identificador de remitente de mensajería en la nube de Firebase y la clave de API se corresponde con la clave del servidor heredado. Ambos pueden encontrarse en la consola de Firebase -> proyecto -> configuración, en la pestaña de mensajería en la nube, como se muestra en la captura de pantalla.
![Consola de firebase: credenciales Push Android](../../notifications/media/dev_center_portal/firebase_push_creds.png)

* El último paso es comprobar el dominio de aplicación entre dispositivos, que actúa como un proceso de comprobación para demostrar que la aplicación tiene que actúa como una identidad de aplicación entre dispositivos de la aplicación que registró la propiedad de este dominio.
![Experiencias multidispositivo: comprobación de dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)

### <a name="process-notifications-as-they-are-received-by-the-app"></a>Procesar las notificaciones que son recibidos por la aplicación

Una vez que se haya validado la experiencia entre dispositivos en Microsoft Windows Dev Center, asegúrese de que la aplicación puede procesar las notificaciones, tal y como vienen. 

```Java
    ensurePlatformInitialized().thenAccept((ConnectedDevicesPlatform platform) -> {
            ConnectedDevicesProcessNotificationOperation operation = platform.processNotification(data);
        });
```
