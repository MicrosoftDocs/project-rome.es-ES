---
title: MCDUserNotificationStatus
description: Contiene valores que determinan si la notificación se ha eliminado o no. Las notificaciones eliminadas seguirán estando en el almacén de notificaciones y las devolverá el lector antes de que se produzca la limpieza de la plataforma. Se puede aplicar un filtro de lector correspondiente UserNotificationStatusFilter para evitar que estas notificaciones se muestren en el lector de notificaciones.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800817"
---
# <a name="enum-mcdusernotificationstatus"></a>enumeración`MCDUserNotificationStatus`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

Contiene valores que determinan si la notificación se ha eliminado o no. Las notificaciones eliminadas seguirán estando en el almacén de notificaciones y las devolverá el lector antes de que se produzca la limpieza de la plataforma. Se puede aplicar un filtro de lector correspondiente UserNotificationStatusFilter para evitar que estas notificaciones se muestren en el lector de notificaciones. 

|NOMBRE | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationStatusActive |0| La notificación todavía está activa y se conserva dentro del almacén de plataforma de dispositivos conectados. |
|   MCDUserNotificationStatusDeleted | 1| La notificación se ha eliminado.|