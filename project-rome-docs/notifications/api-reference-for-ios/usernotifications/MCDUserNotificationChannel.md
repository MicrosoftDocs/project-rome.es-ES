---
title: MCDUserNotificationChannel
description: Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, windows, retransmisión de dispositivo, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 234e1af807ac816918fe1de37a18dc07f73fca09
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907187"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="ad740-104">Clase `MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="ad740-104">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="ad740-105">Esta clase proporciona el lector de cambio de notificación que controla la recepción y la administración de las notificaciones de usuario de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ad740-105">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="ad740-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ad740-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="ad740-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="ad740-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="ad740-108">SyncScope se utiliza para garantizar que usernotifications se incluyen en la fuente.</span><span class="sxs-lookup"><span data-stu-id="ad740-108">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="ad740-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="ad740-109">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="ad740-110">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="ad740-110">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="ad740-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad740-111">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="ad740-112">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="ad740-112">userDataFeed</span></span>
<span data-ttu-id="ad740-113">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="ad740-113">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="ad740-114">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="ad740-114">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="ad740-115">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="ad740-115">userDataFeed</span></span>
<span data-ttu-id="ad740-116">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="ad740-116">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="ad740-117">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad740-117">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="ad740-118">createReader</span><span class="sxs-lookup"><span data-stu-id="ad740-118">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="ad740-119">Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="ad740-119">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="ad740-120">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="ad740-120">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="ad740-121">Crear un lector de notificación de usuario con opciones.</span><span class="sxs-lookup"><span data-stu-id="ad740-121">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="ad740-122">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="ad740-122">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="ad740-123">Crear un lector de notificación de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="ad740-123">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="ad740-124">El lector se iniciará en el estado de seguimiento proporcionados.</span><span class="sxs-lookup"><span data-stu-id="ad740-124">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="ad740-125">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="ad740-125">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="ad740-126">Reciba una notificación de usuario según su identificador.</span><span class="sxs-lookup"><span data-stu-id="ad740-126">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="ad740-127">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="ad740-127">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="ad740-128">Eliminar una notificación de usuario según su identificador.</span><span class="sxs-lookup"><span data-stu-id="ad740-128">Delete a user notification based on its id.</span></span> 