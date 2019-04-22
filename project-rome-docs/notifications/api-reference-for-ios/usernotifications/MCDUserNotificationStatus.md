---
title: MCDUserNotificationStatus
description: Contiene valores que determina si la notificación se ha eliminado o no. Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma. Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800817"
---
# <a name="enum-mcdusernotificationstatus"></a>Enum `MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

Contiene valores que determina si la notificación se ha eliminado o no. Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma. Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación. 

|Nombre | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| La notificación es sigue activo y persistente dentro de la tienda de la plataforma de dispositivos conectados. |
|   MCDUserNotificationStatusDeleted | 1| Se ha eliminado la notificación.|