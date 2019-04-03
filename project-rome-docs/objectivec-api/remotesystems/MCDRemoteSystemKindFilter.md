---
title: MCDRemoteSystemKindFilter
description: Una clase utilizada para filtrar según el tipo de dispositivo de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 162e8f881b532fae50f6d301149b50c5ddf344b5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907267"
---
# <a name="class-mcdremotesystemkindfilter"></a>Clase `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Una clase utilizada para filtrar según el tipo de dispositivo de sistemas remotos.

## <a name="properties"></a>Propiedades

### <a name="kinds"></a>tipos
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

Una matriz de cadenas que indica los tipos de dispositivo para filtrar.

## <a name="constructors"></a>Constructores

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Una nueva instancia de esta clase filtrada por tipos.

#### <a name="parameters"></a>Parámetros 
* `kinds`

 Una matriz de cadenas que indica los tipos de dispositivo para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemKindFilter filtrado con tipos.

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Una nueva instancia de esta clase filtrada por tipos.

#### <a name="parameters"></a>Parámetros 
* `kinds` 

Una matriz de cadenas que indica los tipos de dispositivo para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemKindFilter inicializado con los tipos.