---
title: MCDRemoteSystemPlatformFilter
description: Una clase utilizada para filtrar los sistemas remotos basados en la plataforma de sistema operativo que se están ejecutando.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 1b82d7b3a1626489a83196bf949567b3ce7b94f0
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908757"
---
# <a name="class-mcdremotesystemplatformfilter"></a>Clase `MCDRemoteSystemPlatformFilter` 

```
@interface MCDRemoteSystemPlatformFilter : NSObject<MCDRemoteSystemFilter> 
```  

Una clase utilizada para filtrar los sistemas remotos basados en la plataforma de sistema operativo que se están ejecutando.

## <a name="properties"></a>Propiedades

### <a name="platform"></a>Plataforma
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.

## <a name="constructors"></a>Constructores

### <a name="filterwithplatform"></a>filterWithPlatform
`+ (nullable instancetype)filterWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>Parámetros 
* `platform` 

Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemPlatformFilter filtrado por plataforma.

### <a name="initwithplatform"></a>initWithPlatform
`- (nullable instancetype)initWithPlatform:(MCDRemoteSystemPlatform)platform;`

#### <a name="parameters"></a>Parámetros 
* `platform` 

Un valor de MCDRemoteSystemPlatform que indica la plataforma para filtrar.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemPlatformFilter inicializado con un filtro por plataforma.