---
title: MCDRemoteSystemAuthorizationKindFilter
description: Obtenga información sobre la clase MCDRemoteSystemAuthorizationKindFilter. Esta clase se usa para filtrar los sistemas remotos según el tipo de autorización.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760709"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="04f0b-105">las `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="04f0b-105">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="04f0b-106">Clase utilizada para filtrar los sistemas remotos según el tipo de autorización.</span><span class="sxs-lookup"><span data-stu-id="04f0b-106">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="04f0b-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="04f0b-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="04f0b-108">kind</span><span class="sxs-lookup"><span data-stu-id="04f0b-108">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="04f0b-109">Tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="04f0b-109">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="04f0b-110">Constructores</span><span class="sxs-lookup"><span data-stu-id="04f0b-110">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="04f0b-111">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="04f0b-111">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="04f0b-112">Nueva instancia de esta clase filtrada en MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="04f0b-112">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="04f0b-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="04f0b-113">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="04f0b-114">Tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="04f0b-114">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="04f0b-115">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="04f0b-115">Returns</span></span>
<span data-ttu-id="04f0b-116">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter con el filtro de autorización proporcionado.</span><span class="sxs-lookup"><span data-stu-id="04f0b-116">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="04f0b-117">initWithKind</span><span class="sxs-lookup"><span data-stu-id="04f0b-117">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="04f0b-118">Nueva instancia de esta clase con MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="04f0b-118">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="04f0b-119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="04f0b-119">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="04f0b-120">Tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="04f0b-120">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="04f0b-121">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="04f0b-121">Returns</span></span>
<span data-ttu-id="04f0b-122">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter inicializado con authorizationKind.</span><span class="sxs-lookup"><span data-stu-id="04f0b-122">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>