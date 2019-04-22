---
title: MCDConnectedDevicesNotificationType
description: Contiene valores que describen el tipo (servicio) de una notificación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801697"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>Enum `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
Contiene valores que describen el tipo (servicio) de una notificación.

## <a name="fields"></a>Campos

| Nombre                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType es desconocido. |
| MCDNotificationTypeWNS | 1 | Servicios de notificación de inserción de Windows. |
| MCDNotificationTypeGCM | 2 | Google Cloud Messaging. |
| MCDNotificationTypeFCM | 3 | Firebase Cloud Messaging.|
| MCDNotificationTypeAPN | 4 | Servicio de notificaciones Push de Apple. |
| MCDNotificationTypePolling | 5 | Ningún servicio de notificación en la nube; en su lugar un sondeo para las respuestas entrantes. |
