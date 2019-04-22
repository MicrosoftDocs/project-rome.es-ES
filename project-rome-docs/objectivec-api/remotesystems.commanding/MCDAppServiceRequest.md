---
title: MCDAppServiceRequest
description: Representa un mensaje entrante de un aplicación o dispositivo remoto para esta conexión de servicio de aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800537"
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