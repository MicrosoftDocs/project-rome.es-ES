---
title: MCDRemoteSystemKindFilter
description: Una clase utilizada para filtrar según el tipo de dispositivo de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801337"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="5ee4d-104">Clase `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="5ee4d-104">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="5ee4d-105">Una clase utilizada para filtrar según el tipo de dispositivo de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-105">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="5ee4d-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="5ee4d-106">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="5ee4d-107">tipos</span><span class="sxs-lookup"><span data-stu-id="5ee4d-107">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="5ee4d-108">Una matriz de cadenas que indica los tipos de dispositivo para filtrar.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-108">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="5ee4d-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="5ee4d-109">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="5ee4d-110">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="5ee4d-110">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="5ee4d-111">Una nueva instancia de esta clase filtrada por tipos.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-111">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5ee4d-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5ee4d-112">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="5ee4d-113">Una matriz de cadenas que indica los tipos de dispositivo para filtrar.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-113">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="5ee4d-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="5ee4d-114">Returns</span></span>
<span data-ttu-id="5ee4d-115">Devuelve un objeto MCDRemoteSystemKindFilter filtrado con tipos.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-115">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="5ee4d-116">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="5ee4d-116">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="5ee4d-117">Una nueva instancia de esta clase filtrada por tipos.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-117">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5ee4d-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5ee4d-118">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="5ee4d-119">Una matriz de cadenas que indica los tipos de dispositivo para filtrar.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-119">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="5ee4d-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="5ee4d-120">Returns</span></span>
<span data-ttu-id="5ee4d-121">Devuelve un objeto MCDRemoteSystemKindFilter inicializado con los tipos.</span><span class="sxs-lookup"><span data-stu-id="5ee4d-121">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>