---
title: MCDUserActivityVisualElements
description: Esta clase contiene la información visual, como la descripción y el icono, que se puede mostrar en el icono "Detalles" para un MCDUserActivity.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907417"
---
# <a name="class-mcduseractivityvisualelements"></a><span data-ttu-id="5a4fa-104">Clase `MCDUserActivityVisualElements`</span><span class="sxs-lookup"><span data-stu-id="5a4fa-104">class `MCDUserActivityVisualElements`</span></span>

```
@interface MCDUserActivityVisualElements : NSObject 
```

<span data-ttu-id="5a4fa-105">Esta clase contiene la información visual, como la descripción y el icono, que se puede mostrar en el icono "Detalles" para un MCDUserActivity.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-105">This class contains the visual information, such as the description and icon, that can be shown in the "details" tile for a MCDUserActivity.</span></span>

## <a name="properties"></a><span data-ttu-id="5a4fa-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="5a4fa-106">Properties</span></span>

### <a name="displaytext"></a><span data-ttu-id="5a4fa-107">displayText</span><span class="sxs-lookup"><span data-stu-id="5a4fa-107">displayText</span></span>
`@property(nonatomic, copy, nonnull) NSString* displayText;`

<span data-ttu-id="5a4fa-108">El texto para mostrar para el icono "Detalles" de la actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-108">The display text for the "details" tile of the activity.</span></span>

### <a name="descriptiontext"></a><span data-ttu-id="5a4fa-109">descriptionText</span><span class="sxs-lookup"><span data-stu-id="5a4fa-109">descriptionText</span></span>
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

<span data-ttu-id="5a4fa-110">El texto de descripción para el icono "Detalles" de la actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-110">The description text for the "details" tile of the activity.</span></span>

### <a name="backgroundcolor"></a><span data-ttu-id="5a4fa-111">backgroundColor</span><span class="sxs-lookup"><span data-stu-id="5a4fa-111">backgroundColor</span></span>
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

<span data-ttu-id="5a4fa-112">El color de fondo del icono de la actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-112">The background color for the tile of the activity.</span></span>

### <a name="attribution"></a><span data-ttu-id="5a4fa-113">Atribución</span><span class="sxs-lookup"><span data-stu-id="5a4fa-113">attribution</span></span>
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

<span data-ttu-id="5a4fa-114">La información gráfica acerca de la actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-114">The graphical information about the activity.</span></span>

### <a name="adaptivecardjson"></a><span data-ttu-id="5a4fa-115">adaptiveCardJson</span><span class="sxs-lookup"><span data-stu-id="5a4fa-115">adaptiveCardJson</span></span>
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

<span data-ttu-id="5a4fa-116">El texto del contenido para el icono "Detalles" de la actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-116">The content text for the "details" tile of the activity.</span></span>

### <a name="attributiondisplaytext"></a><span data-ttu-id="5a4fa-117">attributionDisplayText</span><span class="sxs-lookup"><span data-stu-id="5a4fa-117">attributionDisplayText</span></span>
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

<span data-ttu-id="5a4fa-118">El texto que se muestra en el titular superior de la tarjeta de actividad.</span><span class="sxs-lookup"><span data-stu-id="5a4fa-118">The text that is shown in the top banner of the activity card.</span></span>