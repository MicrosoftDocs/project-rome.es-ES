---
title: MCDConnectedDevicesProcessNotificationOperation
description: El resultado de dar una notificación a la plataforma de Roma para su procesamiento.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: cb482e7b00cd5fe090de1708388d140cfd45777b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909897"
---
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a>Clase `MCDConnectedDevicesProcessNotificationOperation` 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
El resultado de dar una notificación de APNS para la plataforma de dispositivos conectados para su procesamiento.

> [!NOTE] 
> Esta clase está en desuso, utilice MCDConnectedDevicesNotification en su lugar. 

## <a name="properties"></a>Propiedades

### <a name="connecteddevicesnotification"></a>connectedDevicesNotification
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

Se trata de una marca que indica si la notificación se diseñó para la plataforma de dispositivos conectados.

## <a name="methods"></a>Métodos

### <a name="waitforcompletionasync"></a>waitForCompletionAsync
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 Espere a que la notificación para finalizar está controlando.

#### <a name="parameters"></a>Parámetros 
* `callback` 

El resultado de la devolución de llamada de finalización de la notificación.
