---
title: MCDAppServiceResponseStatus
description: Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908947"
---
# <a name="enum-mcdappserviceresponsestatus"></a>Enum `MCDAppServiceResponseStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.

|Nombre         | Valor  | Descripción    |                           
|--------|-------------|-----|
|MCDAppServiceResponseStatusSuccess |0| El servicio de aplicación correctamente había recibido y procesado el mensaje.|
|MCDAppServiceResponseStatusFailure |1| El servicio de aplicación no se pudo recibir y procesar el mensaje.|
|MCDAppServiceResponseStatusResourceLimitsExceeded |2| El servicio de aplicación se cerró porque no hay suficientes recursos, no estaban disponibles.|
|MCDAppServiceResponseStatusUnknown |3| Se produjo un error desconocido.|
|MCDAppServiceResponseStatusRemoteSystemUnavailable |4| El dispositivo al que se envió el mensaje no está disponible.|
|MCDAppServiceResponseStatusMessageTooLarge |5| El servicio de aplicación no se pudo procesar el mensaje porque es demasiado grande.|
|MCDAppServiceResponseStatusAppServiceConnectionClosed|6| Se cerró la conexión de servicio de aplicación antes de que se envió una respuesta.|