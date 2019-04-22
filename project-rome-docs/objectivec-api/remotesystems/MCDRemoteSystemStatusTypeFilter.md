---
title: MCDRemoteSystemStatusTypeFilter
description: Una clase utilizada para filtrar según el tipo de estado de disponibilidad de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907127"
---
# <a name="class-mcdremotesystemstatustypefilter"></a><span data-ttu-id="02c4d-104">Clase `MCDRemoteSystemStatusTypeFilter`</span><span class="sxs-lookup"><span data-stu-id="02c4d-104">class `MCDRemoteSystemStatusTypeFilter`</span></span>

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

<span data-ttu-id="02c4d-105">Una clase utilizada para filtrar según el tipo de estado de disponibilidad de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="02c4d-105">A class used to filter remote systems based on availability status type.</span></span>

## <a name="properties"></a><span data-ttu-id="02c4d-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="02c4d-106">Properties</span></span>

### <a name="type"></a><span data-ttu-id="02c4d-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="02c4d-107">type</span></span>
<span data-ttu-id="02c4d-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` El tipo de estado del sistema remoto de esta instancia de filtro.</span><span class="sxs-lookup"><span data-stu-id="02c4d-108">`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` The remote system status type of this filter instance.</span></span>

## <a name="constructors"></a><span data-ttu-id="02c4d-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="02c4d-109">Constructors</span></span>

### <a name="filterwithtype"></a><span data-ttu-id="02c4d-110">filterWithType</span><span class="sxs-lookup"><span data-stu-id="02c4d-110">filterWithType</span></span>
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="02c4d-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="02c4d-111">Parameters</span></span> 
* <span data-ttu-id="02c4d-112">`statusType` Un valor que indica el tipo de estado de disponibilidad para filtrar.</span><span class="sxs-lookup"><span data-stu-id="02c4d-112">`statusType` A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="02c4d-113">Devuelve</span><span class="sxs-lookup"><span data-stu-id="02c4d-113">Returns</span></span>
<span data-ttu-id="02c4d-114">Devuelve un objeto MCDRemoteSystemStatusTypeFilter filtrado por tipo.</span><span class="sxs-lookup"><span data-stu-id="02c4d-114">Returns an MCDRemoteSystemStatusTypeFilter object filtered by type.</span></span>

### <a name="initwithtype"></a><span data-ttu-id="02c4d-115">initWithType</span><span class="sxs-lookup"><span data-stu-id="02c4d-115">initWithType</span></span>
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a><span data-ttu-id="02c4d-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="02c4d-116">Parameters</span></span> 
* `statusType` 

<span data-ttu-id="02c4d-117">Un valor que indica el tipo de estado de disponibilidad para filtrar.</span><span class="sxs-lookup"><span data-stu-id="02c4d-117">A value indicating the availability status type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="02c4d-118">Devuelve</span><span class="sxs-lookup"><span data-stu-id="02c4d-118">Returns</span></span>
<span data-ttu-id="02c4d-119">Devuelve un objeto MCDRemoteSystemStatusTypeFilter inicializado con el tipo.</span><span class="sxs-lookup"><span data-stu-id="02c4d-119">Returns an MCDRemoteSystemStatusTypeFilter object initialized with the type.</span></span>