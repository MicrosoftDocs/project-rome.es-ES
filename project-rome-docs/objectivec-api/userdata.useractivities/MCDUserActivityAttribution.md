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
# <a name="class-mcduseractivityattribution"></a>las `MCDUserActivityAttribution`

```
@interface MCDUserActivityAttribution : NSObject
```

Esta clase administra los elementos gráficos de una actividad de usuario.

## <a name="properties"></a>Propiedades

### <a name="iconuri"></a>iconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

El URI de la imagen del icono.

### <a name="alternatetext"></a>alternateText
`@property(nonatomic, copy, nonnull) NSString* alternateText;`

Texto que describe la imagen de icono (para su uso con lectores de pantalla).

### <a name="addimagequery"></a>addImageQuery
`@property(nonatomic, assign) BOOL addImageQuery;`

Determina si se permite a Windows anexar una cadena de consulta al identificador URI de la imagen proporcionado desde **IconUri** al recuperar la imagen. La cadena de consulta incluye información que puede ayudar a seleccionar la imagen ideal en función del valor de PPP de la pantalla del usuario, la configuración de contraste alto y el idioma del usuario. Esta cadena de consulta especifica la escala, la configuración de contraste y el idioma; por ejemplo, un valor **IconUri** de "www.website.com/images/hello.png" se convierte en "www.website.com/images/hello.png? MS-Scale = 100&MS-Contrast = Standard&MS-lang = en-US".

## <a name="constructors"></a>Constructores

### <a name="useractivityattributionwithiconuri"></a>userActivityAttributionWithIconUri
`+ (nullable instancetype)userActivityAttributionWithIconUri:(nonnull NSString*)iconUri;`

Crea una instancia de esta clase con un URI de icono.

#### <a name="parameters"></a>Parámetros
* `iconUri` 

Valor de cadena de un URI de icono que pertenece a la instancia creada.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDUserActivityAttribution inicializado con un URI de icono.

### <a name="attributionwithiconuri"></a>attributionWithIconUri
`+ (nullable instancetype)attributionWithIconUri:(nonnull NSString*)iconUri;`

Crea una instancia de esta clase con atribución a un URI de icono.

#### <a name="parameters"></a>Parámetros
* `iconUri` 

Valor de cadena de un URI de icono que pertenece a la instancia creada.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDUserActivityAttribution que atribuye un URI de icono.