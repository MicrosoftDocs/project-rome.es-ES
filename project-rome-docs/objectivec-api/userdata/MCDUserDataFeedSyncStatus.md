---
title: MCDUserDataSyncStatus
description: Contiene valores que describen el estado de un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de sincronización con la plataforma de dispositivos conectados de back-end.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 805192b0d9169c799f30b7daa0371767145ae86f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908627"
---
# <a name="enum-mcduserdatasyncstatus"></a><span data-ttu-id="2bc66-104">Enum `MCDUserDataSyncStatus`</span><span class="sxs-lookup"><span data-stu-id="2bc66-104">enum `MCDUserDataSyncStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserDataSyncStatus)
```

<span data-ttu-id="2bc66-105">Contiene valores que describen el estado de un  **[MCDUserDataFeed](MCDUserDataFeed.md)** de sincronización con la plataforma de dispositivos conectados de back-end.</span><span class="sxs-lookup"><span data-stu-id="2bc66-105">Contains values that describe the state of a **[MCDUserDataFeed](MCDUserDataFeed.md)**'s synchronization with the Connected Devices Platform backend.</span></span>

|<span data-ttu-id="2bc66-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="2bc66-106">Name</span></span> | <span data-ttu-id="2bc66-107">Valor</span><span class="sxs-lookup"><span data-stu-id="2bc66-107">Value</span></span> | <span data-ttu-id="2bc66-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="2bc66-108">Description</span></span> |
|:-- |:-- |:-- |
|  <span data-ttu-id="2bc66-109">MCDUserDataFeedSyncStatusQueued</span><span class="sxs-lookup"><span data-stu-id="2bc66-109">MCDUserDataFeedSyncStatusQueued</span></span> |<span data-ttu-id="2bc66-110">0</span><span class="sxs-lookup"><span data-stu-id="2bc66-110">0</span></span>| <span data-ttu-id="2bc66-111">Los datos no se ha sincronizado.</span><span class="sxs-lookup"><span data-stu-id="2bc66-111">The data is not yet synchronized.</span></span> |
| <span data-ttu-id="2bc66-112">MCDUserDataFeedSyncStatusSynchronized</span><span class="sxs-lookup"><span data-stu-id="2bc66-112">MCDUserDataFeedSyncStatusSynchronized</span></span> |<span data-ttu-id="2bc66-113">1</span><span class="sxs-lookup"><span data-stu-id="2bc66-113">1</span></span>| <span data-ttu-id="2bc66-114">Los datos se han sincronizado.</span><span class="sxs-lookup"><span data-stu-id="2bc66-114">The data has been synchronized.</span></span>|