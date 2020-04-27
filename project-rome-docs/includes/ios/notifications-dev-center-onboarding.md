---
title: include file
description: include file
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909297"
---
### <a name="register-your-app-for-push-notifications"></a>Registro de la aplicación para notificaciones push

Registra la aplicación con Apple para conseguir la compatibilidad con [Apple Push Notification](https://developer.apple.com/notifications/). No olvides anotar el id. del remitente y la clave de servidor que recibas, ya que los necesitarás más adelante.

Una vez efectuado el registro, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados de tu aplicación.

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registro de la aplicación en el Centro de desarrollo de Microsoft Windows para experiencias multidispositivo

> [!WARNING]
> Este paso solo es necesario si deseas usar características de Project Rome para acceder a datos de dispositivos que no sean Windows o realizar solicitudes en ellos. Si solo vas a trabajar con dispositivos Windows, no es necesario que realices este paso.

Registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se sigue un procedimiento diferente al registro de la aplicación con MSA y AAD anterior. El objetivo principal de este proceso consiste en asignar las identidades de la aplicación específicas de la plataforma a una identidad de aplicación multiplataforma que se reconozca en la plataforma de dispositivos conectados. Este paso también permitirá enviar notificaciones mediante los servicios de notificación push nativos correspondientes a las plataformas móviles que utilice la aplicación. En iOS, permite que las notificaciones se envíen a los puntos de conexión de la aplicación iOS mediante APNS (Apple Push Notification Service).

Ve al Panel del Centro de desarrollo y allí, a Cross-Device Experiences (Experiencias multidispositivo) en el panel de navegación del lado izquierdo; selecciona la opción de configuración de una nueva aplicación multidispositivo.
![Panel del Centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación del Centro de desarrollo requiere los siguientes pasos:

* Select supported platforms (Seleccionar plataformas compatibles): selecciona las plataformas donde la aplicación estará presente y habilitada para experiencias multidispositivo. En el caso de la integración con las notificaciones de Graph, puedes seleccionar Windows, Android o iOS, en función de las plataformas que utilices. ![Experiencias multidispositivo: plataformas compatibles](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Proporciona los id. de la aplicación: proporciona los id. de la aplicación para cada plataforma que utilices. En las aplicaciones iOS, es el nombre del paquete que asignaste a la aplicación al crear el proyecto. Ten en cuenta que puedes agregar varios id. (hasta diez) por plataforma; esto se aplica en el caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, que quieres que reciban las mismas notificaciones enviadas por el servidor de aplicaciones destinadas al mismo usuario. ![Experiencias multidispositivo: id. de la aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Proporciona o selecciona los id. de la aplicación de los registros de la aplicación con MSA o AAD obtenidos en los pasos de registro de la aplicación con AAD/MSA anteriores. ![Experiencias multidispositivo: registros de la aplicación con MSA y AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Indica tus credenciales para las plataformas de notificación nativas relevantes para la aplicación (es decir, WNS para Windows, FCM para Android o APNS para iOS), para permitir la entrega de notificaciones desde el servidor de aplicaciones al publicar notificaciones destinadas al usuario. ![Experiencias multidispositivo: credenciales de notificaciones push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* Por último, comprueba el dominio de la aplicación multidispositivo para asegurarte de que la aplicación tiene la propiedad del dominio y puede utilizarlo como una identidad multidispositivo para la aplicación. ![Experiencias multidispositivo: verificación del dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
