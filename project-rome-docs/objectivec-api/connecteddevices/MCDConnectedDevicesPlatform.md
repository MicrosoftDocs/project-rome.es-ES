---
title: MCDConnectedDevicesPlatform
description: Una clase para representar la plataforma de dispositivos conectados y administrar la conexión de la aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909747"
---
# <a name="class-mcdconnecteddevicesplatform"></a><span data-ttu-id="b388c-104">Clase `MCDConnectedDevicesPlatform`</span><span class="sxs-lookup"><span data-stu-id="b388c-104">class `MCDConnectedDevicesPlatform`</span></span> 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
<span data-ttu-id="b388c-105">Esta clase para representar la plataforma de dispositivos conectados y administrar la conexión de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b388c-105">This class to represent the Connected Devices Platform and manage the app's connection to it.</span></span>

## <a name="properties"></a><span data-ttu-id="b388c-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b388c-106">Properties</span></span>

### <a name="accountmanager"></a><span data-ttu-id="b388c-107">accountManager</span><span class="sxs-lookup"><span data-stu-id="b388c-107">accountManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

<span data-ttu-id="b388c-108">Instancia de MCDConnectedDevicesAccountManager mantenido por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-108">MCDConnectedDevicesAccountManager instance held by the platform.</span></span>

### <a name="notificationregistrationmanager"></a><span data-ttu-id="b388c-109">notificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="b388c-109">notificationRegistrationManager</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

<span data-ttu-id="b388c-110">Instancia de MCDConnectedDevicesNotificationRegistrationManager mantenido por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-110">MCDConnectedDevicesNotificationRegistrationManager instance held by platform.</span></span>

## <a name="constructors"></a><span data-ttu-id="b388c-111">Constructores</span><span class="sxs-lookup"><span data-stu-id="b388c-111">Constructors</span></span>

### <a name="platformwithsettings"></a><span data-ttu-id="b388c-112">platformWithSettings</span><span class="sxs-lookup"><span data-stu-id="b388c-112">platformWithSettings</span></span>
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="b388c-113">Una nueva instancia de esta clase con la configuración de plataforma especificado.</span><span class="sxs-lookup"><span data-stu-id="b388c-113">A new instance of this class with specified platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b388c-114">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b388c-114">Parameters</span></span> 
* `settings` 

<span data-ttu-id="b388c-115">El objeto MCDConnectedDevicesPlatformSettings que almacena la configuración de la aplicación de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-115">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="b388c-116">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b388c-116">Returns</span></span>

<span data-ttu-id="b388c-117">Devuelve un objeto MCDConnectedDevicesPlatform que contiene la configuración de la plataforma de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b388c-117">Returns an MCDConnectedDevicesPlatform object containing the app's platform settings.</span></span>

### <a name="initwithsettings"></a><span data-ttu-id="b388c-118">initWithSettings</span><span class="sxs-lookup"><span data-stu-id="b388c-118">initWithSettings</span></span>
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

<span data-ttu-id="b388c-119">Una nueva instancia de esta clase con la configuración de plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-119">A new instance of this class with the platform settings.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b388c-120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b388c-120">Parameters</span></span> 
* `settings` 

<span data-ttu-id="b388c-121">El objeto MCDConnectedDevicesPlatformSettings que almacena la configuración de la aplicación de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-121">The MCDConnectedDevicesPlatformSettings object which stores the app's settings of the platform.</span></span>

#### <a name="returns"></a><span data-ttu-id="b388c-122">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b388c-122">Returns</span></span>

<span data-ttu-id="b388c-123">Devuelve un objeto MCDConnectedDevicesPlatform inicializado con la configuración de la plataforma de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="b388c-123">Returns an MCDConnectedDevicesPlatform object initialized with the app's platform settings.</span></span>

## <a name="methods"></a><span data-ttu-id="b388c-124">Métodos</span><span class="sxs-lookup"><span data-stu-id="b388c-124">Methods</span></span>

### <a name="processnotification"></a><span data-ttu-id="b388c-125">processNotification</span><span class="sxs-lookup"><span data-stu-id="b388c-125">processNotification</span></span>
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

<span data-ttu-id="b388c-126">Procesar la notificación de APNs entrante.</span><span class="sxs-lookup"><span data-stu-id="b388c-126">Process incoming APNs notification.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b388c-127">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b388c-127">Parameters</span></span> 
* `notification` 

<span data-ttu-id="b388c-128">Contiene la notificación de APNs para procesar.</span><span class="sxs-lookup"><span data-stu-id="b388c-128">Contains the APNs notification to process.</span></span>

#### <a name="returns"></a><span data-ttu-id="b388c-129">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b388c-129">Returns</span></span>

<span data-ttu-id="b388c-130">Una instancia de la clase MCDConnectedDevicesProcessNotificationOperation.</span><span class="sxs-lookup"><span data-stu-id="b388c-130">An instance of the MCDConnectedDevicesProcessNotificationOperation class.</span></span>

### <a name="start"></a><span data-ttu-id="b388c-131">start</span><span class="sxs-lookup"><span data-stu-id="b388c-131">start</span></span>
`- (void) start;`

<span data-ttu-id="b388c-132">Inicie la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b388c-132">Start the platform.</span></span>

### <a name="shutdownasync"></a><span data-ttu-id="b388c-133">shutdownAsync</span><span class="sxs-lookup"><span data-stu-id="b388c-133">shutdownAsync</span></span>
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="b388c-134">Se cierra la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="b388c-134">Shuts down the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b388c-135">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b388c-135">Parameters</span></span> 
* `completionBlock` 

<span data-ttu-id="b388c-136">El bloque para invocar la finalización.</span><span class="sxs-lookup"><span data-stu-id="b388c-136">The block to invoke upon completion.</span></span>