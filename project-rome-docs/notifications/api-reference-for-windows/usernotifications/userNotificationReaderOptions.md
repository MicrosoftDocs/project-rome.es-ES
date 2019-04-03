---
title: UserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.
keywords: Microsoft, windows, las notificaciones de Graph, Windows procedimientos
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909687"
---
# <a name="class-usernotificationreaderoptions"></a>Clase `UserNotificationReaderOptions`

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente. 

## <a name="constructors"></a>Constructores

### <a name="usernotificationreaderoptions"></a>UserNotificationReaderOptions
Crea e inicializa una nueva instancia de UserNotificationReaderOptions.

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a>UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)
Crea e inicializa una nueva instancia de UserNotificationReaderOptions con filtros y la posición de inicio especificada. 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a>Propiedades

|Nombre | Descripción |
|:-- |:-- |
|StartPosition |Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.|
|   StatusFilter |Obtiene o establece el filtro de estado para este lector de notificación de usuario que desee crear.| 
|   ReadStateFilter |Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions.| 
|   UserActionStateFilter|El filtro de estado de acción de usuario que se establece para esta instancia de UserNotificationReaderOptions Getor Set.| 




