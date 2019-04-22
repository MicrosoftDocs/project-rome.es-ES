---
title: UserNotificationReader
description: Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, windows, la notificación de usuario, procedimientos de windows
ms.openlocfilehash: 3a929939be7e2dd9ecd9db65322efadaea3013d5
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801427"
---
# <a name="class-usernotificationreader"></a><span data-ttu-id="30051-105">Clase `UserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="30051-105">class `UserNotificationReader`</span></span>

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

<span data-ttu-id="30051-106">Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="30051-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="30051-107">También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="30051-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="methods"></a><span data-ttu-id="30051-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="30051-108">Methods</span></span>

### <a name="readbatchasyncint32"></a><span data-ttu-id="30051-109">ReadBatchAsync(Int32)</span><span class="sxs-lookup"><span data-stu-id="30051-109">ReadBatchAsync(Int32)</span></span> 
<span data-ttu-id="30051-110">Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="30051-110">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a><span data-ttu-id="30051-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="30051-111">Events</span></span>


### <a name="datachanged"></a><span data-ttu-id="30051-112">dataChanged</span><span class="sxs-lookup"><span data-stu-id="30051-112">DataChanged</span></span>
<span data-ttu-id="30051-113">Se genera cuando el lector complete la sincronización con el servidor y tiene el nuevo cambio - nueva UserNotifications entrante o UserNotification se actualiza para notificar a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="30051-113">Raised when the reader completes sync with the server and has new change - new incoming UserNotifications or UserNotification updates to notify the app.</span></span> 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
