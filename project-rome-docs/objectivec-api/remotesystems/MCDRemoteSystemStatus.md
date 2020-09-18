---
title: MCDRemoteSystemStatus
description: Obtenga información sobre la enumeración MCDRemoteSystemStatus. Esta enumeración contiene valores que describen la disponibilidad de un sistema remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760659"
---
# <a name="enum-mcdremotesystemstatus"></a><span data-ttu-id="9b8a3-105">enumeración `MCDRemoteSystemStatus`</span><span class="sxs-lookup"><span data-stu-id="9b8a3-105">enum `MCDRemoteSystemStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
<span data-ttu-id="9b8a3-106">Contiene valores que describen la disponibilidad de un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="9b8a3-106">Contains values that describe the availability of a remote system.</span></span> <span data-ttu-id="9b8a3-107">En las aplicaciones iOS, siempre se encontrará un valor de **MCDRemoteSystemStatusUnknown** . otros valores solo están disponibles en los sistemas Windows.</span><span class="sxs-lookup"><span data-stu-id="9b8a3-107">On iOS apps, a value of **MCDRemoteSystemStatusUnknown** will always be encountered; other values are only available on Windows systems.</span></span>

## <a name="fields"></a><span data-ttu-id="9b8a3-108">Campos</span><span class="sxs-lookup"><span data-stu-id="9b8a3-108">Fields</span></span>

| <span data-ttu-id="9b8a3-109">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="9b8a3-109">Name</span></span>                              | <span data-ttu-id="9b8a3-110">Valor</span><span class="sxs-lookup"><span data-stu-id="9b8a3-110">Value</span></span> | <span data-ttu-id="9b8a3-111">Descripción</span><span class="sxs-lookup"><span data-stu-id="9b8a3-111">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="9b8a3-112">MCDRemoteSystemStatusUnavailable</span><span class="sxs-lookup"><span data-stu-id="9b8a3-112">MCDRemoteSystemStatusUnavailable</span></span> | <span data-ttu-id="9b8a3-113">0</span><span class="sxs-lookup"><span data-stu-id="9b8a3-113">0</span></span> | <span data-ttu-id="9b8a3-114">El sistema remoto se muestra como no disponible.</span><span class="sxs-lookup"><span data-stu-id="9b8a3-114">The remote system is reported as unavailable.</span></span> |
| <span data-ttu-id="9b8a3-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span><span class="sxs-lookup"><span data-stu-id="9b8a3-115">MCDRemoteSystemStatusDiscoveringAvailablilty</span></span> | <span data-ttu-id="9b8a3-116">1</span><span class="sxs-lookup"><span data-stu-id="9b8a3-116">1</span></span> | <span data-ttu-id="9b8a3-117">Se está determinando el estado del sistema remoto (se produce durante el proceso de detección).</span><span class="sxs-lookup"><span data-stu-id="9b8a3-117">The status of the remote system is being determined (occurs during the discovery process).</span></span> |
| <span data-ttu-id="9b8a3-118">MCDRemoteSystemStatusAvailable</span><span class="sxs-lookup"><span data-stu-id="9b8a3-118">MCDRemoteSystemStatusAvailable</span></span> | <span data-ttu-id="9b8a3-119">2</span><span class="sxs-lookup"><span data-stu-id="9b8a3-119">2</span></span> | <span data-ttu-id="9b8a3-120">El sistema remoto se muestra como disponible.</span><span class="sxs-lookup"><span data-stu-id="9b8a3-120">The remote system is reported as available.</span></span> |
| <span data-ttu-id="9b8a3-121">MCDRemoteSystemStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="9b8a3-121">MCDRemoteSystemStatusUnknown</span></span> | <span data-ttu-id="9b8a3-122">3</span><span class="sxs-lookup"><span data-stu-id="9b8a3-122">3</span></span> | <span data-ttu-id="9b8a3-123">El estado es desconocido.</span><span class="sxs-lookup"><span data-stu-id="9b8a3-123">The status is unknown.</span></span> |
