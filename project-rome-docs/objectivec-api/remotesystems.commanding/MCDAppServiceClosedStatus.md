---
title: MCDAppServiceClosedStatus
description: Contiene valores que describen una conexión cerrada a un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800777"
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