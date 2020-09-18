---
title: MCDAppServiceRequestReceivedEventArgs
description: Obtenga información sobre la clase MCDAppServiceRequestReceivedEventArgs. Esta clase contiene datos asociados a un evento de solicitud recibida.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 9a4a64ae163a0cc553196914da2f42d8d32e6ade
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760769"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="57e99-105">las `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="57e99-105">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="57e99-106">Contiene datos asociados a un evento de "solicitud recibida".</span><span class="sxs-lookup"><span data-stu-id="57e99-106">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="57e99-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="57e99-107">Properties</span></span>

### <a name="request"></a><span data-ttu-id="57e99-108">request</span><span class="sxs-lookup"><span data-stu-id="57e99-108">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="57e99-109">La solicitud enviada por el dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="57e99-109">The request sent by the remote device.</span></span>