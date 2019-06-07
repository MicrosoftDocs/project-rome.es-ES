---
title: MCDRemoteSystemWatcher
description: Una clase utilizada para descubrir los sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 8fcb0c01fd8f8c3ef1eb2d959dc9ef8af758562d
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755739"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="b2ba7-104">Clase `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="b2ba7-104">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="b2ba7-105">Una clase utilizada para descubrir los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-105">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="b2ba7-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b2ba7-106">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="b2ba7-107">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="b2ba7-107">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="b2ba7-108">Evento para cuando se detecta un nuevo sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-108">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="b2ba7-109">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="b2ba7-109">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="b2ba7-110">Evento para cuando se cambia un sistema remoto que se ha detectado anteriormente en esta sesión de detección desde proximally conectado a conectado a la nube o viceversa.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-110">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="b2ba7-111">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="b2ba7-111">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="b2ba7-112">Evento para cuando se quita un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-112">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="b2ba7-113">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="b2ba7-113">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="b2ba7-114">Evento de cuándo ha finalizado la detección inicial de los dispositivos actualmente reconocible.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-114">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="b2ba7-115">Continuará el proceso de detección para ejecutarse y provocar eventos adicionales si cambia el conjunto de sistemas remotos existentes.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-115">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="b2ba7-116">errorOccurred</span><span class="sxs-lookup"><span data-stu-id="b2ba7-116">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="b2ba7-117">Evento para cuando se produce un error durante la detección.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-117">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="b2ba7-118">El proceso de detección seguirá si es posible.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-118">The discovery process will continue if possible.</span></span> <span data-ttu-id="b2ba7-119">Por ejemplo, si se produce el error con un valor de **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, detección articulaciones próximas puede continuar porque el error se aplica solo a cloud discovery (consulte  **MCDRemoteSystemDiscoveryType**).</span><span class="sxs-lookup"><span data-stu-id="b2ba7-119">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="b2ba7-120">Constructores</span><span class="sxs-lookup"><span data-stu-id="b2ba7-120">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="b2ba7-121">watcher</span><span class="sxs-lookup"><span data-stu-id="b2ba7-121">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="b2ba7-122">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="b2ba7-123">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b2ba7-123">Returns</span></span> 
<span data-ttu-id="b2ba7-124">Devuelve una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-124">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="b2ba7-125">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="b2ba7-125">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="b2ba7-126">Crea e inicializa una nueva instancia de esta clase con filtros.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-126">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b2ba7-127">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b2ba7-127">Parameters</span></span> 
* `filters` 

<span data-ttu-id="b2ba7-128">Una matriz de filtros que desea usar en el proceso de detección de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-128">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="b2ba7-129">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b2ba7-129">Returns</span></span> 
<span data-ttu-id="b2ba7-130">Devuelve un objeto MCDRemoteSystemWatcher con filtros.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-130">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="b2ba7-131">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="b2ba7-131">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="b2ba7-132">Crea e inicializa una nueva instancia de esta clase con filtros.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-132">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b2ba7-133">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b2ba7-133">Parameters</span></span> 
* `filters` 

<span data-ttu-id="b2ba7-134">Una matriz de filtros que desea usar en el proceso de detección de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-134">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="b2ba7-135">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b2ba7-135">Returns</span></span> 
<span data-ttu-id="b2ba7-136">Devuelve un objeto MCDRemoteSystemWatcher inicializado con los filtros.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-136">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="b2ba7-137">Métodos</span><span class="sxs-lookup"><span data-stu-id="b2ba7-137">Methods</span></span>

### <a name="start"></a><span data-ttu-id="b2ba7-138">start</span><span class="sxs-lookup"><span data-stu-id="b2ba7-138">start</span></span>
`- (void)start;`

<span data-ttu-id="b2ba7-139">Empieza la detección de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-139">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="b2ba7-140">stop</span><span class="sxs-lookup"><span data-stu-id="b2ba7-140">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="b2ba7-141">Detiene la detección de activa.</span><span class="sxs-lookup"><span data-stu-id="b2ba7-141">Stops the active discovery.</span></span>
