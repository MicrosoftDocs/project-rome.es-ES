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
# <a name="class-mcdevent"></a><span data-ttu-id="55e37-105">Clase `MCDEvent`</span><span class="sxs-lookup"><span data-stu-id="55e37-105">class `MCDEvent`</span></span> 

```
@interface MCDEvent<__covariant SourceType, __covariant ArgsType> : NSObject
```  
 
 <span data-ttu-id="55e37-106">Esta interfaz proporciona un modelo de evento simple.</span><span class="sxs-lookup"><span data-stu-id="55e37-106">This interface provides a simple event model.</span></span> <span data-ttu-id="55e37-107">Eventos de generan elementos consumidos por los elementos EventListener.</span><span class="sxs-lookup"><span data-stu-id="55e37-107">Events produce items consumed by EventListeners.</span></span>
<span data-ttu-id="55e37-108">El flujo de elementos de evento está controlado por la MCDEventSubscription.</span><span class="sxs-lookup"><span data-stu-id="55e37-108">The flow of event items is controlled by the MCDEventSubscription.</span></span>

## <a name="methods"></a><span data-ttu-id="55e37-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="55e37-109">Methods</span></span>

### <a name="subscribe"></a><span data-ttu-id="55e37-110">suscribirse</span><span class="sxs-lookup"><span data-stu-id="55e37-110">subscribe</span></span>
`- (nonnull MCDEventSubscription*)subscribe:(nonnull void (^)(SourceType _Nonnull, ArgsType _Nonnull))listener;`

<span data-ttu-id="55e37-111">Suscríbase a dado de los eventos de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="55e37-111">Subscribe to given events in the Connected Devices Platform.</span></span>

#### <a name="parameters"></a><span data-ttu-id="55e37-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="55e37-112">Parameters</span></span> 
* `listener` 

<span data-ttu-id="55e37-113">Escuchar MCDEventSubscriptions.</span><span class="sxs-lookup"><span data-stu-id="55e37-113">Listen to MCDEventSubscriptions.</span></span>

#### <a name="returns"></a><span data-ttu-id="55e37-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="55e37-114">Returns</span></span>
<span data-ttu-id="55e37-115">Una instancia de la MCDEventSubscription.</span><span class="sxs-lookup"><span data-stu-id="55e37-115">An instance of the MCDEventSubscription.</span></span>