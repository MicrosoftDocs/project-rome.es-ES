---
title: MCDUserNotificationReader
description: Esta clase proporciona nuevas notificaciones de usuario entrantes y actualizaciones de notificaciones de usuario. También proporciona acceso a la colección de notificaciones de usuario que se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, Windows, retransmisión de dispositivos, iOS y procedimientos de iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800737"
---
# <a name="class-mcdusernotificationreader"></a>las`MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

Esta clase proporciona nuevas notificaciones de usuario entrantes y actualizaciones de notificaciones de usuario. También proporciona acceso a la colección de notificaciones de usuario que se conservan en la plataforma de dispositivos conectados.  

## <a name="properties"></a>Propiedades

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

Devuelve el estado actual del lector de cambios. Se puede usar para construir un nuevo lector a partir del mismo estado.
Según el último lote completado de cambios de notificación (o el estado inicial, si no se ha completado correctamente).

### <a name="datachanged"></a>Modificado
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

La suscripción de eventos para MCDUserNotificationReader ha cambiado.

## <a name="methods"></a>Métodos

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

Los cambios en las notificaciones de lectura incluyen nuevas notificaciones entrantes y actualizaciones en las notificaciones existentes en batch.