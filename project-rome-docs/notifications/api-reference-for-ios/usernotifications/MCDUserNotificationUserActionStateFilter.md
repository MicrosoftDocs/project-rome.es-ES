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
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="a5a0d-104">Enum `MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="a5a0d-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="a5a0d-105">Contiene valores que clasifican las notificaciones de estado de acción del usuario (para la recuperación de notificación filtrada).</span><span class="sxs-lookup"><span data-stu-id="a5a0d-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="a5a0d-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="a5a0d-106">Name</span></span> | <span data-ttu-id="a5a0d-107">Valor</span><span class="sxs-lookup"><span data-stu-id="a5a0d-107">Value</span></span> | <span data-ttu-id="a5a0d-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="a5a0d-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="a5a0d-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="a5a0d-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="a5a0d-110">0</span><span class="sxs-lookup"><span data-stu-id="a5a0d-110">0</span></span>| <span data-ttu-id="a5a0d-111">Incluir notificaciones independientemente del estado de acción del usuario.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="a5a0d-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="a5a0d-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="a5a0d-113">1</span><span class="sxs-lookup"><span data-stu-id="a5a0d-113">1</span></span>| <span data-ttu-id="a5a0d-114">Incluyen las notificaciones que no se ha actuado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="a5a0d-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="a5a0d-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="a5a0d-116">2</span><span class="sxs-lookup"><span data-stu-id="a5a0d-116">2</span></span>| <span data-ttu-id="a5a0d-117">Incluyen las notificaciones que se han activado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="a5a0d-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="a5a0d-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="a5a0d-119">3</span><span class="sxs-lookup"><span data-stu-id="a5a0d-119">3</span></span>| <span data-ttu-id="a5a0d-120">Incluyen las notificaciones que se han descartado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="a5a0d-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="a5a0d-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="a5a0d-122">4</span><span class="sxs-lookup"><span data-stu-id="a5a0d-122">4</span></span>| <span data-ttu-id="a5a0d-123">Incluyen las notificaciones que se han pospuesto por el usuario.</span><span class="sxs-lookup"><span data-stu-id="a5a0d-123">Include notifications that have been snoozed by the user.</span></span>|