---
title: MCDRemoteLauncherOptions
description: Una clase que representa las opciones de la característica de inicio remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907337"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="d1598-104">Clase `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="d1598-104">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="d1598-105">Una clase que representa las opciones de la característica de inicio remoto.</span><span class="sxs-lookup"><span data-stu-id="d1598-105">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="d1598-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d1598-106">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="d1598-107">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="d1598-107">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="d1598-108">Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-108">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="d1598-109">preferredPackageIds</span><span class="sxs-lookup"><span data-stu-id="d1598-109">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="d1598-110">Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI.</span><span class="sxs-lookup"><span data-stu-id="d1598-110">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="d1598-111">Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-111">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="d1598-112">Constructores</span><span class="sxs-lookup"><span data-stu-id="d1598-112">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="d1598-113">optionsWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="d1598-113">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="d1598-114">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="d1598-114">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d1598-115">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d1598-115">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="d1598-116">Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-116">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="d1598-117">Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI.</span><span class="sxs-lookup"><span data-stu-id="d1598-117">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="d1598-118">Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-118">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="d1598-119">Devuelve</span><span class="sxs-lookup"><span data-stu-id="d1598-119">Returns</span></span>
<span data-ttu-id="d1598-120">Devuelve el inicializado [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="d1598-120">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="d1598-121">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="d1598-121">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="d1598-122">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="d1598-122">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d1598-123">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d1598-123">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="d1598-124">Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-124">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="d1598-125">Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI.</span><span class="sxs-lookup"><span data-stu-id="d1598-125">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="d1598-126">Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d1598-126">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="d1598-127">Devuelve</span><span class="sxs-lookup"><span data-stu-id="d1598-127">Returns</span></span>
<span data-ttu-id="d1598-128">Devuelve el inicializado [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="d1598-128">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>