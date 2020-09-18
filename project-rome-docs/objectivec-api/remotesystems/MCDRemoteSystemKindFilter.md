---
title: MCDRemoteSystemKindFilter
description: Obtenga información sobre la clase MCDRemoteSystemKindFilter. Esta clase se usa para filtrar los sistemas remotos en función del tipo de dispositivo.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: eb0799fe3c2c9831c7963d2d062f39fbf458689e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760679"
---
# <a name="class-mcdremotesystemkindfilter"></a>las `MCDRemoteSystemKindFilter` 

```
@interface MCDRemoteSystemKindFilter : NSObject <MCDRemoteSystemFilter>
```  

Una clase que se usa para filtrar sistemas remotos en función del tipo de dispositivo.

## <a name="properties"></a>Propiedades

### <a name="kinds"></a>categorías
`@property(nonatomic, readonly, copy, nonnull) NSArray<NSString*>* kinds;`

Matriz de cadenas que indica los tipos de dispositivo que se van a filtrar.

## <a name="constructors"></a>Constructores

### <a name="filterwithkinds"></a>filterWithKinds
`+ (nullable instancetype)filterWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Nueva instancia de esta clase filtrada en tipos.

#### <a name="parameters"></a>Parámetros 
* `kinds`

 Matriz de cadenas que indica los tipos de dispositivos que se van a filtrar.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemKindFilter filtrado con tipos.

### <a name="initwithkinds"></a>initWithKinds
`- (nullable instancetype)initWithKinds:(nonnull NSArray<NSString*>*)kinds;`

Nueva instancia de esta clase filtrada en tipos.

#### <a name="parameters"></a>Parámetros 
* `kinds` 

Matriz de cadenas que indica los tipos de dispositivos que se van a filtrar.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemKindFilter inicializado con tipos.