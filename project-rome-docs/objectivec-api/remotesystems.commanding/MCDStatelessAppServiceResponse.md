---
title: MCDStatelessAppServiceResponse
description: Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801627"
---
# <a name="class-mcdstatelessappserviceresponse"></a>Clase `MCDStatelessAppServiceResponse` 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.


## <a name="properties"></a>Propiedades

### <a name="message"></a>mensaje
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

El mensaje enviado por el servicio de aplicación remota, que consta de pares clave/valor.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

El estado de la respuesta del servicio de aplicación remota.

