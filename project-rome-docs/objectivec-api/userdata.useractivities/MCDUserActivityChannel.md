---
title: MCDUserActivityChannel
description: Esta clase controla la adición y la consulta de las actividades del usuario para la aplicación.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b047af1da3ba79be88a53cf589c3894892b01ef4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907807"
---
# <a name="class-mcduseractivitychannel"></a>Clase `MCDUserActivityChannel`

```
@interface MCDUserActivityChannel : NSObject
```

Esta clase controla la adición y la consulta de las actividades del usuario para la aplicación.

## <a name="properties"></a>Propiedades

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

Obtiene el valor de ámbito de sincronización de datos de usuario para las actividades del usuario.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

El nombre para mostrar de la aplicación para todas las actividades.

## <a name="constructors"></a>Constructores

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

Crea una instancia de esta clase con la fuente de datos de usuario.

#### <a name="parameters"></a>Parámetros
* `userDataFeed` Los datos de usuario asociados con las actividades en este canal.

#### <a name="returns"></a>Devuelve
Devuelve una nueva instancia de esta clase.

## <a name="methods"></a>Métodos

### <a name="getorcreateuseractivityasync"></a>getOrCreateUserActivityAsync
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

Crea la actividad del usuario especificado u obtiene una referencia a él si ya existe.

#### <a name="parameters"></a>Parámetros
* `activityId` El identificador para esta actividad.
* `completionBlock` El bloque de código para ejecutar la finalización. Esto proporciona acceso a la actividad recuperada.

### <a name="deleteactivityasync"></a>deleteActivityAsync
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Elimina la actividad de usuario determinado.

#### <a name="parameters"></a>Parámetros
* `activityId` El identificador de la actividad va a eliminar.
* `completionBlock` El bloque de código para ejecutar la finalización.

### <a name="deleteallactivitiesasync"></a>deleteAllActivitiesAsync
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Elimina todas las actividades del usuario.

#### <a name="parameters"></a>Parámetros
* `completionBlock` El bloque de código para ejecutar la finalización.

### <a name="getrecentuseractivitiesasync"></a>getRecentUserActivitiesAsync
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

Obtiene un historial de las actividades recientes del usuario. 

#### <a name="parameters"></a>Parámetros
* `maxUniqueActivities` El número máximo de las actividades del usuario para recuperar.
* `completionBlock` El bloque de código para ejecutar la finalización. Esto proporciona acceso al historial de la actividad.

### <a name="getsessionhistoryitemsforuseractivityasync"></a>getSessionHistoryItemsForUserActivityAsync
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

Obtiene las entradas del historial de la sesión para una actividad determinada.

#### <a name="parameters"></a>Parámetros
* `activityId` Identificador de la actividad para obtener el historial.
* `startTime` La hora en que se considere la posibilidad de historial de la sesión.
* `completionBlock` El bloque de código para ejecutar la finalización. Esto proporciona acceso al historial de la actividad.

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a>getRecentSessionHistoryItemsForTimeRangeAsync
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

Obtiene las entradas del historial de la sesión para una actividad determinada.

#### <a name="parameters"></a>Parámetros
* `startTime` La hora en que se va a empezar a considerar el historial de la sesión.
* `endTime` La hora en que se va a terminar teniendo en cuenta el historial de la sesión.
* `maxActivities` El número máximo de las actividades del usuario para recuperar.
* `completion` El bloque de código para ejecutar la finalización.
* `completionBlock` El bloque de código para ejecutar la finalización. Esto proporciona acceso al historial de la actividad.