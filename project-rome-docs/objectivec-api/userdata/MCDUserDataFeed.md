---
title: MCDUserDataFeed
description: Esta clase es responsable de sincronizar los datos específicos del usuario con la plataforma de dispositivos conectados de back-end.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 66898563bdad8adb2f1ebfe75f010cd5ef1d9ca2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908997"
---
# <a name="class-mcduserdatafeed"></a><span data-ttu-id="53ae3-104">Clase `MCDUserDataFeed`</span><span class="sxs-lookup"><span data-stu-id="53ae3-104">class `MCDUserDataFeed`</span></span>

```
@interface MCDUserDataFeed : NSObject
```

<span data-ttu-id="53ae3-105">Esta clase es responsable de sincronizar los datos específicos del usuario con la plataforma de dispositivos conectados de back-end.</span><span class="sxs-lookup"><span data-stu-id="53ae3-105">This class is responsible for synchronizing user-specific data with the Connected Devices Platform backend.</span></span> <span data-ttu-id="53ae3-106">Los datos que se sincronizan dependen de cuál **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** se encuentran las instancias.</span><span class="sxs-lookup"><span data-stu-id="53ae3-106">The data that is synchronized depends on which **[MCDUserDataFeedSyncScope](MCDUserDataFeedSyncScope.md)** instances are contained.</span></span>

## <a name="properties"></a><span data-ttu-id="53ae3-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="53ae3-107">Properties</span></span>

### <a name="syncstatus"></a><span data-ttu-id="53ae3-108">syncStatus</span><span class="sxs-lookup"><span data-stu-id="53ae3-108">syncStatus</span></span>
`@property(nonatomic, readonly) MCDUserDataSyncStatus syncStatus;`

<span data-ttu-id="53ae3-109">Describe el estado actual de la sincronización de datos de usuario.</span><span class="sxs-lookup"><span data-stu-id="53ae3-109">Describes the current status of user data synchronization.</span></span>

### <a name="syncstatuschanged"></a><span data-ttu-id="53ae3-110">syncStatusChanged</span><span class="sxs-lookup"><span data-stu-id="53ae3-110">syncStatusChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserDataFeed*, MCDUserDataFeedSyncStatusChangedEventArgs*>* syncStatusChanged;`

<span data-ttu-id="53ae3-111">Evento para cuando se cambia el estado de sincronización de la UserDataFeed.</span><span class="sxs-lookup"><span data-stu-id="53ae3-111">Event for when the sync status of the UserDataFeed changes.</span></span>

### <a name="daystosync"></a><span data-ttu-id="53ae3-112">daysToSync</span><span class="sxs-lookup"><span data-stu-id="53ae3-112">daysToSync</span></span>
`@property(nonatomic, readwrite) NSInteger daysToSync;`

<span data-ttu-id="53ae3-113">El número de días de datos en sincronizarse, lo que deberían ser menos de 30.</span><span class="sxs-lookup"><span data-stu-id="53ae3-113">The number of days of data to sync, which should be fewer than 30.</span></span>  <span data-ttu-id="53ae3-114">Representa el valor predeterminado, que se determinará por el servidor.</span><span class="sxs-lookup"><span data-stu-id="53ae3-114">It represents the default value, which will be determined by the server.</span></span>

## <a name="constructors"></a><span data-ttu-id="53ae3-115">Constructores</span><span class="sxs-lookup"><span data-stu-id="53ae3-115">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="53ae3-116">getForAccount</span><span class="sxs-lookup"><span data-stu-id="53ae3-116">getForAccount</span></span>
`+ (nullable instancetype)getForAccount:(nonnull MCDConnectedDevicesAccount*)userAccount
                                   platform:(nonnull MCDConnectedDevicesPlatform*)platform
                         activitySourceHost:(nonnull NSString*)activitySourceHost;`

