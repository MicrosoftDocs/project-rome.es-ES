---
title: MCDRemoteSystemStatusTypeFilter
description: Una clase utilizada para filtrar según el tipo de estado de disponibilidad de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 201570c16a8eb9cf1a31e450b3408c8ab255fe1a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907127"
---
# <a name="class-mcdremotesystemstatustypefilter"></a>Clase `MCDRemoteSystemStatusTypeFilter`

```
@interface MCDRemoteSystemStatusTypeFilter : NSObject <MCDRemoteSystemFilter>
```

Una clase utilizada para filtrar según el tipo de estado de disponibilidad de sistemas remotos.

## <a name="properties"></a>Propiedades

### <a name="type"></a>Tipo
`@property(nonatomic, readonly) MCDRemoteSystemStatusType type;` El tipo de estado del sistema remoto de esta instancia de filtro.

## <a name="constructors"></a>Constructores

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>Parámetros 
* `statusType` Un valor que indica el tipo de estado de disponibilidad para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemStatusTypeFilter filtrado por tipo.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemStatusType)statusType;`

#### <a name="parameters"></a>Parámetros 
* `statusType` 

Un valor que indica el tipo de estado de disponibilidad para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemStatusTypeFilter inicializado con el tipo.