---
title: MCDUserNotificationReader
description: Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, windows, retransmisión de dispositivo, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909027"
---
# <a name="class-mcdusernotificationreader"></a>Clase `MCDUserNotificationReader`

```
@interface MCDUserNotificationReader : NSObject
```

Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.  

## <a name="properties"></a>Propiedades

### <a name="serializedstate"></a>serializedState
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

Devuelve el estado actual del lector de cambio. Puede usarse para construir un nuevo lector desde el mismo estado.
Según el último lote completado de notificación cambios (o el estado inicial, si no se han completado correctamente).

### <a name="datachanged"></a>dataChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

Cambia la suscripción de eventos para MCDUserNotificationReader.

## <a name="methods"></a>Métodos

### <a name="readbatchasyncwithmaxsize"></a>readBatchAsyncWithMaxSize
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

Leer los cambios de notificación incluidos nuevas notificaciones entrantes y las actualizaciones en las notificaciones existentes en lote.