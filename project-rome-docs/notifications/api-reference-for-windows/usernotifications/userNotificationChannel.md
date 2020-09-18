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
# <a name="class-usernotificationchannel"></a><span data-ttu-id="c5f23-105">las `UserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="c5f23-105">class `UserNotificationChannel`</span></span>

```C#
public sealed class UserNotificationChannel : IUserNotificationChannel
```

<span data-ttu-id="c5f23-106">Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="c5f23-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="methods"></a><span data-ttu-id="c5f23-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="c5f23-107">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="c5f23-108">CreateReader ()</span><span class="sxs-lookup"><span data-stu-id="c5f23-108">CreateReader()</span></span> 
<span data-ttu-id="c5f23-109">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c5f23-109">Create a user notification reader to receive and manage user notifications published by app server.</span></span>
```C#
public UserNotificationReader CreateReader()
```

### <a name="createreaderusernotificationreaderoptions"></a><span data-ttu-id="c5f23-110">CreateReader (UserNotificationReaderOptions)</span><span class="sxs-lookup"><span data-stu-id="c5f23-110">CreateReader(UserNotificationReaderOptions)</span></span> 
<span data-ttu-id="c5f23-111">Crear un lector de notificaciones de usuario con opciones</span><span class="sxs-lookup"><span data-stu-id="c5f23-111">Create a user notification reader with options</span></span> 
```C#
public UserNotificationReader CreateReader(UserNotificationReaderOptions options)
```

### <a name="createreaderwithstatestring"></a><span data-ttu-id="c5f23-112">CreateReaderWithState (cadena)</span><span class="sxs-lookup"><span data-stu-id="c5f23-112">CreateReaderWithState(String)</span></span> 
<span data-ttu-id="c5f23-113">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="c5f23-113">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="c5f23-114">El lector se iniciará en el estado de seguimiento proporcionado.</span><span class="sxs-lookup"><span data-stu-id="c5f23-114">The reader will start at the provided tracking state.</span></span> 
```C#
public UserNotificationReader CreateReaderWithState(String readerState)
```

### <a name="getusernotificationasyncstring"></a><span data-ttu-id="c5f23-115">GetUserNotificationAsync (cadena)</span><span class="sxs-lookup"><span data-stu-id="c5f23-115">GetUserNotificationAsync(String)</span></span>
<span data-ttu-id="c5f23-116">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="c5f23-116">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotification> GetUserNotificationAsync(String notificationId)
```

### <a name="deleteusernotificationasyncstring"></a><span data-ttu-id="c5f23-117">DeleteUserNotificationAsync (cadena)</span><span class="sxs-lookup"><span data-stu-id="c5f23-117">DeleteUserNotificationAsync(String)</span></span>
<span data-ttu-id="c5f23-118">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="c5f23-118">Get a user notification based on its id.</span></span> 
```C#
public IAsyncOperation<UserNotificationUpdateResult> DeleteUserNotificationAsync(String notificationId)
```

### <a name="syncscope"></a><span data-ttu-id="c5f23-119">SyncScope()</span><span class="sxs-lookup"><span data-stu-id="c5f23-119">SyncScope()</span></span>
<span data-ttu-id="c5f23-120">Obtiene el ámbito de sincronización de este canal de notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="c5f23-120">Get the sync scope of this user notification channel.</span></span>
```C#
public static IUserDataFeedSyncScope SyncScope()
```