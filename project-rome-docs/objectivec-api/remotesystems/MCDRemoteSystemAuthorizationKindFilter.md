---
title: MCDRemoteSystemAuthorizationKindFilter
description: Una clase utilizada para filtrar según el tipo de autorización de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: da68c7a0eacd2018332d5e2fe5c8e3c906f473f8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801257"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a><span data-ttu-id="29bc1-104">Clase `MCDRemoteSystemAuthorizationKindFilter`</span><span class="sxs-lookup"><span data-stu-id="29bc1-104">class `MCDRemoteSystemAuthorizationKindFilter`</span></span> 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="29bc1-105">Una clase utilizada para filtrar según el tipo de autorización de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="29bc1-105">A class used to filter remote systems based on authorization type.</span></span>

## <a name="properties"></a><span data-ttu-id="29bc1-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="29bc1-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="29bc1-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="29bc1-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

<span data-ttu-id="29bc1-108">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="29bc1-108">The authorization type to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="29bc1-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="29bc1-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="29bc1-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="29bc1-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="29bc1-111">Una nueva instancia de esta clase MCDRemoteSystemAuthorizationKind a filtrar.</span><span class="sxs-lookup"><span data-stu-id="29bc1-111">A new instance of this class filtered on MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="29bc1-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="29bc1-112">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="29bc1-113">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="29bc1-113">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="29bc1-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="29bc1-114">Returns</span></span>
<span data-ttu-id="29bc1-115">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter con el filtro de autorización proporcionado.</span><span class="sxs-lookup"><span data-stu-id="29bc1-115">Returns an MCDRemoteSystemAuthorizationKindFilter object with the provided authorization filter.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="29bc1-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="29bc1-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

<span data-ttu-id="29bc1-117">Una nueva instancia de esta clase con MCDRemoteSystemAuthorizationKind.</span><span class="sxs-lookup"><span data-stu-id="29bc1-117">A new instance of this class with MCDRemoteSystemAuthorizationKind.</span></span>

#### <a name="parameters"></a><span data-ttu-id="29bc1-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="29bc1-118">Parameters</span></span> 
* `authorizationKind` 

<span data-ttu-id="29bc1-119">El tipo de autorización para filtrar.</span><span class="sxs-lookup"><span data-stu-id="29bc1-119">The authorization type to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="29bc1-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="29bc1-120">Returns</span></span>
<span data-ttu-id="29bc1-121">Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter inicializado con el authorizationKind.</span><span class="sxs-lookup"><span data-stu-id="29bc1-121">Returns an MCDRemoteSystemAuthorizationKindFilter object initialized with the authorizationKind.</span></span>