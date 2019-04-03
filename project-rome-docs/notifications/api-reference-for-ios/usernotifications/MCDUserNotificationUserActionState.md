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
# <a name="enum-mcdusernotificationuseractionstate"></a><span data-ttu-id="ea4e2-104">Enum `MCDUserNotificationUserActionState`</span><span class="sxs-lookup"><span data-stu-id="ea4e2-104">enum `MCDUserNotificationUserActionState`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationUserActionState)
```

<span data-ttu-id="ea4e2-105">Contiene valores que describen la acción de que un usuario ha realizado en una notificación.</span><span class="sxs-lookup"><span data-stu-id="ea4e2-105">Contains values describing the action a user has taken on a notification.</span></span>

|<span data-ttu-id="ea4e2-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="ea4e2-106">Name</span></span> | <span data-ttu-id="ea4e2-107">Valor</span><span class="sxs-lookup"><span data-stu-id="ea4e2-107">Value</span></span> | <span data-ttu-id="ea4e2-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="ea4e2-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="ea4e2-109">MCDUserNotificationUserActionStateNoInteraction</span><span class="sxs-lookup"><span data-stu-id="ea4e2-109">MCDUserNotificationUserActionStateNoInteraction</span></span> |<span data-ttu-id="ea4e2-110">0</span><span class="sxs-lookup"><span data-stu-id="ea4e2-110">0</span></span>| <span data-ttu-id="ea4e2-111">El usuario no ha tomado ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="ea4e2-111">The user hasn't taken any action.</span></span>|
|   <span data-ttu-id="ea4e2-112">MCDUserNotificationUserActionStateActivated</span><span class="sxs-lookup"><span data-stu-id="ea4e2-112">MCDUserNotificationUserActionStateActivated</span></span>|<span data-ttu-id="ea4e2-113">1</span><span class="sxs-lookup"><span data-stu-id="ea4e2-113">1</span></span>|<span data-ttu-id="ea4e2-114">El usuario ha activado la notificación.</span><span class="sxs-lookup"><span data-stu-id="ea4e2-114">The user has activated the notification.</span></span>|
|   <span data-ttu-id="ea4e2-115">MCDUserNotificationUserActionStateDismissed</span><span class="sxs-lookup"><span data-stu-id="ea4e2-115">MCDUserNotificationUserActionStateDismissed</span></span>|<span data-ttu-id="ea4e2-116">2</span><span class="sxs-lookup"><span data-stu-id="ea4e2-116">2</span></span>| <span data-ttu-id="ea4e2-117">El usuario ha descartado la notificación.</span><span class="sxs-lookup"><span data-stu-id="ea4e2-117">The user has dismissed the notification.</span></span>|
|   <span data-ttu-id="ea4e2-118">MCDUserNotificationUserActionStateSnoozed</span><span class="sxs-lookup"><span data-stu-id="ea4e2-118">MCDUserNotificationUserActionStateSnoozed</span></span>|<span data-ttu-id="ea4e2-119">3</span><span class="sxs-lookup"><span data-stu-id="ea4e2-119">3</span></span>| <span data-ttu-id="ea4e2-120">El usuario ha posponer la notificación.</span><span class="sxs-lookup"><span data-stu-id="ea4e2-120">The user has snoozed the notification.</span></span>|
