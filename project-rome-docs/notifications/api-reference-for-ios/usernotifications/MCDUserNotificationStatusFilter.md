---
title: MCDUserNotificationStatusFilter
description: Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación. Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801497"
---
# <a name="enum-mcdusernotificationstatusfilter"></a>Enum `MCDUserNotificationStatusFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación. Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos. 

|Nombre | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusFilterAny | 0| Incluir todas las notificaciones, independientemente del valor de estado. |
|   MCDUserNotificationStatusFilterActive |1| Incluyen las notificaciones que están activas y persisten en el almacén de notificación de plataforma de dispositivos conectados. |
|   MCDUserNotificationStatusFilterDeleted | 2| Incluir solo las notificaciones eliminadas.|