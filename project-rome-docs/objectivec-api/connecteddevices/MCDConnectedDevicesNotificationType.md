---
title: MCDConnectedDevicesNotificationType
description: Obtenga información sobre la enumeración MCDConnectedDevicesNotificationType. Esta enumeración contiene valores que describen el tipo (servicio) de una notificación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 5daf6db553df72a14a2cf201b4e974083eb7cf80
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761099"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a>enumeración `MCDConnectedDevicesNotificationType`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
Contiene valores que describen el tipo (servicio) de una notificación.

## <a name="fields"></a>Campos

| NOMBRE                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDNotificationTypeUnknown | 0 | ConnectedDevicesNotificationType es desconocido. |
| MCDNotificationTypeWNS | 1 | Notification Services de Windows Inserte. |
| MCDNotificationTypeGCM | 2 | Google Cloud Messaging. |
| MCDNotificationTypeFCM | 3 | Mensajería en la nube Firebase.|
| MCDNotificationTypeAPN | 4 | Apple Push Notification Service. |
| MCDNotificationTypePolling | 5 | No hay servicio de notificaciones en la nube; en su lugar, sondee las respuestas entrantes. |
