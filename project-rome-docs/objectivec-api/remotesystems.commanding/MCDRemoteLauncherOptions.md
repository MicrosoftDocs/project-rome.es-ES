---
title: MCDRemoteLauncherOptions
description: Una clase que representa las opciones de la característica de inicio remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 628bf1659dfb4ce50e20631622d8a78a322bb2f5
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907337"
---
# <a name="class-mcdremotelauncheroptions"></a>Clase `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

Una clase que representa las opciones de la característica de inicio remoto.

## <a name="properties"></a>Propiedades

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.

### <a name="preferredpackageids"></a>preferredPackageIds
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI. Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.

## <a name="constructors"></a>Constructores

### <a name="optionswithfallbackuri"></a>optionsWithFallbackUri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `fallbackUri` 

Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.

* `preferredPackageIds` 

Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI. Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) si es correcto, en caso contrario nulo.

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `fallbackUri` 

Se produce un error en el URI de reserva para iniciar en la web, en caso de URI de inicio de la aplicación.

* `preferredPackageIds` 

Una lista de **NSString** objetos que representan identificadores de las aplicaciones que deben ser capaces de iniciar con este identificador URI. Para las aplicaciones de Windows, el identificador será el nombre de familia del paquete de la aplicación.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) si es correcto, en caso contrario nulo.