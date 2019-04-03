---
title: MCDAppServiceRequest
description: Representa un mensaje entrante de un aplicación o dispositivo remoto para esta conexión de servicio de aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907577"
---
# <a name="class-mcdappservicerequest"></a>Clase `MCDAppServiceRequest`

```
@interface MCDAppServiceRequest : NSObject
```
Representa un mensaje entrante de un aplicación o dispositivo remoto para esta conexión de servicio de aplicación.

## <a name="properties"></a>Propiedades

### <a name="message"></a>mensaje 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

El mensaje para el servicio de aplicación remota.

## <a name="methods"></a>Métodos

### <a name="sendresponseasync"></a>sendResponseAsync 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

Envía un mensaje de respuesta para el servicio de aplicación remota que envió la solicitud.

#### <a name="parameters"></a>Parámetros
* `message` 

El mensaje para el servicio de aplicación remota.

* `completion`     

La finalización de la operación asincrónica con un valor MCDAppServiceResponseStatus que indica el estado de la operación de envío.