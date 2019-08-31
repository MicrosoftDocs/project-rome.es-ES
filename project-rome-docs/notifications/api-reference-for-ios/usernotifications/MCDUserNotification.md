---
title: MCDUserNotification
description: Esta clase representa una notificación de usuario publicada por el servidor de aplicaciones a través de notificaciones de grafos y recibida por el cliente de la aplicación.
keywords: Microsoft, iOS, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907897"
---
# <a name="class-mcdusernotification"></a>las`MCDUserNotification`

```
@interface MCDUserNotification : NSObject
```


Esta clase representa una instancia de notificación de un solo usuario. El servidor de aplicaciones que se dirige a un usuario crea y publica una notificación de usuario, que se distribuye a todos los puntos de conexión del dispositivo del mismo usuario que ha iniciado sesión.
Una notificación de usuario, una vez recibida por el cliente de la aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación locales de la plataforma correspondiente.

## <a name="properties"></a>Propiedades

### <a name="notificationid"></a>notificationId
`@property(nonatomic, readonly, nonnull) NSString* notificationId;`Obtiene el identificador único especificado por el desarrollador para esta notificación de usuario.

### <a name="groupid"></a>groupId
`@property(nonatomic, readonly, nonnull) NSString* groupId;`Obtiene el identificador de grupo especificado por el desarrollador para esta notificación de usuario.

### <a name="expirationtime"></a>expirationTime
`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`Obtiene la hora de expiración de esta notificación de usuario.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDUserNotificationStatus status;`Obtiene el estado de la notificación del usuario.

### <a name="changetime"></a>changeTime
`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`Obtiene la hora a la que se realizó el cambio.

### <a name="priority"></a>prioridad
`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`Obtiene la prioridad especificada por el desarrollador para esta notificación de usuario.

### <a name="content"></a>contenido
`@property(nonatomic, readonly, nonnull) NSString* content;`Obtiene la carga de contenido para esta notificación, que es datos arbitrarios definidos por el desarrollador.

###  <a name="readstate"></a>readState
`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`Obtiene el valor del estado de lectura de esta notificación de usuario que indica que la notificación se ha leído o no se ha leído.

### <a name="useractionstate"></a>userActionState
`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`Obtiene el valor del estado de acción del usuario para una notificación de usuario para determinar si la notificación no se ha interactuado, descartado, activado o pospuesto. 

## <a name="methods"></a>Métodos

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

Se debe llamar a este método al publicar cambios en las notificaciones de usuario. Se debe llamar a este método siempre que la aplicación modifique una propiedad actualizable de UserNotification.

#### <a name="parameters"></a>Parámetros
* `completion`Bloque de código que se va a ejecutar cuando se complete.
