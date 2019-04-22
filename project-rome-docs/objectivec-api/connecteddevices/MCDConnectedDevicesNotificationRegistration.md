---
title: MCDConnectedDevicesNotificationRegistration
description: Esta clase representa el registro de la aplicación con un servicio de notificaciones de inserción (necesario para algunos escenarios de proyecto Roma).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801437"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a>Clase `MCDConnectedDevicesNotificationRegistration` 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 Esta clase representa el registro de la aplicación con un servicio de notificaciones de inserción (necesario para algunos escenarios de proyecto Roma). Transmite esa información a la plataforma de dispositivos conectados.

## <a name="properties"></a>Propiedades

### <a name="type"></a>Tipo
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

El tipo de notificaciones en esta configuración.

### <a name="token"></a>símbolo (token)
`@property(nonatomic, readwrite, nonnull) NSString* token;`

El token de registro.

### <a name="appid"></a>appId
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

El identificador de aplicación para el registro de notificaciones push.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

Nombre para mostrar la aplicación. Esto debe ser el nombre de la aplicación que se usó para el registro en el portal de desarrollo de Microsoft.