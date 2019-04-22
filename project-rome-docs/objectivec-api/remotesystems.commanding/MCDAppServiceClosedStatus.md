---
title: MCDAppServiceClosedStatus
description: Contiene valores que describen una conexión cerrada a un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9a56ee489175cb065fde281acb4ae8a345fb851b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800777"
---
# <a name="enum-mcdappserviceclosedstatus"></a><span data-ttu-id="d7b1b-104">Enum `MCDAppServiceClosedStatus`</span><span class="sxs-lookup"><span data-stu-id="d7b1b-104">enum `MCDAppServiceClosedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceClosedStatus)
```

<span data-ttu-id="d7b1b-105">Contiene valores que describen una conexión cerrada a un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-105">Contains values that describe a closed connection to a remote app service.</span></span>

|<span data-ttu-id="d7b1b-106">Miembro</span><span class="sxs-lookup"><span data-stu-id="d7b1b-106">Member</span></span>   |<span data-ttu-id="d7b1b-107">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b1b-107">Value</span></span>   |<span data-ttu-id="d7b1b-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="d7b1b-108">Description</span></span>   |
|--------|-------|-------------|
|<span data-ttu-id="d7b1b-109">MCDAppServiceClosedStatusCompleted</span><span class="sxs-lookup"><span data-stu-id="d7b1b-109">MCDAppServiceClosedStatusCompleted</span></span> |<span data-ttu-id="d7b1b-110">0</span><span class="sxs-lookup"><span data-stu-id="d7b1b-110">0</span></span>| <span data-ttu-id="d7b1b-111">El punto de conexión para el servicio de aplicación se cierra correctamente.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-111">The endpoint for the app service closed gracefully.</span></span>|
|<span data-ttu-id="d7b1b-112">MCDAppServiceClosedStatusCanceled</span><span class="sxs-lookup"><span data-stu-id="d7b1b-112">MCDAppServiceClosedStatusCanceled</span></span> |<span data-ttu-id="d7b1b-113">1</span><span class="sxs-lookup"><span data-stu-id="d7b1b-113">1</span></span>| <span data-ttu-id="d7b1b-114">El punto de conexión para el servicio de aplicación fue cerrada por el cliente o el sistema.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-114">The endpoint for the app service was closed by the client or the system.</span></span>|
|<span data-ttu-id="d7b1b-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="d7b1b-115">MCDAppServiceClosedStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="d7b1b-116">2</span><span class="sxs-lookup"><span data-stu-id="d7b1b-116">2</span></span>| <span data-ttu-id="d7b1b-117">El punto de conexión para el servicio de aplicación se ha cerrado porque el punto de conexión se quedó sin recursos.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-117">The endpoint for the app service was closed because the endpoint ran out of resources.</span></span>|
|<span data-ttu-id="d7b1b-118">MCDAppServiceClosedStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="d7b1b-118">MCDAppServiceClosedStatusUnknown</span></span> |<span data-ttu-id="d7b1b-119">3</span><span class="sxs-lookup"><span data-stu-id="d7b1b-119">3</span></span>| <span data-ttu-id="d7b1b-120">Se produjo un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="d7b1b-120">An unknown error occurred.</span></span>|