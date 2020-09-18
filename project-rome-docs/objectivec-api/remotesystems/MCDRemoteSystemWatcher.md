---
title: MCDRemoteSystemWatcher
description: Obtenga información sobre la clase MCDRemoteSystemWatcher y sus propiedades. Esta clase se usa para detectar sistemas remotos.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: c000d5392fe6498c248b915ae4e26e49ad1d42db
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760649"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="ca27d-105">las `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="ca27d-105">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="ca27d-106">Clase usada para detectar sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="ca27d-106">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="ca27d-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ca27d-107">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="ca27d-108">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="ca27d-108">remoteSystemAdded</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

<span data-ttu-id="ca27d-109">Evento para cuando se detecta un nuevo sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="ca27d-109">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="ca27d-110">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="ca27d-110">remoteSystemUpdated</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

<span data-ttu-id="ca27d-111">Evento para cuando un sistema remoto detectado anteriormente en esta sesión de detección cambia de proximally conectado a la nube conectada o inversa.</span><span class="sxs-lookup"><span data-stu-id="ca27d-111">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="ca27d-112">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="ca27d-112">remoteSystemRemoved</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

<span data-ttu-id="ca27d-113">Evento para cuando se quita un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="ca27d-113">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="ca27d-114">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="ca27d-114">enumerationCompleted</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

<span data-ttu-id="ca27d-115">Evento para el momento en que ha finalizado la detección inicial de dispositivos que se pueden detectar actualmente.</span><span class="sxs-lookup"><span data-stu-id="ca27d-115">Event for when the initial discovery of currently-discoverable devices has finished.</span></span>  <span data-ttu-id="ca27d-116">El proceso de detección continuará ejecutándose y generará eventos adicionales si cambia el conjunto de sistemas remotos existentes.</span><span class="sxs-lookup"><span data-stu-id="ca27d-116">The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.</span></span>

### <a name="erroroccurred"></a><span data-ttu-id="ca27d-117">errorOccurred</span><span class="sxs-lookup"><span data-stu-id="ca27d-117">errorOccurred</span></span>
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

<span data-ttu-id="ca27d-118">Evento para cuando se produce un error durante la detección.</span><span class="sxs-lookup"><span data-stu-id="ca27d-118">Event for when an error occurs during discovery.</span></span> <span data-ttu-id="ca27d-119">El proceso de detección continuará si es posible.</span><span class="sxs-lookup"><span data-stu-id="ca27d-119">The discovery process will continue if possible.</span></span> <span data-ttu-id="ca27d-120">Por ejemplo, si el error se produce con un valor de **MCDRemoteSystemWatcherError. MCDRemoteSystemWatcherErrorInternetNotAvailable**, la detección de proximal puede continuar porque el error se aplica solo a Cloud Discovery (consulte **MCDRemoteSystemDiscoveryType**).</span><span class="sxs-lookup"><span data-stu-id="ca27d-120">For example, if the error occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).</span></span>

## <a name="constructors"></a><span data-ttu-id="ca27d-121">Constructores</span><span class="sxs-lookup"><span data-stu-id="ca27d-121">Constructors</span></span>

### <a name="watcher"></a><span data-ttu-id="ca27d-122">monitor</span><span class="sxs-lookup"><span data-stu-id="ca27d-122">watcher</span></span>
```
+ (nullable instancetype)watcher;
```

<span data-ttu-id="ca27d-123">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ca27d-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="ca27d-124">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="ca27d-124">Returns</span></span> 
<span data-ttu-id="ca27d-125">Devuelve una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ca27d-125">Returns a new instance of this class.</span></span>

### <a name="watcherwithfilters"></a><span data-ttu-id="ca27d-126">watcherWithFilters</span><span class="sxs-lookup"><span data-stu-id="ca27d-126">watcherWithFilters</span></span>
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="ca27d-127">Crea e inicializa una nueva instancia de esta clase con filtros.</span><span class="sxs-lookup"><span data-stu-id="ca27d-127">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ca27d-128">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ca27d-128">Parameters</span></span> 
* `filters` 

<span data-ttu-id="ca27d-129">Matriz de filtros que se va a usar en el proceso de detección de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ca27d-129">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="ca27d-130">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="ca27d-130">Returns</span></span> 
<span data-ttu-id="ca27d-131">Devuelve un objeto MCDRemoteSystemWatcher con filtros.</span><span class="sxs-lookup"><span data-stu-id="ca27d-131">Returns an MCDRemoteSystemWatcher object with filters.</span></span>

### <a name="initwithfilters"></a><span data-ttu-id="ca27d-132">initWithFilters</span><span class="sxs-lookup"><span data-stu-id="ca27d-132">initWithFilters</span></span>
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

<span data-ttu-id="ca27d-133">Crea e inicializa una nueva instancia de esta clase con filtros.</span><span class="sxs-lookup"><span data-stu-id="ca27d-133">Creates and initializes a new instance of this class with filters.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ca27d-134">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ca27d-134">Parameters</span></span> 
* `filters` 

<span data-ttu-id="ca27d-135">Matriz de filtros que se va a usar en el proceso de detección de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="ca27d-135">An array of filters to use in the device discovery process.</span></span>

#### <a name="returns"></a><span data-ttu-id="ca27d-136">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="ca27d-136">Returns</span></span> 
<span data-ttu-id="ca27d-137">Devuelve un objeto MCDRemoteSystemWatcher inicializado con filtros.</span><span class="sxs-lookup"><span data-stu-id="ca27d-137">Returns an MCDRemoteSystemWatcher object initialized with filters.</span></span>

## <a name="methods"></a><span data-ttu-id="ca27d-138">Métodos</span><span class="sxs-lookup"><span data-stu-id="ca27d-138">Methods</span></span>

### <a name="start"></a><span data-ttu-id="ca27d-139">start</span><span class="sxs-lookup"><span data-stu-id="ca27d-139">start</span></span>
`- (void)start;`

<span data-ttu-id="ca27d-140">Comienza a detectar sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="ca27d-140">Begins discovering remote systems.</span></span>

### <a name="stop"></a><span data-ttu-id="ca27d-141">stop</span><span class="sxs-lookup"><span data-stu-id="ca27d-141">stop</span></span>
`- (void)stop;` 

<span data-ttu-id="ca27d-142">Detiene la detección activa.</span><span class="sxs-lookup"><span data-stu-id="ca27d-142">Stops the active discovery.</span></span>
