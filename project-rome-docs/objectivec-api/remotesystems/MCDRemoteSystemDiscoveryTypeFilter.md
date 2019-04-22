---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Una clase utilizada para filtrar según el tipo de detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907527"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="6103f-104">Clase `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="6103f-104">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="6103f-105">Una clase utilizada para filtrar según el tipo de detección de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="6103f-105">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="6103f-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="6103f-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="6103f-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="6103f-107">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="6103f-108">El tipo de detección para filtrar.</span><span class="sxs-lookup"><span data-stu-id="6103f-108">The discovery type to filter for.</span></span>

> <span data-ttu-id="6103f-109">Nota: En Android, la plataforma de dispositivos conectados solo puede usar Bluetooth en sistemas que ejecutan Android 8.0 (Oreo) o una versión posterior.</span><span class="sxs-lookup"><span data-stu-id="6103f-109">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="6103f-110">Constructores</span><span class="sxs-lookup"><span data-stu-id="6103f-110">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="6103f-111">filterWithType</span><span class="sxs-lookup"><span data-stu-id="6103f-111">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="6103f-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6103f-112">Parameters</span></span> 
* <span data-ttu-id="6103f-113">`discoveryType` El tipo de detección para filtrar.</span><span class="sxs-lookup"><span data-stu-id="6103f-113">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="6103f-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="6103f-114">Returns</span></span>
<span data-ttu-id="6103f-115">Una nueva instancia de esta clase con el valor del tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="6103f-115">A new instance of this class with the given type value.</span></span> <span data-ttu-id="6103f-116">Los valores pueden estar unidos por and conjuntamente para aplicar varios filtros a la vez.</span><span class="sxs-lookup"><span data-stu-id="6103f-116">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="6103f-117">initWithType</span><span class="sxs-lookup"><span data-stu-id="6103f-117">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="6103f-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6103f-118">Parameters</span></span> 
* <span data-ttu-id="6103f-119">`discoveryType` El tipo de detección para filtrar.</span><span class="sxs-lookup"><span data-stu-id="6103f-119">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="6103f-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="6103f-120">Returns</span></span>
<span data-ttu-id="6103f-121">Una nueva instancia de esta clase con el valor del tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="6103f-121">A new instance of this class with the given type value.</span></span> <span data-ttu-id="6103f-122">Los valores pueden estar unidos por and conjuntamente para aplicar varios filtros a la vez.</span><span class="sxs-lookup"><span data-stu-id="6103f-122">Values can be AND'ed together to apply multiple filters at once.</span></span>