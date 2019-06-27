---
title: include file
description: include file
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907307"
---
### <a name="register-your-app-for-push-notifications"></a>Registro de la aplicación para notificaciones push

Registra la aplicación con Google para la compatibilidad con [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client). No olvides anotar el id. del remitente y la clave de servidor que recibas; los necesitarás más adelante.

Una vez efectuado el registro, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados de tu aplicación.

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registro de la aplicación en el Centro de desarrollo de Microsoft Windows para experiencias multidispositivo

> [!IMPORTANT]
> Este paso solo es necesario si deseas usar características de Project Rome para acceder a datos de dispositivos que no sean Windows o realizar solicitudes en ellos. Si solo vas a trabajar con dispositivos Windows, no es necesario que realices este paso.

Ve al Panel del Centro de desarrollo y allí, a Cross-Device Experiences (Experiencias multidispositivo) en el panel de navegación del lado izquierdo; selecciona la opción de configuración de una nueva aplicación multidispositivo, tal como se muestra a continuación.
![Panel del Centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación del Centro de desarrollo requiere los siguientes pasos:
* Select supported platforms (Seleccionar plataformas compatibles): selecciona las plataformas donde la aplicación estará presente y habilitada para experiencias multidispositivo. En el caso de la integración con las notificaciones de Graph, puedes seleccionar Windows, Android o iOS.
![Experiencias multidispositivo: plataformas compatibles](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Provide app IDs (Proporcionar id. de la aplicación): proporciona los id. de la aplicación para cada una de las plataformas donde la aplicación estará presente. En las aplicaciones Android, es el nombre del paquete que asignaste a la aplicación al crear el proyecto. Puedes encontrar el nombre del paquete en la consola de Firebase, en Project Overview (Información general del proyecto) -> General. Puedes agregar varios id. (hasta diez) por plataforma; esto se aplica en el caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, que quieres que reciban las mismas notificaciones enviadas por el servidor de aplicaciones destinadas al mismo usuario. 
![Experiencias multidispositivo: id. de la aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Proporciona o selecciona los id. de la aplicación de los registros de la aplicación con MSA o AAD. Estas identificaciones de cliente correspondientes al registro de la aplicación con AAD o MSA se obtuvieron en los pasos de registro de la aplicación con MSA o AAD anteriores, indicados más arriba. 
![Experiencias multidispositivo: registros de la aplicación con MSA y AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Las notificaciones de Graph y otras funcionalidades de la plataforma de dispositivos conectados aprovechan cada una de las plataformas de notificación nativas de las principales plataformas para enviar notificaciones hasta los puntos de conexión cliente de la aplicación, es decir, WNS (para Windows UWP), FCM (para Android) y APNS (para iOS). Proporciona tus credenciales para estas plataformas de notificación para permitir que Notificaciones de Graph entregue las notificaciones para el servidor de aplicaciones al publicar notificaciones destinadas al usuario. En Android, debe [habilitarse el servicio Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) para usar Notificaciones de Microsoft Graph. Además, ten en cuenta que el id. del remitente requerido se corresponde con el valor de Sender ID (id. del remitente) de Firebase Cloud Messaging y que la clave de API se corresponde con el valor de Legacy Server Key (Clave del servidor heredado). Ambos pueden encontrarse en la consola de Firebase -> Project (Proyecto) -> Settings (Configuración), en la pestaña Cloud Messaging (Mensajería en la nube), tal como se muestra en la captura de pantalla.
![Experiencias multidispositivo: credenciales de notificaciones push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* El último paso consiste en comprobar el dominio de la aplicación multidispositivo; sirve como proceso de verificación para confirmar que la aplicación tiene la propiedad de este dominio, que actúa como identidad de aplicación multidispositivo para la aplicación que registraste.
![Experiencias multidispositivo: verificación del dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
