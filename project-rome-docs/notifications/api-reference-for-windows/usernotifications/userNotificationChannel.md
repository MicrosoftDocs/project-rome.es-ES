---
title: UserNotificationChannel
description: Obtenga información sobre la clase UserNotificationChannel. Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, Windows, notificaciones de grafos, ventanas de procedimientos
ms.openlocfilehash: f5347878da2d82035db1dbb63cca015180f66a34
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760939"
---
# <a name="class-usernotificationchannel"></a>las `UserNotificationChannel`

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación. 

## <a name="methods"></a>Métodos

### <a name="createreader"></a>CreateReader () 
Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a>CreateReader (UserNotificationReaderOptions) 
Crear un lector de notificaciones de usuario con opciones 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a>CreateReaderWithState (cadena) 
Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones. El lector se iniciará en el estado de seguimiento proporcionado. 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a>GetUserNotificationAsync (cadena)
Obtiene una notificación de usuario basada en su identificador. 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a>DeleteUserNotificationAsync (cadena)
Obtiene una notificación de usuario basada en su identificador. 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a>SyncScope()
Obtiene el ámbito de sincronización de este canal de notificación de usuario.
```C#
public static IUserDataFeedSyncScope SyncScope()
```