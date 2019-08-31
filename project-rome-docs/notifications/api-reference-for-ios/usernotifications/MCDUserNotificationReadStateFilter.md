---
title: MCDUserNotificationReadStateFilter
description: Contiene valores que clasifican las notificaciones por estado de lectura (para la recuperación de notificaciones filtradas).
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801347"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a>enumeración`MCDUserNotificationReadStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

Contiene valores que clasifican las notificaciones por estado de lectura (para la recuperación de notificaciones filtradas).

|NOMBRE | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationReadStateFilterAny | 0 | Incluye notificaciones independientemente del estado de lectura.|
|   MCDUserNotificationReadStateFilterUnread | 1 | Incluye notificaciones que no se han leído.|
|   MCDUserNotificationReadStateFilterRead | 2 | Incluye las notificaciones que se han leído. |