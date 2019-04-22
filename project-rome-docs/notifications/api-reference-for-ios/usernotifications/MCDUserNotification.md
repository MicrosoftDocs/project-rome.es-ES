---
title: MCDUserNotification
description: Esta clase representa una notificación de usuario publicado por el servidor de aplicaciones a través de las notificaciones de Graph y recibidos por el cliente de aplicación.
keywords: Microsoft, ios, notificaciones de graph, ios procedimientos, procedimientos iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907897"
---
# <a name="class-mcdusernotification"></a>Clase `MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


Esta clase representa una instancia de la notificación de usuario único. Una notificación de usuario creada y publicada por el servidor de aplicaciones dirigido a un usuario, que se distribuye a todos los puntos de conexión de dispositivo del mismo usuario registrado.
Una notificación de usuario, una vez recibida por el cliente de aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación local de la plataforma correspondiente.

## <a name="properties"></a>Propiedades

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Obtiene el programador especifica único identificador para esta notificación de usuario.

### <a name="groupid"></a>groupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;` Obtiene el programador especifica el identificador de grupo para esta notificación de usuario.

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Obtiene la hora de expiración para esta notificación de usuario.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Obtiene el estado de la notificación de usuario.

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Obtiene la hora en que se realizó el cambio.

### <a name="priority"></a>priority
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Obtiene el programador especifica la prioridad para esta notificación de usuario.

### <a name="content"></a>content
`@property(nonatomic, readonly, nonnull) NSString* content;` Obtiene la carga de contenido para esta notificación, que es definido por el desarrollador de datos arbitrarios.

###  <a name="readstate"></a>readState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Obtiene el valor del estado de lectura para esta notificación de usuario que indica que la notificación es leído o no.

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Obtiene el valor del estado de acción de usuario para una notificación de usuario determinar si la notificación no es interactuada, descartar, activada o posponer. 

## <a name="methods"></a>Métodos

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

Debe llamarse al publicar los cambios de notificación de usuario. Este método debe llamarse siempre que la aplicación modifica una propiedad de la UserNotification actualizable.

#### <a name="parameters"></a>Parámetros
* `completion` El bloque de código para ejecutar la finalización.
