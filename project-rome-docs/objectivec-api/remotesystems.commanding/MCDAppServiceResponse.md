---
title: MCDAppServiceResponse
description: Una clase que representa una respuesta recibida de un servicio de aplicación remota conectada.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800797"
---
# <a name="class-mcdappserviceresponse"></a>Clase `MCDAppServiceResponse`

```
@interface MCDAppServiceResponse : NSObject
```

Una clase que representa una respuesta recibida de un servicio de aplicación remota conectada.

## <a name="properties"></a>Propiedades

### <a name="message"></a>mensaje 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

El mensaje recibido desde el servicio de aplicación remota.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

El estado de la respuesta recibida.