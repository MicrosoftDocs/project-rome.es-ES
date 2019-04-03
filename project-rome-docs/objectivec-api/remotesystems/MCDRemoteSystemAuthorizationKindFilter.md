---
title: MCDRemoteSystemAuthorizationKindFilter
description: Una clase utilizada para filtrar según el tipo de autorización de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907647"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="78d1b-104">Clase `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="78d1b-104">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="78d1b-105">Una clase utilizada para filtrar según el tipo de autorización de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="78d1b-105">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="78d1b-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="78d1b-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="78d1b-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="78d1b-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="78d1b-108">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="78d1b-108">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="78d1b-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="78d1b-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="78d1b-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="78d1b-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="78d1b-111">Una nueva instancia de esta clase MCDRemoteSystemAuthorizationKind a filtrar.</span><span class="sxs-lookup"><span data-stu-id="78d1b-111">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="78d1b-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="78d1b-112">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="78d1b-113">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="78d1b-113">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="78d1b-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="78d1b-114">Returns</span></span>
<span data-ttu-id="78d1b-115">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter con el filtro de autorización proporcionado.</span><span class="sxs-lookup"><span data-stu-id="78d1b-115">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="78d1b-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="78d1b-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="78d1b-117">Una nueva instancia de esta clase con MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="78d1b-117">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="78d1b-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="78d1b-118">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="78d1b-119">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="78d1b-119">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="78d1b-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="78d1b-120">Returns</span></span>
<span data-ttu-id="78d1b-121">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter inicializado con el authorizationKind.</span><span class="sxs-lookup"><span data-stu-id="78d1b-121">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>