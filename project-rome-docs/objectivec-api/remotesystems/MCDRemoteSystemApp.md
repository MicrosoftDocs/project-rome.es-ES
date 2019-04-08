---
title: MCDRemoteSystemApp
description: Representa una aplicación en un sistema remoto que está disponible para la conectividad.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907657"
---
# <a name="class-mcdremotesystemapp"></a><span data-ttu-id="a209f-104">Clase `MCDRemoteSystemApp`</span><span class="sxs-lookup"><span data-stu-id="a209f-104">class `MCDRemoteSystemApp`</span></span> 

```
@interface MCDRemoteSystemApp : NSObject
```  

<span data-ttu-id="a209f-105">Representa una aplicación en un sistema remoto que está disponible para la conectividad.</span><span class="sxs-lookup"><span data-stu-id="a209f-105">Represents an application on a remote system that is available for connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="a209f-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a209f-106">Properties</span></span>

### <a name="appid"></a><span data-ttu-id="a209f-107">appId</span><span class="sxs-lookup"><span data-stu-id="a209f-107">appId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* appId;`

<span data-ttu-id="a209f-108">Un identificador único para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="a209f-108">A unique identifier for this application.</span></span>

### <a name="displayname"></a><span data-ttu-id="a209f-109">displayName</span><span class="sxs-lookup"><span data-stu-id="a209f-109">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="a209f-110">El nombre para mostrar descriptivo para esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="a209f-110">The friendly display name for this application.</span></span> <span data-ttu-id="a209f-111">Este es el nombre utilizado por el dispositivo para la identificación de Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="a209f-111">This is the name used by the device for Bluetooth identification.</span></span> <span data-ttu-id="a209f-112">Si esto no se ha establecido o el dispositivo no es compatible con Bluetooth, este campo estará vacío.</span><span class="sxs-lookup"><span data-stu-id="a209f-112">If this hasn't been set or the device doesn't support Bluetooth, this field will be empty.</span></span>

### <a name="availablebyproximity"></a><span data-ttu-id="a209f-113">availableByProximity</span><span class="sxs-lookup"><span data-stu-id="a209f-113">availableByProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

<span data-ttu-id="a209f-114">Indica si esta aplicación está actualmente disponible para la conexión articulaciones próximas.</span><span class="sxs-lookup"><span data-stu-id="a209f-114">Indicates whether this application is currently available for proximal connection.</span></span>

### <a name="availablebyspatialproximity"></a><span data-ttu-id="a209f-115">availableBySpatialProximity</span><span class="sxs-lookup"><span data-stu-id="a209f-115">availableBySpatialProximity</span></span>
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

<span data-ttu-id="a209f-116">Indica si esta aplicación está disponible actualmente para la conexión compartida espacial.</span><span class="sxs-lookup"><span data-stu-id="a209f-116">Indicates whether this application is currently available for spatial sharing connection.</span></span>

### <a name="attributes"></a><span data-ttu-id="a209f-117">atributos</span><span class="sxs-lookup"><span data-stu-id="a209f-117">attributes</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

<span data-ttu-id="a209f-118">Un diccionario de pares clave/valor que define los atributos de esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="a209f-118">A dictionary of key/value pairs defining the attributes of this application.</span></span>

### <a name="appservices"></a><span data-ttu-id="a209f-119">appServices</span><span class="sxs-lookup"><span data-stu-id="a209f-119">appServices</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

<span data-ttu-id="a209f-120">Una matriz de instancias de MCDAppServiceDescription que describe los servicios de aplicación que proporciona esta aplicación para la conectividad remota.</span><span class="sxs-lookup"><span data-stu-id="a209f-120">An array of MCDAppServiceDescription instances describing the app services that this application provides for remote connectivity.</span></span>

### <a name="accounts"></a><span data-ttu-id="a209f-121">cuentas</span><span class="sxs-lookup"><span data-stu-id="a209f-121">accounts</span></span>
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

<span data-ttu-id="a209f-122">La cuenta asociada con el MCDRemoteSystemApp que debe saber acerca de los permisos.</span><span class="sxs-lookup"><span data-stu-id="a209f-122">The Account associated with the MCDRemoteSystemApp that you have permissions to know about.</span></span> <span data-ttu-id="a209f-123">¿Qué determina los permisos es si el MCDConnectedDevicesAccount existe en el MCDConnectedDevicesAccountManager cuando se inicia el MCDRemoteSystemWatcher.</span><span class="sxs-lookup"><span data-stu-id="a209f-123">What determines permissions is if the MCDConnectedDevicesAccount exists in the MCDConnectedDevicesAccountManager when the MCDRemoteSystemWatcher is started.</span></span>