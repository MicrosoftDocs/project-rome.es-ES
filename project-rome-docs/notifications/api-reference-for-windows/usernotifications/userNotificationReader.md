---
title: UserNotificationReader
description: Esta clase proporciona nuevas notificaciones de usuario entrantes y actualizaciones de notificaciones de usuario. También proporciona acceso a la colección de notificaciones de usuario que se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, Windows, notificación de usuario, ventanas de procedimientos
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801427"
---
# <a name="class-usernotificationreader"></a>las`UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

Esta clase proporciona nuevas notificaciones de usuario entrantes y actualizaciones de notificaciones de usuario. También proporciona acceso a la colección de notificaciones de usuario que se conservan en la plataforma de dispositivos conectados.  

## <a name="methods"></a>Métodos

### <a name="readbatchasyncint32"></a>ReadBatchAsync (Int32) 
Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>Events


### <a name="datachanged"></a>Modificado
Se genera cuando el lector finaliza la sincronización con el servidor y tiene nuevas actualizaciones de UserNotifications o UserNotification entrantes nuevas para notificar a la aplicación. 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
