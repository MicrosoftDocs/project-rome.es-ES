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
# <a name="class-mcdremotesystemwatcher"></a>Clase `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

Una clase utilizada para descubrir los sistemas remotos. 

## <a name="properties"></a>Propiedades

### <a name="remotesystemadded"></a>remoteSystemAdded
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemAddedEventArgs*>* remoteSystemAdded;
```

Evento para cuando se detecta un nuevo sistema remoto.

### <a name="remotesystemupdated"></a>remoteSystemUpdated
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemUpdatedEventArgs*>* remoteSystemUpdated;
```

Evento para cuando se cambia un sistema remoto que se ha detectado anteriormente en esta sesión de detección desde proximally conectado a conectado a la nube o viceversa. 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

Evento para cuando se quita un sistema remoto. 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

Evento de cuándo ha finalizado la detección inicial de los dispositivos actualmente reconocible.  Continuará el proceso de detección para ejecutarse y provocar eventos adicionales si cambia el conjunto de sistemas remotos existentes.

### <a name="erroroccurred"></a>errorOccurred
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

Evento para cuando se produce un error durante la detección. El proceso de detección seguirá si es posible. Por ejemplo, si se produce el error con un valor de **MCDRemoteSystemWatcherError.MCDRemoteSystemWatcherErrorInternetNotAvailable**, detección articulaciones próximas puede continuar porque el error se aplica solo a cloud discovery (consulte  **MCDRemoteSystemDiscoveryType**).

## <a name="constructors"></a>Constructores

### <a name="watcher"></a>watcher
```
+ (nullable instancetype)watcher;
```

Crea e inicializa una nueva instancia de esta clase.

#### <a name="returns"></a>Devuelve 
Devuelve una nueva instancia de esta clase.

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crea e inicializa una nueva instancia de esta clase con filtros.

#### <a name="parameters"></a>Parámetros 
* `filters` 

Una matriz de filtros que desea usar en el proceso de detección de dispositivos.

#### <a name="returns"></a>Devuelve 
Devuelve un objeto MCDRemoteSystemWatcher con filtros.

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crea e inicializa una nueva instancia de esta clase con filtros.

#### <a name="parameters"></a>Parámetros 
* `filters` 

Una matriz de filtros que desea usar en el proceso de detección de dispositivos.

#### <a name="returns"></a>Devuelve 
Devuelve un objeto MCDRemoteSystemWatcher inicializado con los filtros.

## <a name="methods"></a>Métodos

### <a name="start"></a>start
`- (void)start;`

Empieza la detección de sistemas remotos.

### <a name="stop"></a>stop
`- (void)stop;` 

Detiene la detección de activa.
