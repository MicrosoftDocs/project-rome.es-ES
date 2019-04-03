---
title: MCDRemoteSystemAppRegistration
description: Esta clase representa una aplicación que va a ser registrada con la plataforma de dispositivos conectados.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909917"
---
# <a name="class-mcdremotesystemappregistration"></a><span data-ttu-id="321ce-104">Clase `MCDRemoteSystemAppRegistration`</span><span class="sxs-lookup"><span data-stu-id="321ce-104">class `MCDRemoteSystemAppRegistration`</span></span> 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

<span data-ttu-id="321ce-105">Esta clase contiene toda la información sobre esta aplicación que otra podría detectar y utilizar.</span><span class="sxs-lookup"><span data-stu-id="321ce-105">This class contains all of the information about this app that another could discover and use.</span></span>

> [!NOTE] 
> <span data-ttu-id="321ce-106">Información de MCDRemoteSystemAppRegistration debe publicarse antes de cualquier comunicación saliente a otra aplicación possble.</span><span class="sxs-lookup"><span data-stu-id="321ce-106">MCDRemoteSystemAppRegistration information must be published before any outgoing communication to another app is possble.</span></span> <span data-ttu-id="321ce-107">Esto es para que la otra aplicación puede saber cómo responder a esa comunicación.</span><span class="sxs-lookup"><span data-stu-id="321ce-107">This is so that the other application can know how to respond to that communication.</span></span>

## <a name="properties"></a><span data-ttu-id="321ce-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="321ce-108">Properties</span></span>

### <a name="account"></a><span data-ttu-id="321ce-109">cuenta</span><span class="sxs-lookup"><span data-stu-id="321ce-109">account</span></span>
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="321ce-110">Cuenta que pertenece este registro.</span><span class="sxs-lookup"><span data-stu-id="321ce-110">Account that this registration belongs to.</span></span>

### <a name="attributes"></a><span data-ttu-id="321ce-111">atributos</span><span class="sxs-lookup"><span data-stu-id="321ce-111">attributes</span></span>
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 <span data-ttu-id="321ce-112">Diccionario de cadenas que describen los atributos de esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="321ce-112">Dictionary of strings that describe the attributes of this app.</span></span>

### <a name="appserviceproviders"></a><span data-ttu-id="321ce-113">appServiceProviders</span><span class="sxs-lookup"><span data-stu-id="321ce-113">appServiceProviders</span></span>
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

<span data-ttu-id="321ce-114">Matriz de AppServiceProviders que admite esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="321ce-114">Array of AppServiceProviders that this app supports.</span></span>

> [!NOTE] 
> <span data-ttu-id="321ce-115">Un proveedor de servicios de aplicación debe estar presente en esta matriz para recibir conexiones entrantes.</span><span class="sxs-lookup"><span data-stu-id="321ce-115">An app service provider must be present in this array in order to receive incoming connections.</span></span>  <span data-ttu-id="321ce-116">MCDRemoteSystemAppRegistration.publishAsync() no deben llamarse para que el proveedor de servicios de aplicación recibir solicitudes.</span><span class="sxs-lookup"><span data-stu-id="321ce-116">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

### <a name="launchuriprovider"></a><span data-ttu-id="321ce-117">launchUriProvider</span><span class="sxs-lookup"><span data-stu-id="321ce-117">launchUriProvider</span></span>
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

<span data-ttu-id="321ce-118">Inicie el Uri del proveedor para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="321ce-118">Launch Uri provider for this app.</span></span>

> [!NOTE] 
> <span data-ttu-id="321ce-119">Un proveedor de uri de inicio debe almacenarse en esta propiedad con el fin de recibir solicitudes entrantes.</span><span class="sxs-lookup"><span data-stu-id="321ce-119">A launch uri provider must be stored in this property in order to receive incoming requests.</span></span>  <span data-ttu-id="321ce-120">MCDRemoteSystemAppRegistration.publishAsync() no deben llamarse para que el proveedor de servicios de aplicación recibir solicitudes.</span><span class="sxs-lookup"><span data-stu-id="321ce-120">MCDRemoteSystemAppRegistration.publishAsync() does not need to be called for the app service provider to receive requests.</span></span>  

