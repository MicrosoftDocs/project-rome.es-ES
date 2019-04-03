---
title: MCDRemoteSystemStatus
description: Contiene valores que describen la disponibilidad de un sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907587"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="1a210-104">Enum `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="1a210-104">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="1a210-105">Contiene valores que describen la disponibilidad de un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="1a210-105">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="1a210-106">En las aplicaciones de iOS, un valor de **MCDRemoteSystemStatusUnknown** siempre se encuentre; otros valores solo están disponibles en sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="1a210-106">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="1a210-107">Campos</span><span class="sxs-lookup"><span data-stu-id="1a210-107">Fields</span></span>

| <span data-ttu-id="1a210-108">Nombre</span><span class="sxs-lookup"><span data-stu-id="1a210-108">Name</span></span>                              | <span data-ttu-id="1a210-109">Valor</span><span class="sxs-lookup"><span data-stu-id="1a210-109">Value</span></span> | <span data-ttu-id="1a210-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="1a210-110">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="1a210-111">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="1a210-111">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="1a210-112">0</span><span class="sxs-lookup"><span data-stu-id="1a210-112">0</span></span> | <span data-ttu-id="1a210-113">El sistema remoto se notifica como no disponible.</span><span class="sxs-lookup"><span data-stu-id="1a210-113">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="1a210-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="1a210-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="1a210-115">1</span><span class="sxs-lookup"><span data-stu-id="1a210-115">1</span></span> | <span data-ttu-id="1a210-116">Se está determinando el estado del sistema remoto (que se produce durante el proceso de detección).</span><span class="sxs-lookup"><span data-stu-id="1a210-116">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="1a210-117">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="1a210-117">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="1a210-118">2</span><span class="sxs-lookup"><span data-stu-id="1a210-118">2</span></span> | <span data-ttu-id="1a210-119">El sistema remoto se notifica como disponibles.</span><span class="sxs-lookup"><span data-stu-id="1a210-119">The remote system is reported as available.</span></span> |
| <span data-ttu-id="1a210-120">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="1a210-120">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="1a210-121">3</span><span class="sxs-lookup"><span data-stu-id="1a210-121">3</span></span> | <span data-ttu-id="1a210-122">El estado es desconocido.</span><span class="sxs-lookup"><span data-stu-id="1a210-122">The status is unknown.</span></span> |
