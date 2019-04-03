---
title: MCDAppServiceInfo
description: Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907117"
---
# <a name="class-mcdappserviceinfo"></a><span data-ttu-id="a996c-104">Clase `MCDAppServiceInfo`</span><span class="sxs-lookup"><span data-stu-id="a996c-104">class `MCDAppServiceInfo`</span></span> 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

<span data-ttu-id="a996c-105">Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="a996c-105">This class describes an app service that belongs to a remote device or application.</span></span>

## <a name="properties"></a><span data-ttu-id="a996c-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a996c-106">Properties</span></span>

### <a name="name"></a><span data-ttu-id="a996c-107">NAME</span><span class="sxs-lookup"><span data-stu-id="a996c-107">name</span></span>
`@property(nonatomic, readonly, nullable) NSString* name;`

<span data-ttu-id="a996c-108">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-108">The name of the app service being described.</span></span>

### <a name="packageid"></a><span data-ttu-id="a996c-109">packageId</span><span class="sxs-lookup"><span data-stu-id="a996c-109">packageId</span></span>
`@property(nonatomic, readonly, nullable) NSString* packageId;`

<span data-ttu-id="a996c-110">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-110">The package ID of the app service being described.</span></span>

## <a name="constructors"></a><span data-ttu-id="a996c-111">Constructores</span><span class="sxs-lookup"><span data-stu-id="a996c-111">Constructors</span></span>

### <a name="infowithname"></a><span data-ttu-id="a996c-112">infoWithName</span><span class="sxs-lookup"><span data-stu-id="a996c-112">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

<span data-ttu-id="a996c-113">Inicializar la clase con información y el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a996c-113">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a996c-114">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a996c-114">Parameters</span></span> 
* `name` 

<span data-ttu-id="a996c-115">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-115">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a996c-116">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a996c-116">Returns</span></span>
<span data-ttu-id="a996c-117">Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a996c-117">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="a996c-118">initWithName</span><span class="sxs-lookup"><span data-stu-id="a996c-118">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

<span data-ttu-id="a996c-119">Inicializar la clase con el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a996c-119">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a996c-120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a996c-120">Parameters</span></span> 
* `name` 

<span data-ttu-id="a996c-121">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-121">The name of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a996c-122">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a996c-122">Returns</span></span>
<span data-ttu-id="a996c-123">Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a996c-123">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>

### <a name="infowithname"></a><span data-ttu-id="a996c-124">infoWithName</span><span class="sxs-lookup"><span data-stu-id="a996c-124">infoWithName</span></span>
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="a996c-125">Inicializar la clase con información y el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a996c-125">Initialize the class with information and name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a996c-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a996c-126">Parameters</span></span> 
* `name` 

<span data-ttu-id="a996c-127">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-127">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="a996c-128">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-128">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a996c-129">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a996c-129">Returns</span></span>
<span data-ttu-id="a996c-130">Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a996c-130">Returns an MCDAppServiceInfo object containing the provided name.</span></span>

### <a name="initwithname"></a><span data-ttu-id="a996c-131">initWithName</span><span class="sxs-lookup"><span data-stu-id="a996c-131">initWithName</span></span>
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

<span data-ttu-id="a996c-132">Inicializar la clase con el nombre del servicio en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a996c-132">Initialize the class with the name of the app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a996c-133">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a996c-133">Parameters</span></span> 
* `name` 

<span data-ttu-id="a996c-134">El nombre del servicio en la aplicación que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-134">The name of the app service being described.</span></span>

* `packageId` 

<span data-ttu-id="a996c-135">El identificador del paquete de app service que se describe.</span><span class="sxs-lookup"><span data-stu-id="a996c-135">The package ID of the app service being described.</span></span>

#### <a name="returns"></a><span data-ttu-id="a996c-136">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a996c-136">Returns</span></span>
<span data-ttu-id="a996c-137">Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a996c-137">Returns an MCDAppServiceInfo object initialized with the provided name.</span></span>
