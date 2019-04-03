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
# <a name="class-mcdconnecteddevicesprocessnotificationoperation"></a><span data-ttu-id="4eb70-104">Clase `MCDConnectedDevicesProcessNotificationOperation`</span><span class="sxs-lookup"><span data-stu-id="4eb70-104">class `MCDConnectedDevicesProcessNotificationOperation`</span></span> 

```
@interface MCDConnectedDevicesProcessNotificationOperation : NSObject
```  
<span data-ttu-id="4eb70-105">El resultado de dar una notificación de APNS para la plataforma de dispositivos conectados para su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="4eb70-105">The result of giving an APNS notification to the Connected Devices platform for processing.</span></span>

> [!NOTE] 
> <span data-ttu-id="4eb70-106">Esta clase está en desuso, utilice MCDConnectedDevicesNotification en su lugar.</span><span class="sxs-lookup"><span data-stu-id="4eb70-106">This class is deprecated, use MCDConnectedDevicesNotification instead.</span></span> 

## <a name="properties"></a><span data-ttu-id="4eb70-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4eb70-107">Properties</span></span>

### <a name="connecteddevicesnotification"></a><span data-ttu-id="4eb70-108">connectedDevicesNotification</span><span class="sxs-lookup"><span data-stu-id="4eb70-108">connectedDevicesNotification</span></span>
`@property(nonatomic, readonly, getter=isConnectedDevicesNotification) BOOL connectedDevicesNotification;`

<span data-ttu-id="4eb70-109">Se trata de una marca que indica si la notificación se diseñó para la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="4eb70-109">This is a flag indicating whether the notification was intended for the Connected Devices platform.</span></span>

## <a name="methods"></a><span data-ttu-id="4eb70-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="4eb70-110">Methods</span></span>

### <a name="waitforcompletionasync"></a><span data-ttu-id="4eb70-111">waitForCompletionAsync</span><span class="sxs-lookup"><span data-stu-id="4eb70-111">waitForCompletionAsync</span></span>
`- (void)waitForCompletionAsync:(nonnull void (^)(NSError* _Nullable error))callback;`

 <span data-ttu-id="4eb70-112">Espere a que la notificación para finalizar está controlando.</span><span class="sxs-lookup"><span data-stu-id="4eb70-112">Wait for the notification to finish being handled.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4eb70-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4eb70-113">Parameters</span></span> 
* `callback` 

<span data-ttu-id="4eb70-114">El resultado de la devolución de llamada de finalización de la notificación.</span><span class="sxs-lookup"><span data-stu-id="4eb70-114">The callback result for notification completion.</span></span>
