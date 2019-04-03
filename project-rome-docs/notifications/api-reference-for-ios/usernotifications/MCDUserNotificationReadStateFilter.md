---
title: MCDUserNotificationReadStateFilter
description: Contiene valores que clasifican las notificaciones de estado de lectura (para la recuperación de notificación filtrada).
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 19da2f22e88dba5617ee60169c06552191aebe7d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907697"
---
# <a name="enum-mcdusernotificationreadstatefilter"></a><span data-ttu-id="8103e-104">Enum `MCDUserNotificationReadStateFilter`</span><span class="sxs-lookup"><span data-stu-id="8103e-104">enum `MCDUserNotificationReadStateFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationReadStateFilter)
```

<span data-ttu-id="8103e-105">Contiene valores que clasifican las notificaciones de estado de lectura (para la recuperación de notificación filtrada).</span><span class="sxs-lookup"><span data-stu-id="8103e-105">Contains values that categorize notifications by read state (for filtered notification retrieval).</span></span>

|<span data-ttu-id="8103e-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="8103e-106">Name</span></span> | <span data-ttu-id="8103e-107">Valor</span><span class="sxs-lookup"><span data-stu-id="8103e-107">Value</span></span> | <span data-ttu-id="8103e-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="8103e-108">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="8103e-109">MCDUserNotificationReadStateFilterAny</span><span class="sxs-lookup"><span data-stu-id="8103e-109">MCDUserNotificationReadStateFilterAny</span></span> | <span data-ttu-id="8103e-110">0</span><span class="sxs-lookup"><span data-stu-id="8103e-110">0</span></span> | <span data-ttu-id="8103e-111">Incluir notificaciones independientemente del estado de lectura.</span><span class="sxs-lookup"><span data-stu-id="8103e-111">Include notifications regardless of read state.</span></span>|
|   <span data-ttu-id="8103e-112">MCDUserNotificationReadStateFilterUnread</span><span class="sxs-lookup"><span data-stu-id="8103e-112">MCDUserNotificationReadStateFilterUnread</span></span> | <span data-ttu-id="8103e-113">1</span><span class="sxs-lookup"><span data-stu-id="8103e-113">1</span></span> | <span data-ttu-id="8103e-114">Incluyen las notificaciones que no los ha leído.</span><span class="sxs-lookup"><span data-stu-id="8103e-114">Include notifications that haven't been read.</span></span>|
|   <span data-ttu-id="8103e-115">MCDUserNotificationReadStateFilterRead</span><span class="sxs-lookup"><span data-stu-id="8103e-115">MCDUserNotificationReadStateFilterRead</span></span> | <span data-ttu-id="8103e-116">2</span><span class="sxs-lookup"><span data-stu-id="8103e-116">2</span></span> | <span data-ttu-id="8103e-117">Incluyen las notificaciones que se han leído.</span><span class="sxs-lookup"><span data-stu-id="8103e-117">Include notifications that have been read.</span></span> |