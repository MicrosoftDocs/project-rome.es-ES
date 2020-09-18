---
title: MCDUserActivityAttribution
description: Obtenga información sobre la clase MCDUserActivityAttribution. Esta clase administra los elementos gráficos de una actividad de usuario.
keywords: Microsoft, Windows, actividades de usuario, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: e4cf9f078215e987c2f0e8068c4afdf640409acc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760199"
---
# <a name="class-mcduseractivityattribution"></a><span data-ttu-id="b19b3-105">las `MCDUserActivityAttribution`</span><span class="sxs-lookup"><span data-stu-id="b19b3-105">class `MCDUserActivityAttribution`</span></span>

```
@interface MCDUserActivityAttribution : NSObject
```

<span data-ttu-id="b19b3-106">Esta clase administra los elementos gráficos de una actividad de usuario.</span><span class="sxs-lookup"><span data-stu-id="b19b3-106">This class manages the graphical elements of a user activity.</span></span>

## <a name="properties"></a><span data-ttu-id="b19b3-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b19b3-107">Properties</span></span>

### <a name="iconuri"></a><span data-ttu-id="b19b3-108">iconUri</span><span class="sxs-lookup"><span data-stu-id="b19b3-108">iconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="b19b3-109">El URI de la imagen del icono.</span><span class="sxs-lookup"><span data-stu-id="b19b3-109">The URI for the icon image.</span></span>

### <a name="alternatetext"></a><span data-ttu-id="b19b3-110">alternateText</span><span class="sxs-lookup"><span data-stu-id="b19b3-110">alternateText</span></span>
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

<span data-ttu-id="b19b3-111">Texto que describe la imagen de icono (para su uso con lectores de pantalla).</span><span class="sxs-lookup"><span data-stu-id="b19b3-111">The text that describes the icon image (for use with screen readers).</span></span>

### <a name="addimagequery"></a><span data-ttu-id="b19b3-112">addImageQuery</span><span class="sxs-lookup"><span data-stu-id="b19b3-112">addImageQuery</span></span>
`@property(nonatomic, assign) BOOL addImageQuery;`

<span data-ttu-id="b19b3-113">Determina si se permite a Windows anexar una cadena de consulta al identificador URI de la imagen proporcionado desde **IconUri** al recuperar la imagen.</span><span class="sxs-lookup"><span data-stu-id="b19b3-113">Determines whether to allow Windows to append a query string to the image URI supplied from **IconUri** when retrieving the image.</span></span> <span data-ttu-id="b19b3-114">La cadena de consulta incluye información que puede ayudar a seleccionar la imagen ideal en función del valor de PPP de la pantalla del usuario, la configuración de contraste alto y el idioma del usuario.</span><span class="sxs-lookup"><span data-stu-id="b19b3-114">The query string includes information that can help select the ideal image based on the DPI of the user's display, the high contrast setting, and the user's language.</span></span> <span data-ttu-id="b19b3-115">Esta cadena de consulta especifica la escala, la configuración de contraste y el idioma; por ejemplo, un valor **IconUri** de "www.website.com/images/hello.png" se convierte en "www.website.com/images/hello.png? MS-Scale = 100&MS-Contrast = Standard&MS-lang = en-US".</span><span class="sxs-lookup"><span data-stu-id="b19b3-115">This query string specifies scale, contrast setting, and language; for instance, an **IconUri** value of "www.website.com/images/hello.png" becomes "www.website.com/images/hello.png?ms-scale=100&ms-contrast=standard&ms-lang=en-us".</span></span>

## <a name="constructors"></a><span data-ttu-id="b19b3-116">Constructores</span><span class="sxs-lookup"><span data-stu-id="b19b3-116">Constructors</span></span>

### <a name="useractivityattributionwithiconuri"></a><span data-ttu-id="b19b3-117">userActivityAttributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="b19b3-117">userActivityAttributionWithIconUri</span></span>
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="b19b3-118">Crea una instancia de esta clase con un URI de icono.</span><span class="sxs-lookup"><span data-stu-id="b19b3-118">Creates an instance of this class with an Icon URI.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b19b3-119">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b19b3-119">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="b19b3-120">Valor de cadena de un URI de icono que pertenece a la instancia creada.</span><span class="sxs-lookup"><span data-stu-id="b19b3-120">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="b19b3-121">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="b19b3-121">Returns</span></span>
<span data-ttu-id="b19b3-122">Devuelve un objeto MCDUserActivityAttribution inicializado con un URI de icono.</span><span class="sxs-lookup"><span data-stu-id="b19b3-122">Returns an MCDUserActivityAttribution object initialized with an icon uri.</span></span>

### <a name="attributionwithiconuri"></a><span data-ttu-id="b19b3-123">attributionWithIconUri</span><span class="sxs-lookup"><span data-stu-id="b19b3-123">attributionWithIconUri</span></span>
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

<span data-ttu-id="b19b3-124">Crea una instancia de esta clase con atribución a un URI de icono.</span><span class="sxs-lookup"><span data-stu-id="b19b3-124">Creates an instance of this class with attribution to a icon uri.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b19b3-125">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b19b3-125">Parameters</span></span>
* `iconUri` 

<span data-ttu-id="b19b3-126">Valor de cadena de un URI de icono que pertenece a la instancia creada.</span><span class="sxs-lookup"><span data-stu-id="b19b3-126">A string value of an Icon URI to belong to the created instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="b19b3-127">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="b19b3-127">Returns</span></span>
<span data-ttu-id="b19b3-128">Devuelve un objeto MCDUserActivityAttribution que atribuye un URI de icono.</span><span class="sxs-lookup"><span data-stu-id="b19b3-128">Returns an MCDUserActivityAttribution object attributing with an icon uri.</span></span>