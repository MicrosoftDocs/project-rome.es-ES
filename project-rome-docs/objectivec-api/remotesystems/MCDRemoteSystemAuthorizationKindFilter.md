---
title: MCDRemoteSystemAuthorizationKindFilter
description: Obtenga información sobre la clase MCDRemoteSystemAuthorizationKindFilter. Esta clase se usa para filtrar los sistemas remotos según el tipo de autorización.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a48c9aeacf262146a12da6fd691e853cb7dde199
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760709"
---
# <a name="class-mcdremotesystemauthorizationkindfilter"></a>las `MCDRemoteSystemAuthorizationKindFilter` 

```
@interface MCDRemoteSystemAuthorizationKindFilter : NSObject<MCDRemoteSystemFilter>
```  

Clase utilizada para filtrar los sistemas remotos según el tipo de autorización.

## <a name="properties"></a>Propiedades

### <a name="kind"></a>kind
`@property(nonatomic, readonly) MCDRemoteSystemAuthorizationKind kind;`

Tipo de autorización para filtrar.

## <a name="constructors"></a>Constructores

### <a name="filterwithkind"></a>filterWithKind
`+ (nullable instancetype)filterWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Nueva instancia de esta clase filtrada en MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Parámetros 
* `authorizationKind` 

Tipo de autorización para filtrar.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter con el filtro de autorización proporcionado.

### <a name="initwithkind"></a>initWithKind
`- (nullable instancetype)initWithKind:(MCDRemoteSystemAuthorizationKind)authorizationKind;`

Nueva instancia de esta clase con MCDRemoteSystemAuthorizationKind.

#### <a name="parameters"></a>Parámetros 
* `authorizationKind` 

Tipo de autorización para filtrar.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemAuthorizationKindFilter inicializado con authorizationKind.