---
ms.openlocfilehash: 325f0d041408b301c61648bd5c030ae0c7c4f59c
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "76118120"
---
### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registro de la aplicación en el Centro de desarrollo de Microsoft Windows para experiencias multidispositivo
A continuación, debes registrar la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se sigue un procedimiento diferente al registro de la aplicación con MSA y AAD, que se explicó en los pasos anteriores. El objetivo principal de este proceso consiste en asignar las identidades de la aplicación específicas de la plataforma a una identidad de aplicación multiplataforma que se reconozca en la plataforma de dispositivos conectados y, al mismo tiempo, autorizar a la característica Notificaciones de Microsoft Graph para que envíe notificaciones con los servicios de notificación push nativos correspondiente a cada plataforma de sistema operativo. En este caso, permite que la característica Notificaciones de Graph envíe notificaciones a los puntos de conexión de la aplicación para UWP de Windows a través de WNS (Servicio de notificaciones de Windows). Ve al Panel del Centro de desarrollo y allí, a Cross-Device Experiences (Experiencias multidispositivo) en el panel de navegación del lado izquierdo; selecciona la opción de configuración de una nueva aplicación multidispositivo, tal como se muestra a continuación.
![Panel del Centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación del Centro de desarrollo requiere los siguientes pasos:
* Select supported platforms (Seleccionar plataformas compatibles): selecciona las plataformas donde la aplicación estará presente y habilitada para experiencias multidispositivo. En el caso de la integración con las notificaciones de Graph, puedes seleccionar Windows, Android o iOS. Se muestra a continuación.
![Experiencias multidispositivo: plataformas compatibles](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Provide app IDs (Proporcionar id. de la aplicación): proporciona los id. de la aplicación para cada una de las plataformas donde la aplicación estará presente. Se muestra a continuación.
![Experiencias multidispositivo: id. de la aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)
> [!NOTE]
> Puedes agregar varios id. (hasta diez) por plataforma; esto se aplica en el caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, que quieres que reciban las mismas notificaciones enviadas por el servidor de aplicaciones destinadas al mismo usuario. 

* Proporciona o selecciona los id. de la aplicación de los registros de la aplicación con MSA o AAD. Estas identificaciones de cliente correspondientes al registro de la aplicación con AAD o MSA se obtuvieron en los pasos de registro de la aplicación con MSA o AAD anteriores, indicados más arriba. Se muestra a continuación. 
![Experiencias multidispositivo: registros de la aplicación con MSA y AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)
* Las notificaciones de Graph y otras funcionalidades de la plataforma de dispositivos conectados aprovechan cada una de las plataformas de notificación nativas de las principales plataformas para enviar notificaciones hasta los puntos de conexión cliente de la aplicación, es decir, WNS (para Windows UWP), GCM (para Android) y APNS (para iOS). Proporciona tus credenciales para estas plataformas de notificación para permitir que Notificaciones de Graph entregue las notificaciones para el servidor de aplicaciones al publicar notificaciones destinadas al usuario. Se muestra a continuación. 
![Experiencias multidispositivo: credenciales de notificaciones push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)
> [!NOTE] 
> En las aplicaciones para UWP de Windows, la habilitación de la notificación push de WNS es un requisito necesario para usar la característica Notificaciones de Microsoft Graph. Consulta [Introducción a los Servicios de notificaciones de inserción de Windows (WNS)](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/windows-push-notification-services--wns--overview) para obtener más información. Cuando hayas completado la incorporación, puedes proporcionar las credenciales de notificaciones push para la plataforma de dispositivos conectados a través del Centro de desarrollo de Windows. 
* El último paso consiste en comprobar el dominio de la aplicación multidispositivo; sirve como proceso de verificación para confirmar que la aplicación tiene la propiedad de este dominio, que actúa como identidad de aplicación multidispositivo para la aplicación que registraste. Se muestra a continuación.  
![Experiencias multidispositivo: verificación del dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png) Ya has terminado con la incorporación. Continúa en la sección siguiente. 


