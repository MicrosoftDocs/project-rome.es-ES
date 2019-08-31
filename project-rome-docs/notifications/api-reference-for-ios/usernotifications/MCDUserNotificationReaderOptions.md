---
title: MCDUserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907987"
---
# <a name="class-mcdusernotificationreaderoptions"></a>las`MCDUserNotificationReaderOptions`

```
@interface MCDUserNotificationReaderOptions : NSObject
```

Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes. 

## <a name="properties"></a>Propiedades

### <a name="startposition"></a>startPosition
`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.

### <a name="statusfilter"></a>statusFilter
`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`Obtenga o establezca el filtro de estado para este lector de notificaciones de usuario que desea crear.

### <a name="readstatefilter"></a>readStateFilter
`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions

### <a name="useractionstatefilter"></a>userActionStateFilter
`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`Getor establezca el filtro de estado de acción del usuario que se establece para esta instancia de UserNotificationReaderOptions.

## <a name="constructors"></a>Constructores

### <a name="options"></a>opciones
`+ (nullable instancetype)options;`Crea e inicializa una nueva instancia de opciones para las notificaciones de usuario.