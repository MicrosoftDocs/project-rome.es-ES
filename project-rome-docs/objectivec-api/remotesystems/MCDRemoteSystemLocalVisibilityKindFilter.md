---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909577"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a><span data-ttu-id="ceaf1-104">Clase `MCDRemoteSystemLocalVisibilityKindFilter`</span><span class="sxs-lookup"><span data-stu-id="ceaf1-104">class `MCDRemoteSystemLocalVisibilityKindFilter`</span></span> 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="ceaf1-105">Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-105">A class used to set the local (calling) application visibility preference when discovering remote systems.</span></span>

## <a name="properties"></a><span data-ttu-id="ceaf1-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ceaf1-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="ceaf1-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="ceaf1-107">kind</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

<span data-ttu-id="ceaf1-108">Para filtrar con la configuración de visibilidad.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-108">The visibility setting to filter with.</span></span>

## <a name="constructors"></a><span data-ttu-id="ceaf1-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="ceaf1-109">Constructors</span></span>

### <a name="filterwithkind"></a><span data-ttu-id="ceaf1-110">filterWithKind</span><span class="sxs-lookup"><span data-stu-id="ceaf1-110">filterWithKind</span></span>
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="ceaf1-111">Crea e inicializa una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-111">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ceaf1-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ceaf1-112">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="ceaf1-113">Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-113">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="ceaf1-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="ceaf1-114">Returns</span></span>
<span data-ttu-id="ceaf1-115">Devuelve un objeto MCDRemoteSystemLocalVisibilityKind filtrado por tipo.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-115">Returns an MCDRemoteSystemLocalVisibilityKind object filtered by kind.</span></span>

### <a name="initwithkind"></a><span data-ttu-id="ceaf1-116">initWithKind</span><span class="sxs-lookup"><span data-stu-id="ceaf1-116">initWithKind</span></span>
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

<span data-ttu-id="ceaf1-117">Crea e inicializa una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-117">Creates and initializes an instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ceaf1-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ceaf1-118">Parameters</span></span>
* `localVisibilityKind` 

<span data-ttu-id="ceaf1-119">Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-119">An MCDRemoteSystemLocalVisibilityKind value indicating the local app visibility setting to filter with.</span></span>

#### <a name="returns"></a><span data-ttu-id="ceaf1-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="ceaf1-120">Returns</span></span>
<span data-ttu-id="ceaf1-121">Devuelve un objeto MCDRemoteSystemLocalVisibilityKind inicializado con tipo.</span><span class="sxs-lookup"><span data-stu-id="ceaf1-121">Returns an MCDRemoteSystemLocalVisibilityKind object initialized with kind.</span></span>