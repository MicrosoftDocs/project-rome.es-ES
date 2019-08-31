---
title: UserNotification
description: Esta clase representa una notificación de usuario publicada por el servidor de aplicaciones a través de notificaciones de grafos y recibida por el cliente de la aplicación.
keywords: Microsoft, Windows, notificaciones de grafos, ventanas de procedimientos
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801597"
---
# <a name="class-usernotification"></a>las`UserNotification`

```C#
public sealed class UserNotification : IUserNotification
```

Esta clase representa una instancia de notificación de un solo usuario. El servidor de aplicaciones que se dirige a un usuario crea y publica una notificación de usuario, que se distribuye a todos los puntos de conexión del dispositivo del mismo usuario que ha iniciado sesión.
Una notificación de usuario, una vez recibida por el cliente de la aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación locales de la plataforma correspondiente.

## <a name="properties"></a>Propiedades

|NOMBRE | Descripción |
|:-- |:-- |
|Id |Obtiene el identificador único especificado por el desarrollador para esta notificación de usuario.|
|   GroupId |Obtiene el identificador de grupo especificado por el desarrollador para esta notificación de usuario.| 
|   ExpirationTime |Obtiene la hora de expiración de esta notificación de usuario.| 
|   Prioridad|Obtiene la prioridad especificada por el desarrollador para esta notificación de usuario.| 
|   Contenido|Obtiene la carga de contenido para esta notificación, que es datos arbitrarios definidos por el desarrollador.| 
|   ReadState|Obtiene el valor del estado de lectura de esta notificación de usuario que indica que la notificación se ha leído o no se ha leído.| 
|   UserActionState|Obtiene el valor del estado de acción del usuario para una notificación de usuario para determinar si la notificación no se ha interactuado, descartado, activado o pospuesto.| 


## <a name="methods"></a>Métodos

### <a name="saveasync"></a>SaveAsync () 
Se debe llamar a este método al publicar cambios en las notificaciones de usuario. Se debe llamar a este método siempre que la aplicación modifique una propiedad actualizable de UserNotification.
```C#
public IAsyncOperation SaveAsync()
```

