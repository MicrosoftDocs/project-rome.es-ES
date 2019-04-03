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
# <a name="class-mcduseractivityattribution"></a>Clase `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

Esta clase administra los elementos gráficos de una actividad de usuario.

## <a name="properties"></a>Propiedades

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

El URI para la imagen del icono.

### <a name="alternatetext"></a>alternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

El texto que describe la imagen del icono (para su uso con los lectores de pantalla).

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

Determina si se permite Windows anexar una cadena de consulta para el URI proporcionado desde una imagen **IconUri** al recuperar la imagen. La cadena de consulta incluye información que puede ayudar a seleccionar la imagen ideal basándose en el valor de PPP de la pantalla del usuario, la configuración de contraste alto y el idioma del usuario. Esta cadena de consulta especifica la escala, configuración de contraste y lenguaje; Por ejemplo, un **IconUri** valor de "www.website.com/images/hello.png" se convierte en "www.website.com/images/hello.png?ms-scale=100 & ms contraste = standard & ms-lang = en-nosotros".

## <a name="constructors"></a>Constructores

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

Crea una instancia de esta clase con un URI del icono.

#### <a name="parameters"></a>Parámetros
* `iconUri` 

Valor de cadena de un URI del icono de pertenecer a la instancia creada.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDUserActivityAttribution inicializado con un uri del icono.

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

Crea una instancia de esta clase con atribución a un uri del icono.

#### <a name="parameters"></a>Parámetros
* `iconUri` 

Valor de cadena de un URI del icono de pertenecer a la instancia creada.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDUserActivityAttribution atribución con un uri del icono.