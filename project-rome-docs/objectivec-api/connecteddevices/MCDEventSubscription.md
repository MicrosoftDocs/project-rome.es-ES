---
title: MCDEventSubscription
description: Obtenga información sobre la clase MCDEventSubscription. Esta interfaz proporciona una manera sencilla de administrar una suscripción de eventos.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 8f44d1ca75ea247f2cb26fe5b2c136b4db0bd97f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761079"
---
# <a name="class-mcdeventsubscription"></a>las `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
Esta interfaz proporciona una suscripción de eventos simple.

## <a name="methods"></a>Métodos

### <a name="cancel"></a>cancel
`- (void)cancel;`

Cancela una suscripción de eventos. Después de realizar esta llamada, el EventListener adjunto no recibirá más eventos (ya se pueden entregar eventos de vuelo).
Dado que gran parte de la funcionalidad de ConnectedDevices se realiza en código nativo, es importante asegurarse siempre de que se llame a Cancel o se usen WeakReferences para garantizar una limpieza correcta de los recursos mantenidos por el EventListener.
