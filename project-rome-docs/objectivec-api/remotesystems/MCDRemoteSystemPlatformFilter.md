---
title: MCDRemoteSystemPlatformFilter
description: Una clase utilizada para filtrar los sistemas remotos basados en la plataforma de sistema operativo que se están ejecutando.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908757"
---
# <a name="class-mcdremotesystemplatformfilter"></a><span data-ttu-id="bdd2e-104">Clase `MCDRemoteSystemPlatformFilter`</span><span class="sxs-lookup"><span data-stu-id="bdd2e-104">class `MCDRemoteSystemPlatformFilter`</span></span> 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

<span data-ttu-id="bdd2e-105">Una clase utilizada para filtrar los sistemas remotos basados en la plataforma de sistema operativo que se están ejecutando.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-105">A class used to filter remote systems based on the OS platform they are running.</span></span>

## <a name="properties"></a><span data-ttu-id="bdd2e-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="bdd2e-106">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="bdd2e-107">Plataforma</span><span class="sxs-lookup"><span data-stu-id="bdd2e-107">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="bdd2e-108">Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-108">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

## <a name="constructors"></a><span data-ttu-id="bdd2e-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="bdd2e-109">Constructors</span></span>

### <a name="filterwithplatform"></a><span data-ttu-id="bdd2e-110">filterWithPlatform</span><span class="sxs-lookup"><span data-stu-id="bdd2e-110">filterWithPlatform</span></span>
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="bdd2e-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdd2e-111">Parameters</span></span> 
* `platform` 

<span data-ttu-id="bdd2e-112">Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-112">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="bdd2e-113">Devuelve</span><span class="sxs-lookup"><span data-stu-id="bdd2e-113">Returns</span></span>
<span data-ttu-id="bdd2e-114">Devuelve un objeto MCDRemoteSystemPlatformFilter filtrado por plataforma.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-114">Returns an MCDRemoteSystemPlatformFilter object filtered by platform.</span></span>

### <a name="initwithplatform"></a><span data-ttu-id="bdd2e-115">initWithPlatform</span><span class="sxs-lookup"><span data-stu-id="bdd2e-115">initWithPlatform</span></span>
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a><span data-ttu-id="bdd2e-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bdd2e-116">Parameters</span></span> 
* `platform` 

<span data-ttu-id="bdd2e-117">Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-117">A MCDRemoteSystemPlatform value indicating the platform to filter for.</span></span>

#### <a name="returns"></a><span data-ttu-id="bdd2e-118">Devuelve</span><span class="sxs-lookup"><span data-stu-id="bdd2e-118">Returns</span></span>
<span data-ttu-id="bdd2e-119">Devuelve un objeto MCDRemoteSystemPlatformFilter inicializado con un filtro por plataforma.</span><span class="sxs-lookup"><span data-stu-id="bdd2e-119">Returns an MCDRemoteSystemPlatformFilter object initialized with a filter by platform.</span></span>