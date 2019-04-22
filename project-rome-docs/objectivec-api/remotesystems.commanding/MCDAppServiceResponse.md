---
title: MCDAppServiceResponse
description: Una clase que representa una respuesta recibida de un servicio de aplicación remota conectada.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 74cff4a84bdc4bf073dd57319c987e274ea8ceaf
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800797"
---
# <a name="class-mcdappserviceresponse"></a><span data-ttu-id="16d2c-104">Clase `MCDAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="16d2c-104">class `MCDAppServiceResponse`</span></span>

```
@interface MCDAppServiceResponse : NSObject
```

<span data-ttu-id="16d2c-105">Una clase que representa una respuesta recibida de un servicio de aplicación remota conectada.</span><span class="sxs-lookup"><span data-stu-id="16d2c-105">A class that represents a response received from a connected remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="16d2c-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="16d2c-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="16d2c-107">mensaje</span><span class="sxs-lookup"><span data-stu-id="16d2c-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="16d2c-108">El mensaje recibido desde el servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="16d2c-108">The message received from the remote app service.</span></span>

### <a name="status"></a><span data-ttu-id="16d2c-109">status</span><span class="sxs-lookup"><span data-stu-id="16d2c-109">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceResponseStatus status;`

<span data-ttu-id="16d2c-110">El estado de la respuesta recibida.</span><span class="sxs-lookup"><span data-stu-id="16d2c-110">The status of the response received.</span></span>