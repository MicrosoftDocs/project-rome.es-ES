---
title: MCDUserNotificationReadStateFilter
description: Contiene valores que clasifican las notificaciones por estado de lectura (para la recuperación de notificaciones filtradas).
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801347"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="aeac9-104">enumeración`MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="aeac9-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="aeac9-105">Contiene valores que clasifican las notificaciones por estado de lectura (para la recuperación de notificaciones filtradas).</span><span class="sxs-lookup"><span data-stu-id="aeac9-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="aeac9-106">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="aeac9-106">Name</span></span> | <span data-ttu-id="aeac9-107">Valor</span><span class="sxs-lookup"><span data-stu-id="aeac9-107">Value</span></span> | <span data-ttu-id="aeac9-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="aeac9-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="aeac9-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="aeac9-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="aeac9-110">0</span><span class="sxs-lookup"><span data-stu-id="aeac9-110">0</span></span> | <span data-ttu-id="aeac9-111">Incluye notificaciones independientemente del estado de lectura.</span><span class="sxs-lookup"><span data-stu-id="aeac9-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="aeac9-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="aeac9-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="aeac9-113">1</span><span class="sxs-lookup"><span data-stu-id="aeac9-113">1</span></span> | <span data-ttu-id="aeac9-114">Incluye notificaciones que no se han leído.</span><span class="sxs-lookup"><span data-stu-id="aeac9-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="aeac9-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="aeac9-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="aeac9-116">2</span><span class="sxs-lookup"><span data-stu-id="aeac9-116">2</span></span> | <span data-ttu-id="aeac9-117">Incluye las notificaciones que se han leído.</span><span class="sxs-lookup"><span data-stu-id="aeac9-117">Include notifications that have been read.</span></span> |