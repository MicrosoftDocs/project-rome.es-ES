---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800677"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a><span data-ttu-id="a77aa-104">Clase `MCDRemoteSystemLocalVisibilityKindFilter`</span><span class="sxs-lookup"><span data-stu-id="a77aa-104">class `MCDRemoteSystemLocalVisibilityKindFilter`</span></span> 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="a77aa-105">Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="a77aa-105">A class used to set the local (calling) application visibility preference when discovering remote systems.</span></span>

## <a name="properties"></a><span data-ttu-id="a77aa-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a77aa-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="a77aa-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="a77aa-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

<span data-ttu-id="a77aa-108">Para filtrar con la configuración de visibilidad.</span><span class="sxs-lookup"><span data-stu-id="a77aa-108">The visibility setting to filter with.</span></span>

## <a name="constructors"></a><span data-ttu-id="a77aa-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="a77aa-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="a77aa-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="a77aa-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="a77aa-111">Crea e inicializa una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="a77aa-111">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a77aa-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a77aa-112">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="a77aa-113">Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.</span><span class="sxs-lookup"><span data-stu-id="a77aa-113">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="a77aa-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a77aa-114">Returns</span></span>
<span data-ttu-id="a77aa-115">Devuelve un objeto MCDRemoteSystemLocalVisibilityKind filtrado por tipo.</span><span class="sxs-lookup"><span data-stu-id="a77aa-115">Returns an MCDRemoteSystemLocalVisibilityKind object filtered by kind.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="a77aa-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="a77aa-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="a77aa-117">Crea e inicializa una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="a77aa-117">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a77aa-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a77aa-118">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="a77aa-119">Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.</span><span class="sxs-lookup"><span data-stu-id="a77aa-119">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="a77aa-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a77aa-120">Returns</span></span>
<span data-ttu-id="a77aa-121">Devuelve un objeto MCDRemoteSystemLocalVisibilityKind inicializado con tipo.</span><span class="sxs-lookup"><span data-stu-id="a77aa-121">Returns an MCDRemoteSystemLocalVisibilityKind object initialized with kind.</span></span>