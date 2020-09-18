---
title: MCDUserNotificationChannel
description: Obtenga información sobre la clase MCDUserNotificationChannel. Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, Windows, retransmisión de dispositivos, iOS y procedimientos de iPhone
ms.openlocfilehash: dc7e451494014cdcdebd056b00e57cfdf5f0757f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760879"
---
# <a name="class-mcdusernotificationchannel"></a>las `MCDUserNotificationChannel`

```
@interface MCDUserNotificationChannel : NSObject
```

Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación. 

## <a name="properties"></a>Propiedades

### <a name="syncscope"></a>syncScope
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

SyncScope usado para asegurarse de que UserNotifications se incluyen en la fuente.

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

Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.

### <a name="createreaderwithoptions"></a>createReaderWithOptions
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

Cree un lector de notificaciones de usuario con opciones.

### <a name="createreaderwithstate"></a>createReaderWithState
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones. El lector se iniciará en el estado de seguimiento proporcionado.  

### <a name="getusernotificationasync"></a>getUserNotificationAsync
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

Obtiene una notificación de usuario basada en su identificador.

### <a name="deleteusernotificationasync"></a>deleteUserNotificationAsync
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

Elimina una notificación de usuario en función de su identificador. 