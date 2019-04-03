---
title: MCDEventSubscription
description: Esta interfaz proporciona una suscripción de eventos simples.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: ce5a5782f80b54e78a6e3890cd68d9e92c52226c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909477"
---
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="dc905-104">Clase `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="dc905-104">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="dc905-105">Esta interfaz proporciona una suscripción de eventos simples.</span><span class="sxs-lookup"><span data-stu-id="dc905-105">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="dc905-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="dc905-106">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="dc905-107">Cancelar</span><span class="sxs-lookup"><span data-stu-id="dc905-107">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="dc905-108">Cancela una suscripción de eventos.</span><span class="sxs-lookup"><span data-stu-id="dc905-108">Cancels an event subscription.</span></span> <span data-ttu-id="dc905-109">Después de realizar esta llamada, la adjunta EventListener no recibirá más eventos (es posible que todavía se entreguen ya en los eventos de vuelo).</span><span class="sxs-lookup"><span data-stu-id="dc905-109">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="dc905-110">Dado que muchas de las funcionalidades de ConnectedDevices se realiza en código nativo, es importante o bien asegúrese siempre de cancelar se denomina o WeakReferences se usan para garantizar la correcta de limpieza de los recursos mantenidos por el EventListener.</span><span class="sxs-lookup"><span data-stu-id="dc905-110">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