<span data-ttu-id="53ae3-117">Crea e inicializa una nueva instancia de esta clase con una cuenta de usuario, instancia de la plataforma y el identificador de aplicación multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="53ae3-117">Creates and initializes a new instance of this class with a user account, platform instance, and the cross-platform app ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="53ae3-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="53ae3-118">Parameters</span></span>
* `userAccount` 

<span data-ttu-id="53ae3-119">La cuenta de usuario que se asociará estos datos.</span><span class="sxs-lookup"><span data-stu-id="53ae3-119">The user account that this data will be associated with.</span></span>

* `platform` 

<span data-ttu-id="53ae3-120">El **MCDPlatform** instancia que se ha inicializado para la funcionalidad de dispositivos conectados a esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="53ae3-120">The **MCDPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

* `activitySourceHost` 

<span data-ttu-id="53ae3-121">El identificador de aplicación multiplataforma.</span><span class="sxs-lookup"><span data-stu-id="53ae3-121">The cross-platform app ID.</span></span> <span data-ttu-id="53ae3-122">Este valor se recupera mediante el registro del panel para desarrolladores de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="53ae3-122">This is retrieved through the Microsoft Developer Dashboard registration.</span></span>

#### <a name="returns"></a><span data-ttu-id="53ae3-123">Devuelve</span><span class="sxs-lookup"><span data-stu-id="53ae3-123">Returns</span></span>
<span data-ttu-id="53ae3-124">Devuelve una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="53ae3-124">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="53ae3-125">Métodos</span><span class="sxs-lookup"><span data-stu-id="53ae3-125">Methods</span></span>

### <a name="subscribetosyncscopesasync"></a><span data-ttu-id="53ae3-126">subscribeToSyncScopesAsync</span><span class="sxs-lookup"><span data-stu-id="53ae3-126">subscribeToSyncScopesAsync</span></span>
`- (void)subscribeToSyncScopesAsync:(NSArray<MCDUserDataFeedSyncScope*>* _Nonnull) syncScopes callback:(nonnull void (^)(BOOL, NSError* _Nullable)) callback;`

<span data-ttu-id="53ae3-127">Agrega **MCDUserDataFeedSyncScope** instancias para este MCDUserDataFeed.</span><span class="sxs-lookup"><span data-stu-id="53ae3-127">Adds **MCDUserDataFeedSyncScope** instances to this MCDUserDataFeed.</span></span>  <span data-ttu-id="53ae3-128">Este MCDUserDataFeed está sincronizado según la **MCDUserDataFeedSyncScope** instancias especificadas.</span><span class="sxs-lookup"><span data-stu-id="53ae3-128">This MCDUserDataFeed is synchronized according to the **MCDUserDataFeedSyncScope** instances specified.</span></span>

#### <a name="parameters"></a><span data-ttu-id="53ae3-129">Parámetros</span><span class="sxs-lookup"><span data-stu-id="53ae3-129">Parameters</span></span>

* <span data-ttu-id="53ae3-130">`syncScopes` Una matriz de **MCDSyncScope** instancias.</span><span class="sxs-lookup"><span data-stu-id="53ae3-130">`syncScopes` An array of **MCDSyncScope** instances.</span></span>

* `callback`

<span data-ttu-id="53ae3-131">El resultado de la devolución de llamada indica si la suscripción es correcta, o no.</span><span class="sxs-lookup"><span data-stu-id="53ae3-131">The callback result indicates if subscription is successful, or not.</span></span> 

### <a name="startsync"></a><span data-ttu-id="53ae3-132">startSync</span><span class="sxs-lookup"><span data-stu-id="53ae3-132">startSync</span></span>
`- (void)startSync;`

<span data-ttu-id="53ae3-133">Inicia el proceso de sincronización con la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="53ae3-133">Starts the synchronization process with the Connected Devices Platform.</span></span> <span data-ttu-id="53ae3-134">Durante esta operación, el **syncStatus** se actualizará la propiedad y los eventos de cambio, se generará.</span><span class="sxs-lookup"><span data-stu-id="53ae3-134">During this operation, the **syncStatus** property will be updated and change events will be raised.</span></span>