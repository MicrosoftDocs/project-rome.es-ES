---
title: MCDUserNotificationUserActionStateFilter
description: Contiene valores que clasifican las notificaciones por estado de acción del usuario (para la recuperación de notificaciones filtradas).
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800567"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>enumeración`MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

Contiene valores que clasifican las notificaciones por estado de acción del usuario (para la recuperación de notificaciones filtradas).

|NOMBRE | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| Incluye notificaciones independientemente del estado de acción del usuario.|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| Incluye notificaciones en las que el usuario no ha actuado.|
|   MCDUserNotificationUserActionStateFilterActivated|2| Incluye notificaciones activadas por el usuario.|
|   MCDUserNotificationUserActionStateFilterDismissed|3| Incluye notificaciones que el usuario ha descartado.|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| Incluye notificaciones que el usuario ha pospuesto.|