---
title: MCDUserNotificationChannel
description: Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, windows, retransmisión de dispositivo, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907187"
---
# <a name="class-mcdusernotificationchannel"></a>Clase `MCDUserNotificationChannel`

```
@interface MCDUserNotificationChannel : NSObject
```

Esta clase proporciona el lector de cambio de notificación que controla la recepción y la administración de las notificaciones de usuario de la aplicación. 

## <a name="properties"></a>Propiedades

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

SyncScope se utiliza para garantizar que usernotifications se incluyen en la fuente.

## <a name="constructors"></a>Constructores

### <a name="channelwithuserdatafeed"></a>channelWithUserDataFeed
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a>Parámetros

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed que se usa para inicializar esta clase.

### <a name="initwithuserdatafeed"></a>initWithUserDataFeed
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a>userDataFeed
MCDUserDataFeed que se usa para inicializar esta clase.

## <a name="methods"></a>Métodos

### <a name="createreader"></a>createReader
`- (MCDUserNotificationReader* _Nullable)createReader`

Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.

### <a name="createreaderwithoptions"></a>createReaderWithOptions
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

Crear un lector de notificación de usuario con opciones.

### <a name="createreaderwithstate"></a>createReaderWithState
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones. El lector se iniciará en el estado de seguimiento proporcionados.  

### <a name="getusernotificationasync"></a>getUserNotificationAsync
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

Reciba una notificación de usuario según su identificador.

### <a name="deleteusernotificationasync"></a>deleteUserNotificationAsync
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

Eliminar una notificación de usuario según su identificador. 