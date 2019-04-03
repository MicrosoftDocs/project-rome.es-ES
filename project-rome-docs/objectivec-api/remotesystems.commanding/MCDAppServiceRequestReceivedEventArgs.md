---
title: MCDAppServiceRequestReceivedEventArgs
description: Contiene los datos asociados a un evento "recibe la solicitud".
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908567"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="51675-104">Clase `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="51675-104">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="51675-105">Contiene los datos asociados a un evento "recibe la solicitud".</span><span class="sxs-lookup"><span data-stu-id="51675-105">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="51675-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="51675-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="51675-107">solicitud</span><span class="sxs-lookup"><span data-stu-id="51675-107">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="51675-108">La solicitud enviada por el dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="51675-108">The request sent by the remote device.</span></span>