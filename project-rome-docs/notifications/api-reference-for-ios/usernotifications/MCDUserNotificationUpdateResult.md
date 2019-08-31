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
# <a name="class-mcdusernotificationupdateresult"></a><span data-ttu-id="d0805-104">las`MCDUserNotificationUpdateResult`</span><span class="sxs-lookup"><span data-stu-id="d0805-104">class `MCDUserNotificationUpdateResult`</span></span>

```
@interface MCDUserNotificationUpdateResult : NSObject
```

<span data-ttu-id="d0805-105">Esta clase describe el estado de un intento de actualizar una notificación.</span><span class="sxs-lookup"><span data-stu-id="d0805-105">This class describes the status of an attempt to update a notification.</span></span>

## <a name="properties"></a><span data-ttu-id="d0805-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d0805-106">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="d0805-107">notificationId</span><span class="sxs-lookup"><span data-stu-id="d0805-107">notificationId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`

<span data-ttu-id="d0805-108">IDENTIFICADOR de la notificación.</span><span class="sxs-lookup"><span data-stu-id="d0805-108">The ID of the notification.</span></span>

### <a name="succeeded"></a><span data-ttu-id="d0805-109">completa</span><span class="sxs-lookup"><span data-stu-id="d0805-109">succeeded</span></span>
`@property(nonatomic, readonly) Succeeded succeeded;`

<span data-ttu-id="d0805-110">Indica si la operación se realizó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d0805-110">Whether the operation succeeded.</span></span> 