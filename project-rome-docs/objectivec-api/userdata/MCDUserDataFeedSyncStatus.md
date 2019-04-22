---
title: MCDUserDataSyncStatus
description: Contiene valores que describen el estado de un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de sincronización con la plataforma de dispositivos conectados de back-end.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801417"
---
# <a name="enum-mcduserdatasyncstatus"></a><span data-ttu-id="f5dd9-104">Enum `MCDUserDataSyncStatus`</span><span class="sxs-lookup"><span data-stu-id="f5dd9-104">enum `MCDUserDataSyncStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

<span data-ttu-id="f5dd9-105">Contiene valores que describen el estado de un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de sincronización con la plataforma de dispositivos conectados de back-end.</span><span class="sxs-lookup"><span data-stu-id="f5dd9-105">Contains values that describe the state of a **[MCDUserDataFeed](MCDUserDataFeed.md)**'s synchronization with the Connected Devices Platform backend.</span></span>

|<span data-ttu-id="f5dd9-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="f5dd9-106">Name</span></span> | <span data-ttu-id="f5dd9-107">Valor</span><span class="sxs-lookup"><span data-stu-id="f5dd9-107">Value</span></span> | <span data-ttu-id="f5dd9-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="f5dd9-108">Description</span></span> |
|:-- |:-- |:-- |
|  <span data-ttu-id="f5dd9-109">MCDUserDataFeedSyncStatusQueued</span><span class="sxs-lookup"><span data-stu-id="f5dd9-109">MCDUserDataFeedSyncStatusQueued</span></span> |<span data-ttu-id="f5dd9-110">0</span><span class="sxs-lookup"><span data-stu-id="f5dd9-110">0</span></span>| <span data-ttu-id="f5dd9-111">Los datos no se ha sincronizado.</span><span class="sxs-lookup"><span data-stu-id="f5dd9-111">The data is not yet synchronized.</span></span> |
| <span data-ttu-id="f5dd9-112">MCDUserDataFeedSyncStatusSynchronized</span><span class="sxs-lookup"><span data-stu-id="f5dd9-112">MCDUserDataFeedSyncStatusSynchronized</span></span> |<span data-ttu-id="f5dd9-113">1</span><span class="sxs-lookup"><span data-stu-id="f5dd9-113">1</span></span>| <span data-ttu-id="f5dd9-114">Los datos se han sincronizado.</span><span class="sxs-lookup"><span data-stu-id="f5dd9-114">The data has been synchronized.</span></span>|