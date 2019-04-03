---
title: MCDAppServiceClosedStatus
description: Contiene valores que describen una conexión cerrada a un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907727"
---
# <a name="enum-mcdappserviceclosedstatus"></a>Enum `MCDAppServiceClosedStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

Contiene valores que describen una conexión cerrada a un servicio de aplicación remota.

|Miembro   |Valor   |Descripción   |
|--------|-------|-------------|
|MCDAppServiceClosedStatusCompleted |0| El punto de conexión para el servicio de aplicación se cierra correctamente.|
|MCDAppServiceClosedStatusCanceled |1| El punto de conexión para el servicio de aplicación fue cerrada por el cliente o el sistema.|
|MCDAppServiceClosedStatusResourceLimitsExceeded |2| El punto de conexión para el servicio de aplicación se ha cerrado porque el punto de conexión se quedó sin recursos.|
|MCDAppServiceClosedStatusUnknown |3| Se produjo un error desconocido.|