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
# <a name="class-mcdeventsubscription"></a><span data-ttu-id="0a955-105">las `MCDEventSubscription`</span><span class="sxs-lookup"><span data-stu-id="0a955-105">class `MCDEventSubscription`</span></span> 

```
@interface MCDEventSubscription : NSObject
```  
<span data-ttu-id="0a955-106">Esta interfaz proporciona una suscripción de eventos simple.</span><span class="sxs-lookup"><span data-stu-id="0a955-106">This interface provides a simple event subscription.</span></span>

## <a name="methods"></a><span data-ttu-id="0a955-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="0a955-107">Methods</span></span>

### <a name="cancel"></a><span data-ttu-id="0a955-108">cancel</span><span class="sxs-lookup"><span data-stu-id="0a955-108">cancel</span></span>
`- (void)cancel;`

<span data-ttu-id="0a955-109">Cancela una suscripción de eventos.</span><span class="sxs-lookup"><span data-stu-id="0a955-109">Cancels an event subscription.</span></span> <span data-ttu-id="0a955-110">Después de realizar esta llamada, el EventListener adjunto no recibirá más eventos (ya se pueden entregar eventos de vuelo).</span><span class="sxs-lookup"><span data-stu-id="0a955-110">After making this call, the attached EventListener will not receive any more events (Already in flight events may still be delivered).</span></span>
<span data-ttu-id="0a955-111">Dado que gran parte de la funcionalidad de ConnectedDevices se realiza en código nativo, es importante asegurarse siempre de que se llame a Cancel o se usen WeakReferences para garantizar una limpieza correcta de los recursos mantenidos por el EventListener.</span><span class="sxs-lookup"><span data-stu-id="0a955-111">Because much of the ConnectedDevices functionality is done in native code, it is important to either always ensure cancel is called or WeakReferences are used to ensure proper clean up of resources held by the EventListener.</span></span>
