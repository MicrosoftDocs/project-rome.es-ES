---
title: MCDAppServiceRequestReceivedEventArgs
description: Contiene los datos asociados a un evento "recibe la solicitud".
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5fa7a3b2742d5ecacd7c6a90e39e86f4c46f2218
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800647"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a><span data-ttu-id="02e3e-104">Clase `MCDAppServiceRequestReceivedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="02e3e-104">class `MCDAppServiceRequestReceivedEventArgs`</span></span> 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
<span data-ttu-id="02e3e-105">Contiene los datos asociados a un evento "recibe la solicitud".</span><span class="sxs-lookup"><span data-stu-id="02e3e-105">Contains data associated with a "request received" event.</span></span>

## <a name="properties"></a><span data-ttu-id="02e3e-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="02e3e-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="02e3e-107">solicitud</span><span class="sxs-lookup"><span data-stu-id="02e3e-107">request</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

<span data-ttu-id="02e3e-108">La solicitud enviada por el dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="02e3e-108">The request sent by the remote device.</span></span>