---
title: MCDEventSubscription
description: Esta interfaz proporciona una suscripción de eventos simples.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: ce5a5782f80b54e78a6e3890cd68d9e92c52226c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801623"
---
# <a name="class-mcdeventsubscription"></a>Clase `MCDEventSubscription` 

```
@interface MCDEventSubscription : NSObject
```  
Esta interfaz proporciona una suscripción de eventos simples.

## <a name="methods"></a>Métodos

### <a name="cancel"></a>Cancelar
`- (void)cancel;`

Cancela una suscripción de eventos. Después de realizar esta llamada, la adjunta EventListener no recibirá más eventos (es posible que todavía se entreguen ya en los eventos de vuelo).
Dado que muchas de las funcionalidades de ConnectedDevices se realiza en código nativo, es importante o bien asegúrese siempre de cancelar se denomina o WeakReferences se usan para garantizar la correcta de limpieza de los recursos mantenidos por el EventListener.
