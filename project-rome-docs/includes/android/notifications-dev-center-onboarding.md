---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907307"
---
### <a name="register-your-app-for-push-notifications"></a>Registrar la aplicación para notificaciones de inserción

Registrar la aplicación con Google para [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) admite. No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante.

Una vez registrado, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registrar la aplicación en Microsoft Windows Dev Center para experiencias multidispositivo

> [!IMPORTANT]
> Este paso sólo es necesario si desea usar características de proyecto Roma para tener acceso a datos desde o realizar solicitudes de dispositivos que no sean Windows. Si solo tiene como destino dispositivos Windows, no es necesario completar este paso.

Ir al panel del centro de desarrollo, vaya a experiencias multidispositivo desde el panel de navegación del lado izquierdo y seleccione Configurar una nueva aplicación entre dispositivos, que se muestra a continuación.
![Panel del centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación de centro de desarrollo requiere los siguientes pasos:
* Seleccione las plataformas admitidas: seleccione las plataformas donde la aplicación tendrá una presencia y habilitarse para experiencias multidispositivo. En el caso de integración de las notificaciones de gráfico, puede seleccionar desde Windows, Android o iOS.
![Plataformas compatibles con experiencias multidispositivo:](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Proporcione los identificadores de aplicación: proporcione los identificadores de aplicación para cada uno de la plataforma donde la aplicación tiene una presencia. Las aplicaciones Android, esto es el nombre de paquete asignada a la aplicación cuando creó el proyecto. El nombre del paquete puede encontrarse en la consola de Firebase en información general del proyecto -> General. Puede agregar distintos identificadores (hasta diez) por plataforma, que es en caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, lo que quiere que sea capaz de recibir las mismas notificaciones enviadas por el servidor de aplicaciones de destino en el mismo usuario. 
![Experiencias multidispositivo: identificadores de aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Proporcione o seleccione la aplicación de los identificadores de MSA o AAD registros de aplicaciones. Estos identificadores de cliente correspondientes al registro de aplicación AAD o de MSA se obtuvieron en los pasos de registro de aplicación AAD/MSA anteriores desde arriba. 
![Experiencias multidispositivo – MSA y registros de aplicaciones AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Las notificaciones de Graph y otras capacidades de plataforma de dispositivos conectados aprovechan cada una de las plataformas de notificación nativa en las plataformas principales para enviar notificaciones a la aplicación de extremos de cliente, es decir, WNS (para Windows UWP), FCM (para Android) y Apple Push Notification Service (para iOS) . Proporcione sus credenciales para estas plataformas de notificación habilitar las notificaciones de Graph entregar las notificaciones para el servidor de aplicaciones, al publicar las notificaciones de usuario de destino. Para Android, [habilitar el servicio de mensajería de nube](https://firebase.google.com/docs/cloud-messaging/android/client) es un requisito previo para usar notificaciones de Microsoft Graph. Además, tenga en cuenta que el identificador de remitente requerido se corresponde con el identificador del remitente Firebase Cloud Messaging y la clave de API que se corresponde con la clave del servidor heredado. Ambos pueden encontrarse en la consola de Firebase -> proyecto -> configuración, en la pestaña de mensajería en la nube, como se muestra en la captura de pantalla.
![Experiencias multidispositivo: credenciales de inserción](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* El último paso es comprobar el dominio de aplicación entre dispositivos, que actúa como un proceso de comprobación para demostrar que la aplicación tiene que actúa como una identidad de aplicación entre dispositivos de la aplicación que registró la propiedad de este dominio.
![Experiencias multidispositivo: comprobación de dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
