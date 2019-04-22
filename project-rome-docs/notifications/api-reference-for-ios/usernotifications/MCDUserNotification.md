---
title: MCDUserNotification
description: Esta clase representa una notificación de usuario publicado por el servidor de aplicaciones a través de las notificaciones de Graph y recibidos por el cliente de aplicación.
keywords: Microsoft, ios, notificaciones de graph, ios procedimientos, procedimientos iphone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907897"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="7c38c-104">Clase `MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="7c38c-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="7c38c-105">Esta clase representa una instancia de la notificación de usuario único.</span><span class="sxs-lookup"><span data-stu-id="7c38c-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="7c38c-106">Una notificación de usuario creada y publicada por el servidor de aplicaciones dirigido a un usuario, que se distribuye a todos los puntos de conexión de dispositivo del mismo usuario registrado.</span><span class="sxs-lookup"><span data-stu-id="7c38c-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="7c38c-107">Una notificación de usuario, una vez recibida por el cliente de aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación local de la plataforma correspondiente.</span><span class="sxs-lookup"><span data-stu-id="7c38c-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="7c38c-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="7c38c-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="7c38c-109">notificationId</span><span class="sxs-lookup"><span data-stu-id="7c38c-109">notificationId</span></span>
<span data-ttu-id="7c38c-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Obtiene el programador especifica único identificador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="7c38c-111">groupId</span><span class="sxs-lookup"><span data-stu-id="7c38c-111">groupId</span></span>
<span data-ttu-id="7c38c-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Obtiene el programador especifica el identificador de grupo para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="7c38c-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="7c38c-113">expirationTime</span></span>
<span data-ttu-id="7c38c-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Obtiene la hora de expiración para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="7c38c-115">status</span><span class="sxs-lookup"><span data-stu-id="7c38c-115">status</span></span>
<span data-ttu-id="7c38c-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Obtiene el estado de la notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="7c38c-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="7c38c-117">changeTime</span></span>
<span data-ttu-id="7c38c-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Obtiene la hora en que se realizó el cambio.</span><span class="sxs-lookup"><span data-stu-id="7c38c-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="7c38c-119">priority</span><span class="sxs-lookup"><span data-stu-id="7c38c-119">priority</span></span>
<span data-ttu-id="7c38c-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Obtiene el programador especifica la prioridad para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="7c38c-121">content</span><span class="sxs-lookup"><span data-stu-id="7c38c-121">content</span></span>
<span data-ttu-id="7c38c-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Obtiene la carga de contenido para esta notificación, que es definido por el desarrollador de datos arbitrarios.</span><span class="sxs-lookup"><span data-stu-id="7c38c-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="7c38c-123">readState</span><span class="sxs-lookup"><span data-stu-id="7c38c-123">readState</span></span>
<span data-ttu-id="7c38c-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Obtiene el valor del estado de lectura para esta notificación de usuario que indica que la notificación es leído o no.</span><span class="sxs-lookup"><span data-stu-id="7c38c-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="7c38c-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="7c38c-125">userActionState</span></span>
<span data-ttu-id="7c38c-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Obtiene el valor del estado de acción de usuario para una notificación de usuario determinar si la notificación no es interactuada, descartar, activada o posponer.</span><span class="sxs-lookup"><span data-stu-id="7c38c-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="7c38c-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="7c38c-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="7c38c-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="7c38c-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="7c38c-129">Debe llamarse al publicar los cambios de notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="7c38c-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="7c38c-130">Este método debe llamarse siempre que la aplicación modifica una propiedad de la UserNotification actualizable.</span><span class="sxs-lookup"><span data-stu-id="7c38c-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="7c38c-131">Parámetros</span><span class="sxs-lookup"><span data-stu-id="7c38c-131">Parameters</span></span>
* <span data-ttu-id="7c38c-132">`completion` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="7c38c-132">`completion` The code block to execute upon completion.</span></span>
