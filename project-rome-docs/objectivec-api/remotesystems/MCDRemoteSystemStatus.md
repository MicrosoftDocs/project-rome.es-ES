---
title: MCDRemoteSystemStatus
description: Contiene valores que describen la disponibilidad de un sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801377"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="50544-104">Enum `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="50544-104">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="50544-105">Contiene valores que describen la disponibilidad de un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="50544-105">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="50544-106">En las aplicaciones de iOS, un valor de **MCDRemoteSystemStatusUnknown** siempre se encuentre; otros valores solo están disponibles en sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="50544-106">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="50544-107">Campos</span><span class="sxs-lookup"><span data-stu-id="50544-107">Fields</span></span>

| <span data-ttu-id="50544-108">Name</span><span class="sxs-lookup"><span data-stu-id="50544-108">Name</span></span>                              | <span data-ttu-id="50544-109">Valor</span><span class="sxs-lookup"><span data-stu-id="50544-109">Value</span></span> | <span data-ttu-id="50544-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="50544-110">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="50544-111">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="50544-111">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="50544-112">0</span><span class="sxs-lookup"><span data-stu-id="50544-112">0</span></span> | <span data-ttu-id="50544-113">El sistema remoto se notifica como no disponible.</span><span class="sxs-lookup"><span data-stu-id="50544-113">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="50544-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="50544-114">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="50544-115">1</span><span class="sxs-lookup"><span data-stu-id="50544-115">1</span></span> | <span data-ttu-id="50544-116">Se está determinando el estado del sistema remoto (que se produce durante el proceso de detección).</span><span class="sxs-lookup"><span data-stu-id="50544-116">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="50544-117">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="50544-117">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="50544-118">2</span><span class="sxs-lookup"><span data-stu-id="50544-118">2</span></span> | <span data-ttu-id="50544-119">El sistema remoto se notifica como disponibles.</span><span class="sxs-lookup"><span data-stu-id="50544-119">The remote system is reported as available.</span></span> |
| <span data-ttu-id="50544-120">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="50544-120">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="50544-121">3</span><span class="sxs-lookup"><span data-stu-id="50544-121">3</span></span> | <span data-ttu-id="50544-122">El estado es desconocido.</span><span class="sxs-lookup"><span data-stu-id="50544-122">The status is unknown.</span></span> |
