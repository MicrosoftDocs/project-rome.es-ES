---
title: MCDUserNotificationUserActionState
description: Contiene valores que describen la acción de que un usuario ha realizado en una notificación.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 2baebeff7ccd43c7a5259c178434162908ee84c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907787"
---
# <a name="enum-mcdusernotificationuseractionstate"></a>Enum `MCDUserNotificationUserActionState`

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

Contiene valores que describen la acción de que un usuario ha realizado en una notificación.

|Nombre | Valor | Descripción |
|:-- |:-- |:-- |
|   MCDUserNotificationUserActionStateNoInteraction |0| El usuario no ha tomado ninguna acción.|
|   MCDUserNotificationUserActionStateActivated|1|El usuario ha activado la notificación.|
|   MCDUserNotificationUserActionStateDismissed|2| El usuario ha descartado la notificación.|
|   MCDUserNotificationUserActionStateSnoozed|3| El usuario ha posponer la notificación.|
