---
title: MCDRemoteSystemConnectionRequest
description: Una clase que representa un intento para comunicarse con un dispositivo remoto específico o una aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 54ed7deb1fa2b1c87a3195e61c2ce031d6e0cea9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907137"
---
# <a name="class-mcdremotesystemconnectionrequest"></a>Clase `MCDRemoteSystemConnectionRequest` 

```
@interface MCDRemoteSystemConnectionRequest : NSObject
```  

Una clase que representa un intento para comunicarse con un dispositivo remoto específico o una aplicación.

## <a name="constructors"></a>Constructores

### <a name="requestwithremotesystem"></a>requestWithRemoteSystem
`+ (instancetype)requestWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

Inicializa el [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) con un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instancia. Este constructor no se recomienda, ya que no especifica una aplicación de destino y, por tanto, es posible que en una aplicación inesperada que se ha seleccionado para atender las solicitudes que se envía al sistema.

#### <a name="parameters"></a>Parámetros
* `remoteSystem` 

El sistema remoto como destino en esta solicitud de conexión.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.

### <a name="requestwithremotesystemapp"></a>requestWithRemoteSystemApp
`+ (instancetype)requestWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `remoteSystemApp` 

La aplicación remota como destino en esta solicitud de conexión.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.

### <a name="initwithremotesystem"></a>initWithRemoteSystem
`- (nullable instancetype)initWithRemoteSystem:(nonnull MCDRemoteSystem*)remoteSystem;`

Inicializa el [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) con un [MCDRemoteSystem](../remotesystems/MCDRemoteSystem.md) instancia. Este constructor no se recomienda, ya que no especifica una aplicación de destino y, por tanto, es posible que en una aplicación inesperada que se ha seleccionado para atender las solicitudes que se envía al sistema.

#### <a name="parameters"></a>Parámetros
* `remoteSystem` El sistema remoto como destino en esta solicitud de conexión.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.

### <a name="initwithremotesystemapp"></a>initWithRemoteSystemApp
`- (nullable instancetype)initWithRemoteSystemApp:(nonnull MCDRemoteSystemApp*)remoteSystemApp;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="parameters"></a>Parámetros
* `remoteSystemApp` 

La aplicación remota como destino en esta solicitud de conexión.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md) si es correcto, en caso contrario nulo.