---
title: MCDRemoteSystemDiscoveryTypeFilter
description: Obtenga información sobre la clase MCDRemoteSystemDiscoveryTypeFilter. Esta clase se usa para filtrar los sistemas remotos según el tipo de detección.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a38036811fda38df944e67e431f864c33d1c335d
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760699"
---
# <a name="class-mcdremotesystemdiscoverytypefilter"></a>las `MCDRemoteSystemDiscoveryTypeFilter` 

```
@interface MCDRemoteSystemDiscoveryTypeFilter : NSObject<MCDRemoteSystemFilter>
```  

Clase utilizada para filtrar los sistemas remotos según el tipo de detección.

## <a name="properties"></a>Propiedades

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDRemoteSystemDiscoveryType type;`

Tipo de detección que se va a filtrar.

> Nota: en Android, la plataforma de dispositivos conectados solo puede usar Bluetooth en sistemas que ejecutan Android 8,0 (Oreo) o posterior.

## <a name="constructors"></a>Constructores

### <a name="filterwithtype"></a>filterWithType
`+ (nullable instancetype)filterWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Parámetros 
* `discoveryType` Tipo de detección que se va a filtrar.

#### <a name="returns"></a>Devoluciones
Nueva instancia de esta clase con el valor de tipo especificado. Los valores se pueden AND'ed juntos para aplicar varios filtros a la vez.

### <a name="initwithtype"></a>initWithType
`- (nullable instancetype)initWithType:(MCDRemoteSystemDiscoveryType)discoveryType;`

#### <a name="parameters"></a>Parámetros 
* `discoveryType` Tipo de detección que se va a filtrar.

#### <a name="returns"></a>Devoluciones
Nueva instancia de esta clase con el valor de tipo especificado. Los valores se pueden AND'ed juntos para aplicar varios filtros a la vez.