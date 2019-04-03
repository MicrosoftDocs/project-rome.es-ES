---
title: MCDStatelessAppServiceResponse
description: Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4e650b1b114a3cb05b2d9b03b833b9e1cdd6607c
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907237"
---
# <a name="class-mcdstatelessappserviceresponse"></a><span data-ttu-id="e513f-104">Clase `MCDStatelessAppServiceResponse`</span><span class="sxs-lookup"><span data-stu-id="e513f-104">class `MCDStatelessAppServiceResponse`</span></span> 

```
@interface MCDStatelessAppServiceResponse : NSObject
```  

<span data-ttu-id="e513f-105">Representa un mensaje pasado de un servicio de aplicación remota a la aplicación cliente en respuesta a una llamada anterior a MCDAppServiceConnection.sendStatelessMessageAsync.</span><span class="sxs-lookup"><span data-stu-id="e513f-105">Represents a message passed from a remote app service to the client app in response to a previous call to MCDAppServiceConnection.sendStatelessMessageAsync.</span></span>


## <a name="properties"></a><span data-ttu-id="e513f-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="e513f-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="e513f-107">mensaje</span><span class="sxs-lookup"><span data-stu-id="e513f-107">message</span></span>
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="e513f-108">El mensaje enviado por el servicio de aplicación remota, que consta de pares clave/valor.</span><span class="sxs-lookup"><span data-stu-id="e513f-108">The message sent by the remote app service, consisting of key/value pairs.</span></span>

### <a name="status"></a><span data-ttu-id="e513f-109">status</span><span class="sxs-lookup"><span data-stu-id="e513f-109">status</span></span>
`@property(nonatomic, readonly) MCDStatelessAppServiceResponseStatus status;`

<span data-ttu-id="e513f-110">El estado de la respuesta del servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="e513f-110">The status of the response from the remote app service.</span></span>

