---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Obtenga información sobre la clase MCDRemoteSystemDiscoveryTypeFilter. Esta clase se usa para filtrar los sistemas remotos según el tipo de detección.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760699"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a><span data-ttu-id="0f527-105">las `MCDRemoteSystemDiscoveryTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="0f527-105">class `MCDRemoteSystemDiscoveryTypeFilter`</span></span> 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="0f527-106">Clase utilizada para filtrar los sistemas remotos según el tipo de detección.</span><span class="sxs-lookup"><span data-stu-id="0f527-106">A class used to filter remote systems based upon discovery type.</span></span>

## <a name="properties"></a><span data-ttu-id="0f527-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0f527-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="0f527-108">type</span><span class="sxs-lookup"><span data-stu-id="0f527-108">type</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

<span data-ttu-id="0f527-109">Tipo de detección que se va a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0f527-109">The discovery type to filter for.</span></span>

> <span data-ttu-id="0f527-110">Nota: en Android, la plataforma de dispositivos conectados solo puede usar Bluetooth en sistemas que ejecutan Android 8,0 (Oreo) o posterior.</span><span class="sxs-lookup"><span data-stu-id="0f527-110">Note: On Android, the Connected Devices Platform can only use Bluetooth on systems running Android 8.0 (Oreo) or later.</span></span>

## <a name="constructors"></a><span data-ttu-id="0f527-111">Constructores</span><span class="sxs-lookup"><span data-stu-id="0f527-111">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="0f527-112">filterWithType</span><span class="sxs-lookup"><span data-stu-id="0f527-112">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="0f527-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0f527-113">Parameters</span></span> 
* <span data-ttu-id="0f527-114">`discoveryType` Tipo de detección que se va a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0f527-114">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0f527-115">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="0f527-115">Returns</span></span>
<span data-ttu-id="0f527-116">Nueva instancia de esta clase con el valor de tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0f527-116">A new instance of this class with the given type value.</span></span> <span data-ttu-id="0f527-117">Los valores se pueden AND'ed juntos para aplicar varios filtros a la vez.</span><span class="sxs-lookup"><span data-stu-id="0f527-117">Values can be AND'ed together to apply multiple filters at once.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="0f527-118">initWithType</span><span class="sxs-lookup"><span data-stu-id="0f527-118">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a><span data-ttu-id="0f527-119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0f527-119">Parameters</span></span> 
* <span data-ttu-id="0f527-120">`discoveryType` Tipo de detección que se va a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0f527-120">`discoveryType` The discovery type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0f527-121">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="0f527-121">Returns</span></span>
<span data-ttu-id="0f527-122">Nueva instancia de esta clase con el valor de tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="0f527-122">A new instance of this class with the given type value.</span></span> <span data-ttu-id="0f527-123">Los valores se pueden AND'ed juntos para aplicar varios filtros a la vez.</span><span class="sxs-lookup"><span data-stu-id="0f527-123">Values can be AND'ed together to apply multiple filters at once.</span></span>