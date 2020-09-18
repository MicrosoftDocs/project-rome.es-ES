---
title: MCDUserNotificationChannel
description: Obtenga información sobre la clase MCDUserNotificationChannel. Esta clase administra el ciclo de vida de las notificaciones de usuario.
keywords: Microsoft, Windows, retransmisión de dispositivos, iOS y procedimientos de iPhone
ms.openlocfilehash: dc7e451494014cdcdebd056b00e57cfdf5f0757f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760879"
---
# <a name="class-mcdusernotificationchannel"></a><span data-ttu-id="d85a4-105">las `MCDUserNotificationChannel`</span><span class="sxs-lookup"><span data-stu-id="d85a4-105">class `MCDUserNotificationChannel`</span></span>

```
@interface MCDUserNotificationChannel : NSObject
```

<span data-ttu-id="d85a4-106">Esta clase proporciona el lector de cambios de notificación que controla la recepción y la administración de las notificaciones de usuario para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d85a4-106">This class provides the notification change reader which handles the receiving and management of user notifications for the application.</span></span> 

## <a name="properties"></a><span data-ttu-id="d85a4-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d85a4-107">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="d85a4-108">syncScope</span><span class="sxs-lookup"><span data-stu-id="d85a4-108">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="d85a4-109">SyncScope usado para asegurarse de que UserNotifications se incluyen en la fuente.</span><span class="sxs-lookup"><span data-stu-id="d85a4-109">SyncScope used to ensure UserNotifications are included in the feed.</span></span>

## <a name="constructors"></a><span data-ttu-id="d85a4-110">Constructores</span><span class="sxs-lookup"><span data-stu-id="d85a4-110">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="d85a4-111">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="d85a4-111">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

#### <a name="parameters"></a><span data-ttu-id="d85a4-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d85a4-112">Parameters</span></span>

### <a name="userdatafeed"></a><span data-ttu-id="d85a4-113">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="d85a4-113">userDataFeed</span></span>
<span data-ttu-id="d85a4-114">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="d85a4-114">The MCDUserDataFeed used to initialize this class.</span></span>

### <a name="initwithuserdatafeed"></a><span data-ttu-id="d85a4-115">initWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="d85a4-115">initWithUserDataFeed</span></span>
`- (nullable instancetype)initWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

### <a name="userdatafeed"></a><span data-ttu-id="d85a4-116">userDataFeed</span><span class="sxs-lookup"><span data-stu-id="d85a4-116">userDataFeed</span></span>
<span data-ttu-id="d85a4-117">MCDUserDataFeed que se usa para inicializar esta clase.</span><span class="sxs-lookup"><span data-stu-id="d85a4-117">The MCDUserDataFeed used to initialize this class.</span></span>

## <a name="methods"></a><span data-ttu-id="d85a4-118">Métodos</span><span class="sxs-lookup"><span data-stu-id="d85a4-118">Methods</span></span>

### <a name="createreader"></a><span data-ttu-id="d85a4-119">createReader</span><span class="sxs-lookup"><span data-stu-id="d85a4-119">createReader</span></span>
`- (MCDUserNotificationReader* _Nullable)createReader`

<span data-ttu-id="d85a4-120">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d85a4-120">Create a user notification reader to receive and manage user notifications published by app server.</span></span>

### <a name="createreaderwithoptions"></a><span data-ttu-id="d85a4-121">createReaderWithOptions</span><span class="sxs-lookup"><span data-stu-id="d85a4-121">createReaderWithOptions</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithOptions:(MCDUserNotificationReaderOptions* _Nonnull)options`

<span data-ttu-id="d85a4-122">Cree un lector de notificaciones de usuario con opciones.</span><span class="sxs-lookup"><span data-stu-id="d85a4-122">Create a user notification reader with options.</span></span>

### <a name="createreaderwithstate"></a><span data-ttu-id="d85a4-123">createReaderWithState</span><span class="sxs-lookup"><span data-stu-id="d85a4-123">createReaderWithState</span></span>
`- (MCDUserNotificationReader* _Nullable)createReaderWithState:(NSString* _Nonnull)readerState`

<span data-ttu-id="d85a4-124">Cree un lector de notificaciones de usuario para recibir y administrar las notificaciones de usuario publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="d85a4-124">Create a user notification reader to receive and manage user notifications published by app server.</span></span> <span data-ttu-id="d85a4-125">El lector se iniciará en el estado de seguimiento proporcionado.</span><span class="sxs-lookup"><span data-stu-id="d85a4-125">The reader will start at the provided tracking state.</span></span>  

### <a name="getusernotificationasync"></a><span data-ttu-id="d85a4-126">getUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="d85a4-126">getUserNotificationAsync</span></span>
`- (void)getUserNotificationAsync:(NSString* _Nonnull)notificationId
                      completion:(nonnull void (^)(MCDUserNotification* _Nullable, NSError* _Nullable))completion`

<span data-ttu-id="d85a4-127">Obtiene una notificación de usuario basada en su identificador.</span><span class="sxs-lookup"><span data-stu-id="d85a4-127">Get a user notification based on its id.</span></span>

### <a name="deleteusernotificationasync"></a><span data-ttu-id="d85a4-128">deleteUserNotificationAsync</span><span class="sxs-lookup"><span data-stu-id="d85a4-128">deleteUserNotificationAsync</span></span>
```
- (void)deleteUserNotificationAsync:(NSString* _Nonnull)notificationId
                         completion:(nonnull void (^)(MCDUserNotificationUpdateResult* _Nullable, NSError* _Nullable))completion
```

<span data-ttu-id="d85a4-129">Elimina una notificación de usuario en función de su identificador.</span><span class="sxs-lookup"><span data-stu-id="d85a4-129">Delete a user notification based on its id.</span></span> 