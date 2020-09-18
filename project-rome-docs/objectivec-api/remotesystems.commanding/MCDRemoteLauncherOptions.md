---
title: MCDRemoteLauncherOptions
description: Obtenga información sobre la clase MCDRemoteLauncherOptions. Esta clase representa las opciones de la característica de inicio remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 2e698ad71282e44d1447e19085598139b67f9270
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760739"
---
# <a name="class-mcdremotelauncheroptions"></a>las `MCDRemoteLauncherOptions` 

```
@interface MCDRemoteLauncherOptions : NSObject
```  

Una clase que representa las opciones de la característica de inicio remoto.

## <a name="properties"></a>Propiedades

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.

### <a name="preferredpackageids"></a>preferredPackageIds
`@property(nonatomic, copy, nullable) NSArray<NSString*>* preferredPackageIds;`

Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI. En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.

## <a name="constructors"></a>Constructores

### <a name="optionswithfallbackuri"></a>optionsWithFallbackUri
`+ (nullable instancetype)optionsWithFallbackUri: (nullable NSString*)fallbackUri  preferredPackageIds: (nullable NSArray<NSString*>*)preferredPackageIds;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `fallbackUri` 

URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.

* `preferredPackageIds` 

Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI. En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.

#### <a name="returns"></a>Devoluciones
Devuelve el [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) inicializado si es correcto; de lo contrario, es nulo.

### <a name="initwithfallbackuri"></a>initWithFallbackUri
`- (nullable instancetype)initWithFallbackUri:(nullable NSString*)fallbackUri preferredPackageIds:(nullable NSArray<NSString*>*)preferredPackageIds;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `fallbackUri` 

URI de reserva que se va a iniciar en la web en caso de que se produzca un error en el URI de inicio de la aplicación.

* `preferredPackageIds` 

Una lista de objetos **NSString** que representan los identificadores de las aplicaciones que deben poder iniciarse con este URI. En el caso de las aplicaciones de Windows, el identificador será el nombre de la familia de paquetes de la aplicación.

#### <a name="returns"></a>Devoluciones
Devuelve el [MCDRemoteLauncherOptions](MCDRemoteLauncherOptions.md) inicializado si es correcto; de lo contrario, es nulo.