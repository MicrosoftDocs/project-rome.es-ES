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
# <a name="class-mcdremotesystemwatcher"></a>las `MCDRemoteSystemWatcher`

```
@interface MCDRemoteSystemWatcher : NSObject
```

Clase usada para detectar sistemas remotos. 

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

Evento para cuando un sistema remoto detectado anteriormente en esta sesión de detección cambia de proximally conectado a la nube conectada o inversa. 

### <a name="remotesystemremoved"></a>remoteSystemRemoved
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*, MCDRemoteSystemRemovedEventArgs*>* remoteSystemRemoved;
```

Evento para cuando se quita un sistema remoto. 

### <a name="enumerationcompleted"></a>enumerationCompleted
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemEnumerationCompletedEventArgs*>* enumerationCompleted;
```

Evento para el momento en que ha finalizado la detección inicial de dispositivos que se pueden detectar actualmente.  El proceso de detección continuará ejecutándose y generará eventos adicionales si cambia el conjunto de sistemas remotos existentes.

### <a name="erroroccurred"></a>errorOccurred
```
@property(nonatomic, readonly, nonnull) MCDEvent<MCDRemoteSystemWatcher*,  MCDRemoteSystemWatcherErrorOccurredEventArgs*>* errorOccurred;
```

Evento para cuando se produce un error durante la detección. El proceso de detección continuará si es posible. Por ejemplo, si el error se produce con un valor de **MCDRemoteSystemWatcherError. MCDRemoteSystemWatcherErrorInternetNotAvailable**, la detección de proximal puede continuar porque el error se aplica solo a Cloud Discovery (consulte **MCDRemoteSystemDiscoveryType**).

## <a name="constructors"></a>Constructores

### <a name="watcher"></a>monitor
```
+ (nullable instancetype)watcher;
```

Crea e inicializa una nueva instancia de esta clase.

#### <a name="returns"></a>Devoluciones 
Devuelve una nueva instancia de esta clase.

### <a name="watcherwithfilters"></a>watcherWithFilters
```
+ (nullable instancetype)watcherWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crea e inicializa una nueva instancia de esta clase con filtros.

#### <a name="parameters"></a>Parámetros 
* `filters` 

Matriz de filtros que se va a usar en el proceso de detección de dispositivos.

#### <a name="returns"></a>Devoluciones 
Devuelve un objeto MCDRemoteSystemWatcher con filtros.

### <a name="initwithfilters"></a>initWithFilters
```
- (nullable instancetype)initWithFilters:(nonnull NSArray<NSObject<MCDRemoteSystemFilter>*>*)filters;
```

Crea e inicializa una nueva instancia de esta clase con filtros.

#### <a name="parameters"></a>Parámetros 
* `filters` 

Matriz de filtros que se va a usar en el proceso de detección de dispositivos.

#### <a name="returns"></a>Devoluciones 
Devuelve un objeto MCDRemoteSystemWatcher inicializado con filtros.

## <a name="methods"></a>Métodos

### <a name="start"></a>start
`- (void)start;`

Comienza a detectar sistemas remotos.

### <a name="stop"></a>stop
`- (void)stop;` 

Detiene la detección activa.
