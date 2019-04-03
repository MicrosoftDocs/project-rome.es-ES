---
title: MCDUserNotificationUserActionStateFilter
description: Contiene valores que clasifican las notificaciones de estado de acción del usuario (para la recuperación de notificación filtrada).
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907277"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="0268d-104">Enum `MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="0268d-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="0268d-105">Contiene valores que clasifican las notificaciones de estado de acción del usuario (para la recuperación de notificación filtrada).</span><span class="sxs-lookup"><span data-stu-id="0268d-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="0268d-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="0268d-106">Name</span></span> | <span data-ttu-id="0268d-107">Valor</span><span class="sxs-lookup"><span data-stu-id="0268d-107">Value</span></span> | <span data-ttu-id="0268d-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="0268d-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="0268d-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="0268d-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="0268d-110">0</span><span class="sxs-lookup"><span data-stu-id="0268d-110">0</span></span>| <span data-ttu-id="0268d-111">Incluir notificaciones independientemente del estado de acción del usuario.</span><span class="sxs-lookup"><span data-stu-id="0268d-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="0268d-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="0268d-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="0268d-113">1</span><span class="sxs-lookup"><span data-stu-id="0268d-113">1</span></span>| <span data-ttu-id="0268d-114">Incluyen las notificaciones que no se ha actuado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0268d-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="0268d-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="0268d-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="0268d-116">2</span><span class="sxs-lookup"><span data-stu-id="0268d-116">2</span></span>| <span data-ttu-id="0268d-117">Incluyen las notificaciones que se han activado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0268d-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="0268d-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="0268d-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="0268d-119">3</span><span class="sxs-lookup"><span data-stu-id="0268d-119">3</span></span>| <span data-ttu-id="0268d-120">Incluyen las notificaciones que se han descartado por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0268d-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="0268d-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="0268d-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="0268d-122">4</span><span class="sxs-lookup"><span data-stu-id="0268d-122">4</span></span>| <span data-ttu-id="0268d-123">Incluyen las notificaciones que se han pospuesto por el usuario.</span><span class="sxs-lookup"><span data-stu-id="0268d-123">Include notifications that have been snoozed by the user.</span></span>|