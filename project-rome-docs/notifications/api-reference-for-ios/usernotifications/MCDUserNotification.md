---
title: MCDUserNotification
description: Esta clase representa una notificación de usuario publicada por el servidor de aplicaciones a través de notificaciones de grafos y recibida por el cliente de la aplicación.
keywords: Microsoft, iOS, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 5ca1360c34e2bf9aa5d9847b8df2c462e2956b31
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907897"
---
# <a name="class-mcdusernotification"></a><span data-ttu-id="5dc1a-104">las`MCDUserNotification`</span><span class="sxs-lookup"><span data-stu-id="5dc1a-104">class `MCDUserNotification`</span></span>

```
@interface MCDUserNotification : NSObject
```


<span data-ttu-id="5dc1a-105">Esta clase representa una instancia de notificación de un solo usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-105">This class represent a single user notification instance.</span></span> <span data-ttu-id="5dc1a-106">El servidor de aplicaciones que se dirige a un usuario crea y publica una notificación de usuario, que se distribuye a todos los puntos de conexión del dispositivo del mismo usuario que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-106">A user notification is created and published by your app server targeted at a user, distributed to all device endpoints of the same logged in user.</span></span>
<span data-ttu-id="5dc1a-107">Una notificación de usuario, una vez recibida por el cliente de la aplicación, puede dar lugar a experiencias como generar y mostrar un banner de notificación visual mediante las API de notificación locales de la plataforma correspondiente.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-107">A user notification, once received by the app client, can result in experiences such as generating and showing a visual notification banner using local notification APIs of the corresponding platform.</span></span>

## <a name="properties"></a><span data-ttu-id="5dc1a-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="5dc1a-108">Properties</span></span>

### <a name="notificationid"></a><span data-ttu-id="5dc1a-109">notificationId</span><span class="sxs-lookup"><span data-stu-id="5dc1a-109">notificationId</span></span>
<span data-ttu-id="5dc1a-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;`Obtiene el identificador único especificado por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-110">`@property(nonatomic, readonly, nonnull) NSString* notificationId;` Gets the developer specified unique id for this user notification.</span></span>

### <a name="groupid"></a><span data-ttu-id="5dc1a-111">groupId</span><span class="sxs-lookup"><span data-stu-id="5dc1a-111">groupId</span></span>
<span data-ttu-id="5dc1a-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;`Obtiene el identificador de grupo especificado por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-112">`@property(nonatomic, readonly, nonnull) NSString* groupId;` Gets the developer specified group id for this user notification.</span></span>

### <a name="expirationtime"></a><span data-ttu-id="5dc1a-113">expirationTime</span><span class="sxs-lookup"><span data-stu-id="5dc1a-113">expirationTime</span></span>
<span data-ttu-id="5dc1a-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;`Obtiene la hora de expiración de esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-114">`@property(nonatomic, readonly, nonnull) NSDate* expirationTime;` Gets the expiration time for this user notification.</span></span>

### <a name="status"></a><span data-ttu-id="5dc1a-115">status</span><span class="sxs-lookup"><span data-stu-id="5dc1a-115">status</span></span>
<span data-ttu-id="5dc1a-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;`Obtiene el estado de la notificación del usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-116">`@property(nonatomic, readonly) MCDUserNotificationStatus status;` Gets the status of the user notification.</span></span>

### <a name="changetime"></a><span data-ttu-id="5dc1a-117">changeTime</span><span class="sxs-lookup"><span data-stu-id="5dc1a-117">changeTime</span></span>
<span data-ttu-id="5dc1a-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;`Obtiene la hora a la que se realizó el cambio.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-118">`@property(nonatomic, readonly, nonnull) NSDate* changeTime;` Gets the time the change was made.</span></span>

### <a name="priority"></a><span data-ttu-id="5dc1a-119">prioridad</span><span class="sxs-lookup"><span data-stu-id="5dc1a-119">priority</span></span>
<span data-ttu-id="5dc1a-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;`Obtiene la prioridad especificada por el desarrollador para esta notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-120">`@property(nonatomic, readonly) MCDUserNotificationPriority priority;` Gets the developer specified priority for this user notification.</span></span>

### <a name="content"></a><span data-ttu-id="5dc1a-121">contenido</span><span class="sxs-lookup"><span data-stu-id="5dc1a-121">content</span></span>
<span data-ttu-id="5dc1a-122">`@property(nonatomic, readonly, nonnull) NSString* content;`Obtiene la carga de contenido para esta notificación, que es datos arbitrarios definidos por el desarrollador.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-122">`@property(nonatomic, readonly, nonnull) NSString* content;` Gets the content payload for this notification which is developer defined arbitrary data.</span></span>

###  <a name="readstate"></a><span data-ttu-id="5dc1a-123">readState</span><span class="sxs-lookup"><span data-stu-id="5dc1a-123">readState</span></span>
<span data-ttu-id="5dc1a-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;`Obtiene el valor del estado de lectura de esta notificación de usuario que indica que la notificación se ha leído o no se ha leído.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-124">`@property(nonatomic, assign, readwrite) MCDUserNotificationReadState readState;` Gets the value of the read state for this user notification that indicates the notification is read or unread.</span></span>

### <a name="useractionstate"></a><span data-ttu-id="5dc1a-125">userActionState</span><span class="sxs-lookup"><span data-stu-id="5dc1a-125">userActionState</span></span>
<span data-ttu-id="5dc1a-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;`Obtiene el valor del estado de acción del usuario para una notificación de usuario para determinar si la notificación no se ha interactuado, descartado, activado o pospuesto.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-126">`@property(nonatomic, assign, readwrite) MCDUserNotificationUserActionState userActionState;` Gets the value of the user action state for a user notification to determine whether the notification is not interacted, dismissed, activated, or snoozed.</span></span> 

## <a name="methods"></a><span data-ttu-id="5dc1a-127">Métodos</span><span class="sxs-lookup"><span data-stu-id="5dc1a-127">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="5dc1a-128">saveAsync</span><span class="sxs-lookup"><span data-stu-id="5dc1a-128">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(MCDUserNotificationUpdateStatus* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="5dc1a-129">Se debe llamar a este método al publicar cambios en las notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-129">This should be called when publishing user notification changes.</span></span> <span data-ttu-id="5dc1a-130">Se debe llamar a este método siempre que la aplicación modifique una propiedad actualizable de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-130">This method should be called whenever the app modifies an updatable property of the UserNotification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="5dc1a-131">Parámetros</span><span class="sxs-lookup"><span data-stu-id="5dc1a-131">Parameters</span></span>
* <span data-ttu-id="5dc1a-132">`completion`Bloque de código que se va a ejecutar cuando se complete.</span><span class="sxs-lookup"><span data-stu-id="5dc1a-132">`completion` The code block to execute upon completion.</span></span>
