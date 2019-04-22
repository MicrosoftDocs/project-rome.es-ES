---
title: MCDStatelessAppServiceResponse
description: Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801627"
---
# <a name="class-mcdstatelessappserviceresponse"></a><span data-ttu-id="e19c0-104">Clase `MCDStatelessAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="e19c0-104">class `MCDStatelessAppServiceResponse`</span></span> 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

<span data-ttu-id="e19c0-105">Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.</span><span class="sxs-lookup"><span data-stu-id="e19c0-105">Represents a message passed from a remote app service to the client app in response to a previous call to MCDAppServiceConnection.sendStatelessMessageAsync.</span></span>


## <a name="properties"></a><span data-ttu-id="e19c0-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="e19c0-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="e19c0-107">mensaje</span><span class="sxs-lookup"><span data-stu-id="e19c0-107">message</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="e19c0-108">El mensaje enviado por el servicio de aplicación remota, que consta de pares clave/valor.</span><span class="sxs-lookup"><span data-stu-id="e19c0-108">The message sent by the remote app service, consisting of key/value pairs.</span></span>

### <a name="status"></a><span data-ttu-id="e19c0-109">status</span><span class="sxs-lookup"><span data-stu-id="e19c0-109">status</span></span>
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

<span data-ttu-id="e19c0-110">El estado de la respuesta del servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="e19c0-110">The status of the response from the remote app service.</span></span>

