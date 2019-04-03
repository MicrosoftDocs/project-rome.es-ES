---
title: MCDRemoteSystemConnectionInfo
description: Una clase que proporciona más información acerca de una instancia de MCDAppServiceConnection especificada.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907057"
---
# <a name="class-mcdremotesystemconnectioninfo"></a>Clase `MCDRemoteSystemConnectionInfo` 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

Una clase que proporciona más información acerca de un determinado **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instancia.

## <a name="properties"></a>Propiedades

### <a name="proximal"></a>proximal
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

Muestra si la conexión asociada es una conexión articulaciones próximas (**Sí**) o no (**n**).

## <a name="constructors"></a>Constructores

### <a name="trycreatefromappserviceconnection"></a>tryCreateFromAppServiceConnection
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

Crea una instancia de esta clase de la conexión de servicio de aplicación determinada.

#### <a name="parameters"></a>Parámetros
* `appServiceConnection` 

Un **MCDAppServiceConnection** instancia.

#### <a name="returns"></a>Devuelve
Devuelve una instancia de esta clase correspondiente a la conexión de servicio de aplicación.