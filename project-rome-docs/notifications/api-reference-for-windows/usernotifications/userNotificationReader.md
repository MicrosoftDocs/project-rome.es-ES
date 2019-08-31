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
# <a name="class-usernotificationreader"></a><span data-ttu-id="add90-105">las`UserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="add90-105">class `UserNotificationReader`</span></span>

```C#
public sealed class UserNotificationReader : IUserNotificationReader
```

<span data-ttu-id="add90-106">Esta clase proporciona nuevas notificaciones de usuario entrantes y actualizaciones de notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="add90-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="add90-107">También proporciona acceso a la colección de notificaciones de usuario que se conservan en la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="add90-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="methods"></a><span data-ttu-id="add90-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="add90-108">Methods</span></span>

### <a name="readbatchasyncint32"></a><span data-ttu-id="add90-109">ReadBatchAsync (Int32)</span><span class="sxs-lookup"><span data-stu-id="add90-109">ReadBatchAsync(Int32)</span></span> 
<span data-ttu-id="add90-110">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="add90-110">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public IAsyncOperation<IList<UserNotification>> ReadBatchAsync(Int32 maxBatchSize)
```

## <a name="events"></a><span data-ttu-id="add90-111">Events</span><span class="sxs-lookup"><span data-stu-id="add90-111">Events</span></span>


### <a name="datachanged"></a><span data-ttu-id="add90-112">Modificado</span><span class="sxs-lookup"><span data-stu-id="add90-112">DataChanged</span></span>
<span data-ttu-id="add90-113">Se genera cuando el lector finaliza la sincronización con el servidor y tiene nuevas actualizaciones de UserNotifications o UserNotification entrantes nuevas para notificar a la aplicación.</span><span class="sxs-lookup"><span data-stu-id="add90-113">Raised when the reader completes sync with the server and has new change - new incoming UserNotifications or UserNotification updates to notify the app.</span></span> 

```C#
public event TypedEventHandler<UserNotificationReader, DataChangedEventArgs> DataChanged
```
