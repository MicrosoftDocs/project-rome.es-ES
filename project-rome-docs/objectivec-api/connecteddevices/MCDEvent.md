---
title: MCDEvent
description: Esta interfaz proporciona un modelo de evento simple. Eventos de generan elementos consumidos por los elementos EventListener.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: eabe9464a104593b06460153ed30f42f7cc103eb
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907257"
---
# <a name="class-mcdevent"></a>Clase `MCDEvent` 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 Esta interfaz proporciona un modelo de evento simple. Eventos de generan elementos consumidos por los elementos EventListener.
El flujo de elementos de evento está controlado por la MCDEventSubscription.

## <a name="methods"></a>Métodos

### <a name="subscribe"></a>suscribirse
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

Suscríbase a dado de los eventos de la plataforma de dispositivos conectados.

#### <a name="parameters"></a>Parámetros 
* `listener` 

Escuchar MCDEventSubscriptions.

#### <a name="returns"></a>Devuelve
Una instancia de la MCDEventSubscription.