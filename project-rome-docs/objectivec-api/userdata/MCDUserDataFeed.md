---
title: MCDUserDataFeed
description: Esta clase es responsable de sincronizar los datos específicos del usuario con la plataforma de dispositivos conectados de back-end.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: cd90c266c3c0293996a4f23059719224579404ff
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/13/2019
ms.locfileid: "67132240"
---
# <a name="class-mcduserdatafeed"></a>Clase `MCDUserDataFeed`

```
@interface MCDUserDataFeed : NSObject
```

Esta clase es responsable de sincronizar los datos específicos del usuario con la plataforma de dispositivos conectados de back-end. Los datos que se sincronizan dependen de cuál **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** se encuentran las instancias.

## <a name="properties"></a>Propiedades

### <a name="syncstatus"></a>syncStatus
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

Describe el estado actual de la sincronización de datos de usuario.

### <a name="syncstatuschanged"></a>syncStatusChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

Evento para cuando se cambia el estado de sincronización de la UserDataFeed.

### <a name="daystosync"></a>daysToSync
`@property(nonatomic, readwrite) NSInteger daysToSync;`

El número de días de datos en sincronizarse, lo que deberían ser menos de 30.  Representa el valor predeterminado, que se determinará por el servidor.

## <a name="constructors"></a>Constructores

### <a name="getforaccount"></a>getForAccount
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

Crea e inicializa una nueva instancia de esta clase con una cuenta de usuario, instancia de la plataforma y el identificador de aplicación multiplataforma.

#### <a name="parameters"></a>Parámetros
* `userAccount` 

La cuenta de usuario que se asociará estos datos.

* `platform` 

El **MCDPlatform** instancia que se ha inicializado para la funcionalidad de dispositivos conectados a esta aplicación.

* `activitySourceHost` 

El identificador de aplicación multiplataforma. Este valor se recupera mediante el registro del panel para desarrolladores de Microsoft.

#### <a name="returns"></a>Devuelve
Devuelve una instancia de esta clase.

## <a name="methods"></a>Métodos

> [!WARNING]
> Esta función está en desuso, 'subscribeToSyncScopesWithResultAsync' en su lugar.

### <a name="subscribetosyncscopesasync"></a>subscribeToSyncScopesAsync
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback  __attribute__((deprecated("Use subscribeToSyncScopesWithResultAsync instead")));`

Agrega **MCDUserDataFeedSyncScope** instancias para este MCDUserDataFeed.  Este MCDUserDataFeed está sincronizado según la **MCDUserDataFeedSyncScope** instancias especificadas.

#### <a name="parameters"></a>Parámetros

* `syncScopes` Una matriz de **MCDSyncScope** instancias.

* `callback`

El resultado de la devolución de llamada indica si la suscripción es correcta, o no.

### <a name="subscribetosyncscopeswithresultasync"></a>subscribeToSyncScopesWithResultAsync
`- (void)subscribeToSyncScopesWithResultAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(MCDUserDataFeedSubscribeResult* _Nullable, NSError* _Nullable)) callback;`

Agrega **MCDUserDataFeedSyncScope** instancias para este MCDUserDataFeed.  Este MCDUserDataFeed está sincronizado según la **MCDUserDataFeedSyncScope** instancias especificadas.

#### <a name="parameters"></a>Parámetros

* `syncScopes` Una matriz de **MCDSyncScope** instancias.

* `callback`

El resultado de la devolución de llamada indica si la suscripción es correcta, o no.

### <a name="startsync"></a>startSync
`- (void)startSync;`

Inicia el proceso de sincronización con la plataforma de dispositivos conectados. Durante esta operación, el **syncStatus** se actualizará la propiedad y los eventos de cambio, se generará.