---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909297"
---
### <a name="register-your-app-for-push-notifications"></a>Registrar la aplicación para notificaciones de inserción

Registrar la aplicación con Apple para [notificaciones Push de Apple](https://developer.apple.com/notifications/) admite. Asegúrese de anotar el remitente clave de servidor y el identificador que recibe ya que será necesario más adelante.

Una vez registrado, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a>Registrar la aplicación en Microsoft Windows Dev Center para experiencias multidispositivo

> [!WARNING]
> Este paso sólo es necesario si desea usar características de proyecto Roma para tener acceso a datos desde o realizar solicitudes de dispositivos que no sean Windows. Si solo tiene como destino dispositivos Windows, no es necesario completar este paso.

Registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web). Se trata de un procedimiento diferente MSA y AAD del registro de aplicación anterior. El objetivo principal de este proceso consiste en asignar las identidades de aplicación específico de plataforma con una identidad de aplicación multiplataforma que es reconocido por la plataforma de dispositivos conectados. Este paso también permitirá el envío de notificaciones mediante los servicios de notificación de inserción nativa correspondiente a las plataformas móviles que usa la aplicación. Para iOS, habilita las notificaciones se envíen a los extremos de la aplicación iOS mediante Apple Push Notification Service: Apple Push Notification Service.

Ir al panel del centro de desarrollo, vaya a experiencias multidispositivo desde el panel de navegación del lado izquierdo y seleccione Configurar una nueva aplicación de dispositivo cruzado.
![Panel del centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)

El proceso de incorporación de centro de desarrollo requieren los siguientes pasos:

* Seleccione las plataformas admitidas: seleccione las plataformas donde la aplicación tendrá una presencia y habilitarse para experiencias multidispositivo. En el caso de integración de las notificaciones de gráfico, puede seleccionar desde Windows, Android o iOS, dependiendo de qué plataformas está utilizando. ![Plataformas compatibles con experiencias multidispositivo:](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* Proporcionar los identificadores de aplicación: proporcione los identificadores de aplicación para cada plataforma que utilice. Para las aplicaciones de iOS, esto es el nombre de paquete asignada a la aplicación cuando creó el proyecto. Tenga en cuenta que puede agregar distintos identificadores (hasta diez) por plataforma, que es en caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, lo que quiere que sea capaz de recibir las mismas notificaciones enviadas por el servidor de aplicaciones de destino en el mismo usuario. ![Experiencias multidispositivo: identificadores de aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* Proporcionar o seleccione los identificadores de aplicación en registros de aplicaciones MSA o AAD obtenidos en los anteriores pasos de registro de aplicación AAD/MSA anteriores. ![Experiencias multidispositivo – MSA y registros de aplicaciones AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* Proporcione sus credenciales para las plataformas de notificación nativa relevantes para la aplicación (es decir, WNS para Windows, FCM para Android o APNS para iOS) para permitir la entrega de notificaciones desde el servidor de aplicaciones al publicar las notificaciones de usuario de destino. ![Experiencias multidispositivo: credenciales de inserción](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* Por último, compruebe el dominio de aplicación entre dispositivos para asegurarse de que la aplicación tiene la propiedad del dominio y puede utilizarlo como una identidad de dispositivo cruzado de la aplicación. ![Experiencias multidispositivo: comprobación de dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
