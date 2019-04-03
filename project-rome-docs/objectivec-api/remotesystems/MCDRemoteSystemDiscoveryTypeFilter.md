---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Una clase utilizada para filtrar según el tipo de detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 8054d378f203d5cde29af6b4452cc03e15e24828
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907527"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>Clase `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

Una clase utilizada para filtrar según el tipo de detección de sistemas remotos.

## <a name="properties"></a>Propiedades

### <a name="type"></a>Tipo
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

El tipo de detección para filtrar.

> Nota: En Android, la plataforma de dispositivos conectados solo puede usar Bluetooth en sistemas que ejecutan Android 8.0 (Oreo) o una versión posterior.

## <a name="constructors"></a>Constructores

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Parámetros 
* `discoveryType` El tipo de detección para filtrar.

#### <a name="returns"></a>Devuelve
Una nueva instancia de esta clase con el valor del tipo especificado. Los valores pueden estar unidos por and conjuntamente para aplicar varios filtros a la vez.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Parámetros 
* `discoveryType` El tipo de detección para filtrar.

#### <a name="returns"></a>Devuelve
Una nueva instancia de esta clase con el valor del tipo especificado. Los valores pueden estar unidos por and conjuntamente para aplicar varios filtros a la vez.