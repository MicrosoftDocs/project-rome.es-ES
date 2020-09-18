---
title: MCDRemoteLauncherOptions
description: Obtenga información sobre la clase MCDRemoteLauncherOptions. Esta clase representa las opciones de la característica de inicio remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 2e698ad71282e44d1447e19085598139b67f9270
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760739"
---
# <a name="class-mcdremotelauncheroptions"></a><span data-ttu-id="a7338-105">las `MCDRemoteLauncherOptions`</span><span class="sxs-lookup"><span data-stu-id="a7338-105">class `MCDRemoteLauncherOptions`</span></span> 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

<span data-ttu-id="a7338-106">Una clase que representa las opciones de la característica de inicio remoto.</span><span class="sxs-lookup"><span data-stu-id="a7338-106">A class to represent options for the remote launch feature.</span></span>

## <a name="properties"></a><span data-ttu-id="a7338-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a7338-107">Properties</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="a7338-108">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="a7338-108">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="a7338-109">URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-109">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

### <a name="preferredpackageids"></a><span data-ttu-id="a7338-110">preferredPackageIds</span><span class="sxs-lookup"><span data-stu-id="a7338-110">preferredPackageIds</span></span>
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

<span data-ttu-id="a7338-111">Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI.</span><span class="sxs-lookup"><span data-stu-id="a7338-111">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="a7338-112">En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-112">For Windows apps, the ID will be the app's package family name.</span></span>

## <a name="constructors"></a><span data-ttu-id="a7338-113">Constructores</span><span class="sxs-lookup"><span data-stu-id="a7338-113">Constructors</span></span>

### <a name="optionswithfallbackuri"></a><span data-ttu-id="a7338-114">optionsWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="a7338-114">optionsWithFallbackUri</span></span>
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="a7338-115">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="a7338-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a7338-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a7338-116">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="a7338-117">URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-117">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="a7338-118">Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI.</span><span class="sxs-lookup"><span data-stu-id="a7338-118">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="a7338-119">En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-119">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="a7338-120">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="a7338-120">Returns</span></span>
<span data-ttu-id="a7338-121">Devuelve el [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) inicializado si es correcto; de lo contrario, es nulo.</span><span class="sxs-lookup"><span data-stu-id="a7338-121">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>

### <a name="initwithfallbackuri"></a><span data-ttu-id="a7338-122">initWithFallbackUri</span><span class="sxs-lookup"><span data-stu-id="a7338-122">initWithFallbackUri</span></span>
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

<span data-ttu-id="a7338-123">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="a7338-123">Creates and initializes a new instance of this class.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a7338-124">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a7338-124">Parameters</span></span>
* `fallbackUri` 

<span data-ttu-id="a7338-125">URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-125">The fallback URI to launch on the web in case the app launch URI fails.</span></span>

* `preferredPackageIds` 

<span data-ttu-id="a7338-126">Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI.</span><span class="sxs-lookup"><span data-stu-id="a7338-126">A list of **NSString** objects representing IDs of the apps that should be able to launch with this URI.</span></span> <span data-ttu-id="a7338-127">En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a7338-127">For Windows apps, the ID will be the app's package family name.</span></span>

#### <a name="returns"></a><span data-ttu-id="a7338-128">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="a7338-128">Returns</span></span>
<span data-ttu-id="a7338-129">Devuelve el [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) inicializado si es correcto; de lo contrario, es nulo.</span><span class="sxs-lookup"><span data-stu-id="a7338-129">Returns the initialized [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) if successful, otherwise nil.</span></span>