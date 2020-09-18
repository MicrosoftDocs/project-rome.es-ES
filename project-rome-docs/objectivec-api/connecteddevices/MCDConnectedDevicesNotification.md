---
title: MCDConnectedDevicesNotification
description: Obtenga información sobre la clase MCDConnectedDevicesNotification. Esta clase es el resultado del procesamiento de una notificación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761019"
---
# <a name="class-mcdconnecteddevicesnotification"></a>las `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
Resultado del procesamiento de una notificación.

## <a name="methods"></a>Métodos

### <a name="tryparse"></a>tryParse

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

Intenta analizar un MCDConnectedDevicesNotification a partir de un mapa con formato de APNS.

#### <a name="parameters"></a>Parámetros 
* `dictionary` 

Asignación recibida de la notificación de APNS a la plataforma de dispositivos conectados para su procesamiento.
