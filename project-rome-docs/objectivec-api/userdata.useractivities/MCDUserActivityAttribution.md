---
title: MCDUserActivityAttribution
description: Esta clase administra los elementos gráficos de una actividad de usuario.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 94ae2f5afef24a1f4e320014ac930d67b657b0d7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909257"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="a0d1b-104">Clase `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="a0d1b-104">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="a0d1b-105">Esta clase administra los elementos gráficos de una actividad de usuario.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-105">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="a0d1b-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a0d1b-106">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="a0d1b-107">iconUri</span><span class="sxs-lookup"><span data-stu-id="a0d1b-107">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a0d1b-108">El URI para la imagen del icono.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-108">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="a0d1b-109">alternateText</span><span class="sxs-lookup"><span data-stu-id="a0d1b-109">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="a0d1b-110">El texto que describe la imagen del icono (para su uso con los lectores de pantalla).</span><span class="sxs-lookup"><span data-stu-id="a0d1b-110">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="a0d1b-111">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="a0d1b-111">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="a0d1b-112">Determina si se permite Windows anexar una cadena de consulta para el URI proporcionado desde una imagen **IconUri** al recuperar la imagen.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-112">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="a0d1b-113">La cadena de consulta incluye información que puede ayudar a seleccionar la imagen ideal basándose en el valor de PPP de la pantalla del usuario, la configuración de contraste alto y el idioma del usuario.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-113">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="a0d1b-114">Esta cadena de consulta especifica la escala, configuración de contraste y lenguaje; Por ejemplo, un **IconUri** valor de "www.website.com/images/hello.png" se convierte en "www.website.com/images/hello.png?ms-scale=100 & ms contraste = standard & ms-lang = en-nosotros".</span><span class="sxs-lookup"><span data-stu-id="a0d1b-114">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="a0d1b-115">Constructores</span><span class="sxs-lookup"><span data-stu-id="a0d1b-115">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="a0d1b-116">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="a0d1b-116">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a0d1b-117">Crea una instancia de esta clase con un URI del icono.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-117">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a0d1b-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a0d1b-118">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="a0d1b-119">Valor de cadena de un URI del icono de pertenecer a la instancia creada.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-119">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="a0d1b-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a0d1b-120">Returns</span></span>
<span data-ttu-id="a0d1b-121">Devuelve un objeto MCDUserActivityAttribution inicializado con un uri del icono.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-121">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="a0d1b-122">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="a0d1b-122">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="a0d1b-123">Crea una instancia de esta clase con atribución a un uri del icono.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-123">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a0d1b-124">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a0d1b-124">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="a0d1b-125">Valor de cadena de un URI del icono de pertenecer a la instancia creada.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-125">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="a0d1b-126">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a0d1b-126">Returns</span></span>
<span data-ttu-id="a0d1b-127">Devuelve un objeto MCDUserActivityAttribution atribución con un uri del icono.</span><span class="sxs-lookup"><span data-stu-id="a0d1b-127">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>