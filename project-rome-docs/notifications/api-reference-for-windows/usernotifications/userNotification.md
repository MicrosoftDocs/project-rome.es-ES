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
# <a name="class-usernotification"></a><span data-ttu-id="37f99-104">las`UserNotification`</span><span class="sxs-lookup"><span data-stu-id="37f99-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="37f99-105">Esta clase representa una instancia de notificación de un solo usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="37f99-106">El servidor de aplicaciones que se dirige a un usuario crea y publica una notificación de usuario, que se distribuye a todos los puntos de conexión del dispositivo del mismo usuario que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="37f99-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="37f99-107">Una notificación de usuario, una vez recibida por el cliente de la aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación locales de la plataforma correspondiente.</span><span class="sxs-lookup"><span data-stu-id="37f99-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="37f99-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="37f99-108">Properties</span></span>

|<span data-ttu-id="37f99-109">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="37f99-109">Name</span></span> | <span data-ttu-id="37f99-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="37f99-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="37f99-111">Id</span><span class="sxs-lookup"><span data-stu-id="37f99-111">Id</span></span> |<span data-ttu-id="37f99-112">Obtiene el identificador único especificado por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="37f99-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="37f99-113">GroupId</span></span> |<span data-ttu-id="37f99-114">Obtiene el identificador de grupo especificado por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="37f99-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="37f99-115">ExpirationTime</span></span> |<span data-ttu-id="37f99-116">Obtiene la hora de expiración de esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="37f99-117">Prioridad</span><span class="sxs-lookup"><span data-stu-id="37f99-117">Priority</span></span>|<span data-ttu-id="37f99-118">Obtiene la prioridad especificada por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="37f99-119">Contenido</span><span class="sxs-lookup"><span data-stu-id="37f99-119">Content</span></span>|<span data-ttu-id="37f99-120">Obtiene la carga de contenido para esta notificación, que es datos arbitrarios definidos por el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="37f99-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="37f99-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="37f99-121">ReadState</span></span>|<span data-ttu-id="37f99-122">Obtiene el valor del estado de lectura de esta notificación de usuario que indica que la notificación se ha leído o no se ha leído.</span><span class="sxs-lookup"><span data-stu-id="37f99-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="37f99-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="37f99-123">UserActionState</span></span>|<span data-ttu-id="37f99-124">Obtiene el valor del estado de acción del usuario para una notificación de usuario para determinar si la notificación no se ha interactuado, descartado, activado o pospuesto.</span><span class="sxs-lookup"><span data-stu-id="37f99-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="37f99-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="37f99-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="37f99-126">SaveAsync ()</span><span class="sxs-lookup"><span data-stu-id="37f99-126">SaveAsync()</span></span> 
<span data-ttu-id="37f99-127">Se debe llamar a este método al publicar cambios en las notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="37f99-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="37f99-128">Se debe llamar a este método siempre que la aplicación modifique una propiedad actualizable de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="37f99-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```