## <a name="constructors"></a><span data-ttu-id="321ce-121">Constructores</span><span class="sxs-lookup"><span data-stu-id="321ce-121">Constructors</span></span>

### <a name="getforaccount"></a><span data-ttu-id="321ce-122">getForAccount</span><span class="sxs-lookup"><span data-stu-id="321ce-122">getForAccount</span></span>
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

<span data-ttu-id="321ce-123">Obtiene el registro de aplicación actual del sistema remoto para la cuenta.</span><span class="sxs-lookup"><span data-stu-id="321ce-123">Gets the current remote system app registration for the account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="321ce-124">Parámetros</span><span class="sxs-lookup"><span data-stu-id="321ce-124">Parameters</span></span>
* `account` 

<span data-ttu-id="321ce-125">Para recuperar el registro de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="321ce-125">Account to retrieve the registration for.</span></span>

* `platform` 

<span data-ttu-id="321ce-126">Obtener registro de plataforma.</span><span class="sxs-lookup"><span data-stu-id="321ce-126">Platform to get registration from.</span></span>

#### <a name="returns"></a><span data-ttu-id="321ce-127">Devuelve</span><span class="sxs-lookup"><span data-stu-id="321ce-127">Returns</span></span>
<span data-ttu-id="321ce-128">Devuelve un objeto MCDRemoteSystemAppRegistration para la cuenta proporcionada.</span><span class="sxs-lookup"><span data-stu-id="321ce-128">Returns an MCDRemoteSystemAppRegistration object for the provided Account.</span></span>

## <a name="methods"></a><span data-ttu-id="321ce-129">Métodos</span><span class="sxs-lookup"><span data-stu-id="321ce-129">Methods</span></span>

### <a name="saveasync"></a><span data-ttu-id="321ce-130">saveAsync</span><span class="sxs-lookup"><span data-stu-id="321ce-130">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

<span data-ttu-id="321ce-131">Guarda la información almacenada actualmente en el RemoteSystemAppRegistration tal que otras aplicaciones pueden detectarlo.</span><span class="sxs-lookup"><span data-stu-id="321ce-131">Saves the information currently stored in the RemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="321ce-132">MCDConnectedDevicesNotificationRegistration debe estar registrado para que esta llamada se realice correctamente.</span><span class="sxs-lookup"><span data-stu-id="321ce-132">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

> [!WARNING] 
> <span data-ttu-id="321ce-133">En desuso.</span><span class="sxs-lookup"><span data-stu-id="321ce-133">Deprecated.</span></span> <span data-ttu-id="321ce-134">Use publishAsync en su lugar.</span><span class="sxs-lookup"><span data-stu-id="321ce-134">Use publishAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="321ce-135">Parámetros</span><span class="sxs-lookup"><span data-stu-id="321ce-135">Parameters</span></span>

* `callback`

<span data-ttu-id="321ce-136">La devolución de llamada indica el resultado de guardar la información.</span><span class="sxs-lookup"><span data-stu-id="321ce-136">The callback indicates the result of saving the information.</span></span>

### <a name="publishasync"></a><span data-ttu-id="321ce-137">publishAsync</span><span class="sxs-lookup"><span data-stu-id="321ce-137">publishAsync</span></span>
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="321ce-138">Publica la información almacenada actualmente en el MCDRemoteSystemAppRegistration tal que otras aplicaciones pueden detectarlo.</span><span class="sxs-lookup"><span data-stu-id="321ce-138">Publishes the information currently stored in the MCDRemoteSystemAppRegistration such that other applications can discover it.</span></span>

> [!NOTE] 
> <span data-ttu-id="321ce-139">MCDConnectedDevicesNotificationRegistration debe estar registrado para que esta llamada se realice correctamente.</span><span class="sxs-lookup"><span data-stu-id="321ce-139">MCDConnectedDevicesNotificationRegistration must be registered for this call to succeed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="321ce-140">Parámetros</span><span class="sxs-lookup"><span data-stu-id="321ce-140">Parameters</span></span>

* `callback`

<span data-ttu-id="321ce-141">La devolución de llamada indica el resultado de guardar la información.</span><span class="sxs-lookup"><span data-stu-id="321ce-141">The callback indicates the result of saving the information.</span></span>
