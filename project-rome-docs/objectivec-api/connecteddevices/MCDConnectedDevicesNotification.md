---
title: MCDConnectedDevicesNotification
description: Resultado de procesar una notificación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908717"
---
# <a name="class-mcdconnecteddevicesnotification"></a>Clase `MCDConnectedDevicesNotification` 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
Resultado de procesar una notificación.

## <a name="methods"></a>Métodos

### <a name="tryparse"></a>tryParse

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

Intenta analizar un MCDConnectedDevicesNotification desde un APN tiene un formato de mapa.

#### <a name="parameters"></a>Parámetros 
* `dictionary` 

El mapa recibido de la notificación de APNS para la plataforma de dispositivos conectados para su procesamiento.
