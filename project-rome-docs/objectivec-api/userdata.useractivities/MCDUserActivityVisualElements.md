---
title: MCDUserActivityVisualElements
description: Esta clase contiene la información visual, como la descripción y el icono, que se puede mostrar en el icono "Detalles" para un MCDUserActivity.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c969b8a52bc6d2a22fd0a00808f9bb374c63cd8a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801067"
---
# <a name="class-mcduseractivityvisualelements"></a>Clase `MCDUserActivityVisualElements`

```
@interface MCDUserActivityVisualElements : NSObject 
```

Esta clase contiene la información visual, como la descripción y el icono, que se puede mostrar en el icono "Detalles" para un MCDUserActivity.

## <a name="properties"></a>Propiedades

### <a name="displaytext"></a>displayText
`@property(nonatomic, copy, nonnull) NSString* displayText;`

El texto para mostrar para el icono "Detalles" de la actividad.

### <a name="descriptiontext"></a>descriptionText
`@property(nonatomic, copy, nullable) NSString* descriptionText;`

El texto de descripción para el icono "Detalles" de la actividad.

### <a name="backgroundcolor"></a>backgroundColor
`@property(nonatomic, copy, nullable) SKColor* backgroundColor;`

El color de fondo del icono de la actividad.

### <a name="attribution"></a>Atribución
`@property(nonatomic, retain, nullable) MCDUserActivityAttribution* attribution;`

La información gráfica acerca de la actividad.

### <a name="adaptivecardjson"></a>adaptiveCardJson
`@property(nonatomic, copy, nullable) NSString* adaptiveCardJson;`

El texto del contenido para el icono "Detalles" de la actividad.

### <a name="attributiondisplaytext"></a>attributionDisplayText
`@property(nonatomic, copy, nullable) NSString* attributionDisplayText;`

El texto que se muestra en el titular superior de la tarjeta de actividad.