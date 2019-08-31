---
title: UserNotificationChannel
description: Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, Windows, notificaciones de grafos, ventanas de procedimientos
ms.openlocfilehash: ee30f0eab2bb212dddf1de401a91f0487c512705
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801447"
---
# <a name="class-usernotificationchannel"></a><span data-ttu-id="a26a1-104">las`UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="a26a1-104">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="a26a1-105">Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a26a1-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="a26a1-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="a26a1-106">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="a26a1-107">CreateReader ()</span><span class="sxs-lookup"><span data-stu-id="a26a1-107">CreateReader()</span></span> 
<span data-ttu-id="a26a1-108">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a26a1-108">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="a26a1-109">CreateReader (UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="a26a1-109">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="a26a1-110">Crear un lector de notificaciones de usuario con opciones</span><span class="sxs-lookup"><span data-stu-id="a26a1-110">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="a26a1-111">CreateReaderWithState (cadena)</span><span class="sxs-lookup"><span data-stu-id="a26a1-111">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="a26a1-112">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a26a1-112">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="a26a1-113">El lector se iniciará en el estado de seguimiento proporcionado.</span><span class="sxs-lookup"><span data-stu-id="a26a1-113">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="a26a1-114">GetUserNotificationAsync (cadena)</span><span class="sxs-lookup"><span data-stu-id="a26a1-114">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="a26a1-115">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="a26a1-115">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="a26a1-116">DeleteUserNotificationAsync (cadena)</span><span class="sxs-lookup"><span data-stu-id="a26a1-116">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="a26a1-117">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="a26a1-117">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="a26a1-118">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="a26a1-118">SyncScope()</span></span>
<span data-ttu-id="a26a1-119">Obtiene el ámbito de sincronización de este canal de notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="a26a1-119">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```