---
title: MCDUserNotificationStatusFilter
description: Contiene valores que indican un filtro de estado de lectura al crear un lector de notificaciones. Esto determina si la aplicación desea recibir todas las notificaciones, solo las leídas o solo las no leídas.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801497"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>enumeración`MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

Contiene valores que indican un filtro de estado de lectura al crear un lector de notificaciones. Esto determina si la aplicación desea recibir todas las notificaciones, solo las leídas o solo las no leídas. 

|NOMBRE | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| Incluya todas las notificaciones independientemente del valor de estado. |
|   MCDUserNotificationStatusFilterActive |1| Incluye notificaciones que están activas y guardadas en el almacén de notificaciones de la plataforma de dispositivos conectados. |
|   MCDUserNotificationStatusFilterDeleted | 2| Incluir solo las notificaciones eliminadas.|