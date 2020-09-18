---
title: MCDRemoteSystemKindFilter
description: Obtenga información sobre la clase MCDRemoteSystemKindFilter. Esta clase se usa para filtrar los sistemas remotos en función del tipo de dispositivo.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760679"
---
# <a name="class-mcdremotesystemkindfilter"></a><span data-ttu-id="0cdfb-105">las `MCDRemoteSystemKindFilter`</span><span class="sxs-lookup"><span data-stu-id="0cdfb-105">class `MCDRemoteSystemKindFilter`</span></span> 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

<span data-ttu-id="0cdfb-106">Una clase que se usa para filtrar sistemas remotos en función del tipo de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-106">A class used to filter remote systems based upon device kind.</span></span>

## <a name="properties"></a><span data-ttu-id="0cdfb-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0cdfb-107">Properties</span></span>

### <a name="kinds"></a><span data-ttu-id="0cdfb-108">categorías</span><span class="sxs-lookup"><span data-stu-id="0cdfb-108">kinds</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

<span data-ttu-id="0cdfb-109">Matriz de cadenas que indica los tipos de dispositivo que se van a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-109">An array of strings indicating the kinds of device to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="0cdfb-110">Constructores</span><span class="sxs-lookup"><span data-stu-id="0cdfb-110">Constructors</span></span>

### <a name="filterwithkinds"></a><span data-ttu-id="0cdfb-111">filterWithKinds</span><span class="sxs-lookup"><span data-stu-id="0cdfb-111">filterWithKinds</span></span>
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="0cdfb-112">Nueva instancia de esta clase filtrada en tipos.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-112">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0cdfb-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0cdfb-113">Parameters</span></span> 
* `kinds`

 <span data-ttu-id="0cdfb-114">Matriz de cadenas que indica los tipos de dispositivos que se van a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-114">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0cdfb-115">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="0cdfb-115">Returns</span></span>
<span data-ttu-id="0cdfb-116">Devuelve un objeto MCDRemoteSystemKindFilter filtrado con tipos.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-116">Returns an MCDRemoteSystemKindFilter object filtered with kinds.</span></span>

### <a name="initwithkinds"></a><span data-ttu-id="0cdfb-117">initWithKinds</span><span class="sxs-lookup"><span data-stu-id="0cdfb-117">initWithKinds</span></span>
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

<span data-ttu-id="0cdfb-118">Nueva instancia de esta clase filtrada en tipos.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-118">A new instance of this class filtered on kinds.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0cdfb-119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0cdfb-119">Parameters</span></span> 
* `kinds` 

<span data-ttu-id="0cdfb-120">Matriz de cadenas que indica los tipos de dispositivos que se van a filtrar.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-120">An array of strings indicating the device kinds to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="0cdfb-121">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="0cdfb-121">Returns</span></span>
<span data-ttu-id="0cdfb-122">Devuelve un objeto MCDRemoteSystemKindFilter inicializado con tipos.</span><span class="sxs-lookup"><span data-stu-id="0cdfb-122">Returns an MCDRemoteSystemKindFilter object initialized with kinds.</span></span>