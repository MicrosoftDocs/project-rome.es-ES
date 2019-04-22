---
title: MCDUserNotificationUserActionStateFilter
description: Contiene valores que clasifican las notificaciones de estado de acción del usuario (para la recuperación de notificación filtrada).
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800567"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a>Enum `MCDUserNotificationUserActionStateFilter`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

Contiene valores que clasifican las notificaciones de estado de acción del usuario (para la recuperación de notificación filtrada).

|Nombre | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateFilterAny|0| Incluir notificaciones independientemente del estado de acción del usuario.|
|   MCDUserNotificationUserActionStateFilterNoInteraction |1| Incluyen las notificaciones que no se ha actuado por el usuario.|
|   MCDUserNotificationUserActionStateFilterActivated|2| Incluyen las notificaciones que se han activado por el usuario.|
|   MCDUserNotificationUserActionStateFilterDismissed|3| Incluyen las notificaciones que se han descartado por el usuario.|
|   MCDUserNotificationUserActionStateFilterSnoozed|4| Incluyen las notificaciones que se han pospuesto por el usuario.|