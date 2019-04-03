---
title: UserNotificationReader
description: Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, windows, la notificación de usuario, procedimientos de windows
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907377"
---
# <a name="class-usernotificationreader"></a>Clase `UserNotificationReader`

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.  

## <a name="methods"></a>Métodos

### <a name="readbatchasyncint32"></a>ReadBatchAsync(Int32) 
Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a>Eventos


### <a name="datachanged"></a>dataChanged
Se genera cuando el lector complete la sincronización con el servidor y tiene el nuevo cambio - nueva UserNotifications entrante o UserNotification se actualiza para notificar a la aplicación. 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
