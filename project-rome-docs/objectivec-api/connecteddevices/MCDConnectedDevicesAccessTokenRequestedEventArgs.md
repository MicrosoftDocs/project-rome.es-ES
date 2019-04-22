---
title: MCDConnectedDevicesAccessTokenRequestedEventArgs
description: Devuelve MCDConnectedDevicesAccessTokenRequested, que se desencadena cuando hay una necesidad de solicitar un token.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: d50b7dc75944e3c3df553c95247b0ec578a477a4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800747"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequestedeventargs"></a><span data-ttu-id="6848b-104">Clase `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="6848b-104">class `MCDConnectedDevicesAccessTokenRequestedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequestedEventArgs : NSObject
```  

<span data-ttu-id="6848b-105">Devuelve MCDConnectedDevicesAccessTokenRequested, que se desencadena cuando hay una necesidad de solicitar un token.</span><span class="sxs-lookup"><span data-stu-id="6848b-105">Returned by MCDConnectedDevicesAccessTokenRequested, fired when there is a need to request a token.</span></span> 

## <a name="properties"></a><span data-ttu-id="6848b-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="6848b-106">Properties</span></span>

### <a name="request"></a><span data-ttu-id="6848b-107">solicitud</span><span class="sxs-lookup"><span data-stu-id="6848b-107">request</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccessTokenRequest* request;`

<span data-ttu-id="6848b-108">La solicitud asociada con este MCDConnectedDevicesAccessTokenRequest.</span><span class="sxs-lookup"><span data-stu-id="6848b-108">The request associated with this MCDConnectedDevicesAccessTokenRequest.</span></span>