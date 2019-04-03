---
title: MCDRemoteSystemConnectionRequest
description: Una clase que representa un intento para comunicarse con un dispositivo remoto específico o una aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907137"
---
# <a name="class-mcdremotesystemconnectionrequest"></a><span data-ttu-id="75110-104">Clase `MCDRemoteSystemConnectionRequest`</span><span class="sxs-lookup"><span data-stu-id="75110-104">class `MCDRemoteSystemConnectionRequest`</span></span> 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

<span data-ttu-id="75110-105">Una clase que representa un intento para comunicarse con un dispositivo remoto específico o una aplicación.</span><span class="sxs-lookup"><span data-stu-id="75110-105">A class that represents an attempt to communicate with a specific remote device or application.</span></span>

## <a name="constructors"></a><span data-ttu-id="75110-106">Constructores</span><span class="sxs-lookup"><span data-stu-id="75110-106">Constructors</span></span>

### <a name="requestwithremotesystem"></a><span data-ttu-id="75110-107">requestWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="75110-107">requestWithRemoteSystem</span></span>
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="75110-108">Inicializa el [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) con un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instancia.</span><span class="sxs-lookup"><span data-stu-id="75110-108">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="75110-109">Este constructor no se recomienda, ya que no especifica una aplicación de destino y, por tanto, es posible que en una aplicación inesperada que se ha seleccionado para atender las solicitudes que se envía al sistema.</span><span class="sxs-lookup"><span data-stu-id="75110-109">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="75110-110">Parámetros</span><span class="sxs-lookup"><span data-stu-id="75110-110">Parameters</span></span>
* `remoteSystem` 

<span data-ttu-id="75110-111">El sistema remoto como destino en esta solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="75110-111">The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="75110-112">Devuelve</span><span class="sxs-lookup"><span data-stu-id="75110-112">Returns</span></span>
<span data-ttu-id="75110-113">Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="75110-113">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="requestwithremotesystemapp"></a><span data-ttu-id="75110-114">requestWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="75110-114">requestWithRemoteSystemApp</span></span>
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="75110-115">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="75110-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="75110-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="75110-116">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="75110-117">La aplicación remota como destino en esta solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="75110-117">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="75110-118">Devuelve</span><span class="sxs-lookup"><span data-stu-id="75110-118">Returns</span></span>
<span data-ttu-id="75110-119">Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="75110-119">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystem"></a><span data-ttu-id="75110-120">initWithRemoteSystem</span><span class="sxs-lookup"><span data-stu-id="75110-120">initWithRemoteSystem</span></span>
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

<span data-ttu-id="75110-121">Inicializa el [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) con un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instancia.</span><span class="sxs-lookup"><span data-stu-id="75110-121">Initializes the [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) with a [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instance.</span></span> <span data-ttu-id="75110-122">Este constructor no se recomienda, ya que no especifica una aplicación de destino y, por tanto, es posible que en una aplicación inesperada que se ha seleccionado para atender las solicitudes que se envía al sistema.</span><span class="sxs-lookup"><span data-stu-id="75110-122">This constructor is not recommended, as it does not specify an app to target and therefore may result in an unexpected app being selected to service requests sent to the system.</span></span>

#### <a name="parameters"></a><span data-ttu-id="75110-123">Parámetros</span><span class="sxs-lookup"><span data-stu-id="75110-123">Parameters</span></span>
* <span data-ttu-id="75110-124">`remoteSystem` El sistema remoto como destino en esta solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="75110-124">`remoteSystem` The remote system to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="75110-125">Devuelve</span><span class="sxs-lookup"><span data-stu-id="75110-125">Returns</span></span>
<span data-ttu-id="75110-126">Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="75110-126">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>

### <a name="initwithremotesystemapp"></a><span data-ttu-id="75110-127">initWithRemoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="75110-127">initWithRemoteSystemApp</span></span>
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

<span data-ttu-id="75110-128">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="75110-128">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="75110-129">Parámetros</span><span class="sxs-lookup"><span data-stu-id="75110-129">Parameters</span></span>
* `remoteSystemApp` 

<span data-ttu-id="75110-130">La aplicación remota como destino en esta solicitud de conexión.</span><span class="sxs-lookup"><span data-stu-id="75110-130">The remote app to be targeted in this connection request.</span></span>

#### <a name="returns"></a><span data-ttu-id="75110-131">Devuelve</span><span class="sxs-lookup"><span data-stu-id="75110-131">Returns</span></span>
<span data-ttu-id="75110-132">Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="75110-132">Returns the initialized [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) if successful, otherwise nil.</span></span>