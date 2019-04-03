---
title: MCDUserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907987"
---
# <a name="class-mcdusernotificationreaderoptions"></a>Clase `MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente. 

## <a name="properties"></a>Propiedades

### <a name="startposition"></a>startPosition
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.

### <a name="statusfilter"></a>statusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Obtiene o establece el filtro de estado para este lector de notificación de usuario que desee crear.

### <a name="readstatefilter"></a>readStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` El filtro de estado de acción de usuario que se establece para esta instancia de UserNotificationReaderOptions Getor Set.

## <a name="constructors"></a>Constructores

### <a name="options"></a>opciones
`+ (nullable instancetype)options;` Crea e inicializa una nueva instancia de las opciones de notificaciones de usuario.