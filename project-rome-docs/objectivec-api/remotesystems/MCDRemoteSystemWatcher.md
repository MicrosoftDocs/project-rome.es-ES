---
title: MCDRemoteSystemWatcher
description: Una clase utilizada para descubrir los sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 88bb52465de165224c62270e0630dfb72f47b31f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908837"
---
# <a name="class-mcdremotesystemwatcher"></a><span data-ttu-id="06de4-104">Clase `MCDRemoteSystemWatcher`</span><span class="sxs-lookup"><span data-stu-id="06de4-104">class `MCDRemoteSystemWatcher`</span></span>

```
@interface MCDRemoteSystemWatcher : NSObject
```

<span data-ttu-id="06de4-105">Una clase utilizada para descubrir los sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="06de4-105">A class used to discover remote systems.</span></span> 

## <a name="properties"></a><span data-ttu-id="06de4-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="06de4-106">Properties</span></span>

### <a name="remotesystemadded"></a><span data-ttu-id="06de4-107">remoteSystemAdded</span><span class="sxs-lookup"><span data-stu-id="06de4-107">remoteSystemAdded</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;`

<span data-ttu-id="06de4-108">Evento para cuando se detecta un nuevo sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="06de4-108">Event for when a new remote system is discovered.</span></span>

### <a name="remotesystemupdated"></a><span data-ttu-id="06de4-109">remoteSystemUpdated</span><span class="sxs-lookup"><span data-stu-id="06de4-109">remoteSystemUpdated</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;`

<span data-ttu-id="06de4-110">Evento para cuando se cambia un sistema remoto que se ha detectado anteriormente en esta sesión de detección desde proximally conectado a conectado a la nube o viceversa.</span><span class="sxs-lookup"><span data-stu-id="06de4-110">Event for when a remote system that was previously discovered in this discovery session changes from proximally connected to cloud connected, or the reverse.</span></span> 

### <a name="remotesystemremoved"></a><span data-ttu-id="06de4-111">remoteSystemRemoved</span><span class="sxs-lookup"><span data-stu-id="06de4-111">remoteSystemRemoved</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;`

<span data-ttu-id="06de4-112">Evento para cuando se quita un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="06de4-112">Event for when a remote system is removed.</span></span> 

### <a name="enumerationcompleted"></a><span data-ttu-id="06de4-113">enumerationCompleted</span><span class="sxs-lookup"><span data-stu-id="06de4-113">enumerationCompleted</span></span>
<span data-ttu-id="06de4-114">\`\`\`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher *, MCDRemoteSystemEnumerationCompletedEventArgs*>\* enumerationCompleted;</span><span class="sxs-lookup"><span data-stu-id="06de4-114">\`\`\`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher *, MCDRemoteSystemEnumerationCompletedEventArgs*>\* enumerationCompleted;</span></span>
```

Event for when the initial discovery of currently-discoverable devices has finished.  The discovery process will continue to run and will raise additional events if the set of existing remote systems changes.

### errorOccurred
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;`

Event for when an error occurs during discovery. The discovery process will continue if possible. For example, if the error
occurs with a value of **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, proximal discovery
may continue because the error applies only to cloud discovery (see **MCDRemoteSystemDiscoveryType**).

## Constructors

### watcher
`+ (nullable instancetype)watcher;`

Creates and initializes a new instance of this class.

#### Returns 
Returns a new instance of this class.

### watcherWithFilters
`+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;`

Creates and initializes a new instance of this class with filters.

#### Parameters 
* `filters` 

An array of filters to use in the device discovery process.

#### Returns 
Returns an MCDRemoteSystemWatcher object with filters.

### initWithFilters
`- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;`

Creates and initializes a new instance of this class with filters.

#### Parameters 
* `filters` 

An array of filters to use in the device discovery process.

#### Returns 
Returns an MCDRemoteSystemWatcher object initialized with filters.

## Methods

### start
`- (void)start;`

Begins discovering remote systems.

### stop
`- (void)stop;` 

Stops the active discovery.