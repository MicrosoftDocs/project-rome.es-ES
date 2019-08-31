---
title: MCDUserNotificationUserActionStateFilter
description: Contiene valores que clasifican las notificaciones por estado de acción del usuario (para la recuperación de notificaciones filtradas).
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 41719d76e03fd6def57c8f77f9ab6956811e8803
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800567"
---
# <a name="enum-mcdusernotificationuseractionstatefilter"></a><span data-ttu-id="856be-104">enumeración`MCDUserNotificationUserActionStateFilter`</span><span class="sxs-lookup"><span data-stu-id="856be-104">enum `MCDUserNotificationUserActionStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionStateFilter)
```

<span data-ttu-id="856be-105">Contiene valores que clasifican las notificaciones por estado de acción del usuario (para la recuperación de notificaciones filtradas).</span><span class="sxs-lookup"><span data-stu-id="856be-105">Contains values that categorize notifications by user action state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="856be-106">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="856be-106">Name</span></span> | <span data-ttu-id="856be-107">Valor</span><span class="sxs-lookup"><span data-stu-id="856be-107">Value</span></span> | <span data-ttu-id="856be-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="856be-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="856be-109">MCDUserNotificationUserActionStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="856be-109">MCDUserNotificationUserActionStateFilterAny</span></span>|<span data-ttu-id="856be-110">0</span><span class="sxs-lookup"><span data-stu-id="856be-110">0</span></span>| <span data-ttu-id="856be-111">Incluye notificaciones independientemente del estado de acción del usuario.</span><span class="sxs-lookup"><span data-stu-id="856be-111">Include notifications regardless of user action state.</span></span>|
|   <span data-ttu-id="856be-112">MCDUserNotificationUserActionStateFilterNoInteraction</span><span class="sxs-lookup"><span data-stu-id="856be-112">MCDUserNotificationUserActionStateFilterNoInteraction</span></span> |<span data-ttu-id="856be-113">1</span><span class="sxs-lookup"><span data-stu-id="856be-113">1</span></span>| <span data-ttu-id="856be-114">Incluye notificaciones en las que el usuario no ha actuado.</span><span class="sxs-lookup"><span data-stu-id="856be-114">Include notifications that have not been acted on by the user.</span></span>|
|   <span data-ttu-id="856be-115">MCDUserNotificationUserActionStateFilterActivated</span><span class="sxs-lookup"><span data-stu-id="856be-115">MCDUserNotificationUserActionStateFilterActivated</span></span>|<span data-ttu-id="856be-116">2</span><span class="sxs-lookup"><span data-stu-id="856be-116">2</span></span>| <span data-ttu-id="856be-117">Incluye notificaciones activadas por el usuario.</span><span class="sxs-lookup"><span data-stu-id="856be-117">Include notifications that have been activated by the user.</span></span>|
|   <span data-ttu-id="856be-118">MCDUserNotificationUserActionStateFilterDismissed</span><span class="sxs-lookup"><span data-stu-id="856be-118">MCDUserNotificationUserActionStateFilterDismissed</span></span>|<span data-ttu-id="856be-119">3</span><span class="sxs-lookup"><span data-stu-id="856be-119">3</span></span>| <span data-ttu-id="856be-120">Incluye notificaciones que el usuario ha descartado.</span><span class="sxs-lookup"><span data-stu-id="856be-120">Include notifications that have been dismissed by the user.</span></span>|
|   <span data-ttu-id="856be-121">MCDUserNotificationUserActionStateFilterSnoozed</span><span class="sxs-lookup"><span data-stu-id="856be-121">MCDUserNotificationUserActionStateFilterSnoozed</span></span>|<span data-ttu-id="856be-122">4</span><span class="sxs-lookup"><span data-stu-id="856be-122">4</span></span>| <span data-ttu-id="856be-123">Incluye notificaciones que el usuario ha pospuesto.</span><span class="sxs-lookup"><span data-stu-id="856be-123">Include notifications that have been snoozed by the user.</span></span>|