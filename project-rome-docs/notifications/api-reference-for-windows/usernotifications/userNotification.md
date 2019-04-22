---
title: UserNotification
description: Esta clase representa una notificación de usuario publicado por el servidor de aplicaciones a través de las notificaciones de Graph y recibidos por el cliente de aplicación.
keywords: Microsoft, windows, las notificaciones de graph, procedimientos de windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801597"
---
# <a name="class-usernotification"></a>Clase `UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

Esta clase representa una instancia de la notificación de usuario único. Una notificación de usuario creada y publicada por el servidor de aplicaciones dirigido a un usuario, que se distribuye a todos los puntos de conexión de dispositivo del mismo usuario registrado.
Una notificación de usuario, una vez recibida por el cliente de aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación local de la plataforma correspondiente.

## <a name="properties"></a>Propiedades

|Nombre | Descripción |
|:-- |:-- |
|Id |Obtiene el programador especifica único identificador para esta notificación de usuario.|
|   GroupId |Obtiene el programador especifica el identificador de grupo para esta notificación de usuario.| 
|   ExpirationTime |Obtiene la hora de expiración para esta notificación de usuario.| 
|   Prioridad|Obtiene el programador especifica la prioridad para esta notificación de usuario.| 
|   Contenido|Obtiene la carga de contenido para esta notificación, que es definido por el desarrollador de datos arbitrarios.| 
|   ReadState|Obtiene el valor del estado de lectura para esta notificación de usuario que indica que la notificación es leído o no.| 
|   UserActionState|Obtiene el valor del estado de acción de usuario para una notificación de usuario determinar si la notificación no es interactuada, descartar, activada o posponer.| 


## <a name="methods"></a>Métodos

### <a name="saveasync"></a>SaveAsync() 
Debe llamarse al publicar los cambios de notificación de usuario. Este método debe llamarse siempre que la aplicación modifica una propiedad de la UserNotification actualizable.
```C#
public IAsyncOperation SaveAsync()
```

