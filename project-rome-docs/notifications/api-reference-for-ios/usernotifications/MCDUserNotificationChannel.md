---
title: MCDUserNotificationChannel
description: Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, Windows, retransmisión de dispositivos, iOS y procedimientos de iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801247"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="99f96-104">las`MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="99f96-104">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="99f96-105">Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="99f96-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="99f96-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="99f96-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="99f96-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="99f96-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="99f96-108">SyncScope usado para asegurarse de que UserNotifications se incluyen en la fuente.</span><span class="sxs-lookup"><span data-stu-id="99f96-108">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="99f96-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="99f96-109">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="99f96-110">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="99f96-110">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="99f96-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="99f96-111">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="99f96-112">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="99f96-112">userDataFeed</span></span>
<span data-ttu-id="99f96-113">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="99f96-113">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="99f96-114">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="99f96-114">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="99f96-115">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="99f96-115">userDataFeed</span></span>
<span data-ttu-id="99f96-116">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="99f96-116">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="99f96-117">Métodos</span><span class="sxs-lookup"><span data-stu-id="99f96-117">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="99f96-118">createReader</span><span class="sxs-lookup"><span data-stu-id="99f96-118">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="99f96-119">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="99f96-119">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="99f96-120">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="99f96-120">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="99f96-121">Cree un lector de notificaciones de usuario con opciones.</span><span class="sxs-lookup"><span data-stu-id="99f96-121">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="99f96-122">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="99f96-122">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="99f96-123">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="99f96-123">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="99f96-124">El lector se iniciará en el estado de seguimiento proporcionado.</span><span class="sxs-lookup"><span data-stu-id="99f96-124">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="99f96-125">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="99f96-125">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="99f96-126">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="99f96-126">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="99f96-127">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="99f96-127">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="99f96-128">Elimina una notificación de usuario en función de su identificador.</span><span class="sxs-lookup"><span data-stu-id="99f96-128">Delete a user notification based on its id.</span></span> 