---
title: UserNotification
description: Esta clase representa una notificación de usuario publicado por el servidor de aplicaciones a través de las notificaciones de Graph y recibidos por el cliente de aplicación.
keywords: Microsoft, windows, las notificaciones de graph, procedimientos de windows
ms.openlocfilehash: 5f0489b9db0e644cd0dedd14b07bf2357615419f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907967"
---
# <a name="class-usernotification"></a><span data-ttu-id="9e38e-104">Clase `UserNotification`</span><span class="sxs-lookup"><span data-stu-id="9e38e-104">class `UserNotification`</span></span>

```C#
public sealed class UserNotification : IUserNotification
```

<span data-ttu-id="9e38e-105">Esta clase representa una instancia de la notificación de usuario único.</span><span class="sxs-lookup"><span data-stu-id="9e38e-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="9e38e-106">Una notificación de usuario creada y publicada por el servidor de aplicaciones dirigido a un usuario, que se distribuye a todos los puntos de conexión de dispositivo del mismo usuario registrado.</span><span class="sxs-lookup"><span data-stu-id="9e38e-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="9e38e-107">Una notificación de usuario, una vez recibida por el cliente de aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación local de la plataforma correspondiente.</span><span class="sxs-lookup"><span data-stu-id="9e38e-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="9e38e-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="9e38e-108">Properties</span></span>

|<span data-ttu-id="9e38e-109">Nombre</span><span class="sxs-lookup"><span data-stu-id="9e38e-109">Name</span></span> | <span data-ttu-id="9e38e-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="9e38e-110">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="9e38e-111">Id</span><span class="sxs-lookup"><span data-stu-id="9e38e-111">Id</span></span> |<span data-ttu-id="9e38e-112">Obtiene el programador especifica único identificador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e38e-112">Gets the developer specified unique id for this user notification.</span></span>|
|   <span data-ttu-id="9e38e-113">GroupId</span><span class="sxs-lookup"><span data-stu-id="9e38e-113">GroupId</span></span> |<span data-ttu-id="9e38e-114">Obtiene el programador especifica el identificador de grupo para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e38e-114">Gets the developer specified group id for this user notification.</span></span>| 
|   <span data-ttu-id="9e38e-115">ExpirationTime</span><span class="sxs-lookup"><span data-stu-id="9e38e-115">ExpirationTime</span></span> |<span data-ttu-id="9e38e-116">Obtiene la hora de expiración para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e38e-116">Gets the expiration time for this user notification.</span></span>| 
|   <span data-ttu-id="9e38e-117">Prioridad</span><span class="sxs-lookup"><span data-stu-id="9e38e-117">Priority</span></span>|<span data-ttu-id="9e38e-118">Obtiene el programador especifica la prioridad para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e38e-118">Gets the developer specified priority for this user notification.</span></span>| 
|   <span data-ttu-id="9e38e-119">Contenido</span><span class="sxs-lookup"><span data-stu-id="9e38e-119">Content</span></span>|<span data-ttu-id="9e38e-120">Obtiene la carga de contenido para esta notificación, que es definido por el desarrollador de datos arbitrarios.</span><span class="sxs-lookup"><span data-stu-id="9e38e-120">Gets the content payload for this notification which is developer defined arbitrary data.</span></span>| 
|   <span data-ttu-id="9e38e-121">ReadState</span><span class="sxs-lookup"><span data-stu-id="9e38e-121">ReadState</span></span>|<span data-ttu-id="9e38e-122">Obtiene el valor del estado de lectura para esta notificación de usuario que indica que la notificación es leído o no.</span><span class="sxs-lookup"><span data-stu-id="9e38e-122">Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>| 
|   <span data-ttu-id="9e38e-123">UserActionState</span><span class="sxs-lookup"><span data-stu-id="9e38e-123">UserActionState</span></span>|<span data-ttu-id="9e38e-124">Obtiene el valor del estado de acción de usuario para una notificación de usuario determinar si la notificación no es interactuada, descartar, activada o posponer.</span><span class="sxs-lookup"><span data-stu-id="9e38e-124">Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span>| 


## <a name="methods"></a><span data-ttu-id="9e38e-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="9e38e-125">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="9e38e-126">SaveAsync()</span><span class="sxs-lookup"><span data-stu-id="9e38e-126">SaveAsync()</span></span> 
<span data-ttu-id="9e38e-127">Debe llamarse al publicar los cambios de notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="9e38e-127">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="9e38e-128">Este método debe llamarse siempre que la aplicación modifica una propiedad de la UserNotification actualizable.</span><span class="sxs-lookup"><span data-stu-id="9e38e-128">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>
```C#
public IAsyncOperation SaveAsync()
```
