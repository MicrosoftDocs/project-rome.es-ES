---
title: MCDRemoteSystemLocalVisibilityKindFilter
description: Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b54614c1ee0a820e605df05768c164d07a5a9464
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800677"
---
# <a name="class-mcdremotesystemlocalvisibilitykindfilter"></a>Clase `MCDRemoteSystemLocalVisibilityKindFilter` 

```
@interface MCDRemoteSystemLocalVisibilityKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Una clase que se usa para establecer la preferencia de visibilidad de aplicación (llamada) local durante la detección de sistemas remotos.

## <a name="properties"></a>Propiedades

### <a name="kind"></a>Tipo
`@property(nonatomic, readonly) MCDRemoteSystemLocalVisibilityKind kind;`

Para filtrar con la configuración de visibilidad.

## <a name="constructors"></a>Constructores

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

Crea e inicializa una instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `localVisibilityKind` 

Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemLocalVisibilityKind filtrado por tipo.

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemLocalVisibilityKind)localVisibilityKind;`

Crea e inicializa una instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `localVisibilityKind` 

Un valor de MCDRemoteSystemLocalVisibilityKind que indica la configuración de visibilidad de la aplicación local para filtrar con.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemLocalVisibilityKind inicializado con tipo.