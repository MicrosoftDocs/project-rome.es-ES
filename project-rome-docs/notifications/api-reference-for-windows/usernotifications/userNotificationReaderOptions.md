---
title: UserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes.
keywords: Microsoft, Windows, notificaciones de grafos, ventanas de procedimientos
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801387"
---
# <a name="class-usernotificationreaderoptions"></a>las`UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes. 

## <a name="constructors"></a>Constructores

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
Crea e inicializa una nueva instancia de UserNotificationReaderOptions.

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)
Crea e inicializa una nueva instancia de UserNotificationReaderOptions con los filtros y la posición inicial especificada. 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>Propiedades

|NOMBRE | Descripción |
|:-- |:-- |
|StartPosition |Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.|
|   StatusFilter |Obtenga o establezca el filtro de estado para este lector de notificaciones de usuario que desea crear.| 
|   ReadStateFilter |Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions.| 
|   UserActionStateFilter|Getor establezca el filtro de estado de acción del usuario que se establece para esta instancia de UserNotificationReaderOptions.| 




