---
title: MCDUserNotificationUpdateResult
description: Esta clase describe el estado de un intento de actualizar una notificación.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 814d4373c47c8af00d3e003f730db804f48c5fb0
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801487"
---
# <a name="class-mcdusernotificationupdateresult"></a>las`MCDUserNotificationUpdateResult`

```
@interface MCDUserNotificationUpdateResult : NSObject
```

Esta clase describe el estado de un intento de actualizar una notificación.

## <a name="properties"></a>Propiedades

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

IDENTIFICADOR de la notificación.

### <a name="succeeded"></a>completa
`@property(nonatomic, readonly) Succeeded succeeded;`

Indica si la operación se realizó correctamente. 