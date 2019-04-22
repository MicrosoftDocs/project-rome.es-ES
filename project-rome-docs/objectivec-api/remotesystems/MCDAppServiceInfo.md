---
title: MCDAppServiceInfo
description: Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801167"
---
# <a name="class-mcdappserviceinfo"></a><span data-ttu-id="a38b5-104">Clase `MCDAppServiceInfo`</span><span class="sxs-lookup"><span data-stu-id="a38b5-104">class `MCDAppServiceInfo`</span></span> 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

<span data-ttu-id="a38b5-105">Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="a38b5-105">This class describes an app service that belongs to a remote device or application.</span></span>

## <a name="properties"></a><span data-ttu-id="a38b5-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a38b5-106">Properties</span></span>

### <a name="name"></a><span data-ttu-id="a38b5-107">NAME</span><span class="sxs-lookup"><span data-stu-id="a38b5-107">name</span></span>
`@property(nonatomic, readonly, nullable) NSString* name;`

<span data-ttu-id="a38b5-108">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-108">The name of the app service being described.</span></span>

### <a name="packageid"></a><span data-ttu-id="a38b5-109">packageId</span><span class="sxs-lookup"><span data-stu-id="a38b5-109">packageId</span></span>
`@property(nonatomic, readonly, nullable) NSString* packageId;`

<span data-ttu-id="a38b5-110">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-110">The package ID of the app service being described.</span></span>

## <a name="constructors"></a><span data-ttu-id="a38b5-111">Constructores</span><span class="sxs-lookup"><span data-stu-id="a38b5-111">Constructors</span></span>

### <a name="infowithname"></a><span data-ttu-id="a38b5-112">infoWithName</span><span class="sxs-lookup"><span data-stu-id="a38b5-112">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

<span data-ttu-id="a38b5-113">Inicializar la clase con información y el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a38b5-113">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a38b5-114">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a38b5-114">Parameters</span></span> 
* `name` 

<span data-ttu-id="a38b5-115">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-115">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a38b5-116">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a38b5-116">Returns</span></span>
<span data-ttu-id="a38b5-117">Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a38b5-117">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="a38b5-118">initWithName</span><span class="sxs-lookup"><span data-stu-id="a38b5-118">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

<span data-ttu-id="a38b5-119">Inicializar la clase con el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a38b5-119">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a38b5-120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a38b5-120">Parameters</span></span> 
* `name` 

<span data-ttu-id="a38b5-121">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-121">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a38b5-122">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a38b5-122">Returns</span></span>
<span data-ttu-id="a38b5-123">Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a38b5-123">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>

### <a name="infowithname"></a><span data-ttu-id="a38b5-124">infoWithName</span><span class="sxs-lookup"><span data-stu-id="a38b5-124">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="a38b5-125">Inicializar la clase con información y el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a38b5-125">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a38b5-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a38b5-126">Parameters</span></span> 
* `name` 

<span data-ttu-id="a38b5-127">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-127">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="a38b5-128">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-128">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a38b5-129">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a38b5-129">Returns</span></span>
<span data-ttu-id="a38b5-130">Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a38b5-130">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="a38b5-131">initWithName</span><span class="sxs-lookup"><span data-stu-id="a38b5-131">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="a38b5-132">Inicializar la clase con el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a38b5-132">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a38b5-133">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a38b5-133">Parameters</span></span> 
* `name` 

<span data-ttu-id="a38b5-134">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-134">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="a38b5-135">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a38b5-135">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a38b5-136">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a38b5-136">Returns</span></span>
<span data-ttu-id="a38b5-137">Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a38b5-137">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>
