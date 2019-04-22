---
title: MCDAppServiceRequest
description: Representa un mensaje entrante de un aplicación o dispositivo remoto para esta conexión de servicio de aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 553403ab57b594294072dc082f5646eb1646e55b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800537"
---
# <a name="class-mcdappservicerequest"></a><span data-ttu-id="866a0-104">Clase `MCDAppServiceRequest`</span><span class="sxs-lookup"><span data-stu-id="866a0-104">class `MCDAppServiceRequest`</span></span>

```
@interface MCDAppServiceRequest : NSObject
```
<span data-ttu-id="866a0-105">Representa un mensaje entrante de un aplicación o dispositivo remoto para esta conexión de servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="866a0-105">Represents an incoming message from a remote app/device to this app service connection.</span></span>

## <a name="properties"></a><span data-ttu-id="866a0-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="866a0-106">Properties</span></span>

### <a name="message"></a><span data-ttu-id="866a0-107">mensaje</span><span class="sxs-lookup"><span data-stu-id="866a0-107">message</span></span> 
`@property(nonatomic, readonly, nonnull) NSDictionary* message;`

<span data-ttu-id="866a0-108">El mensaje para el servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="866a0-108">The message for the remote app service.</span></span>

## <a name="methods"></a><span data-ttu-id="866a0-109">Métodos</span><span class="sxs-lookup"><span data-stu-id="866a0-109">Methods</span></span>

### <a name="sendresponseasync"></a><span data-ttu-id="866a0-110">sendResponseAsync</span><span class="sxs-lookup"><span data-stu-id="866a0-110">sendResponseAsync</span></span> 
```
- (void)sendResponseAsync:(nonnull NSDictionary*)message
               completion:(nonnull void (^)(MCDAppServiceResponseStatus, NSError* _Nullable))completion;
```

<span data-ttu-id="866a0-111">Envía un mensaje de respuesta para el servicio de aplicación remota que envió la solicitud.</span><span class="sxs-lookup"><span data-stu-id="866a0-111">Sends a response message to the remote app service that sent the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="866a0-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="866a0-112">Parameters</span></span>
* `message` 

<span data-ttu-id="866a0-113">El mensaje para el servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="866a0-113">The message for the remote app service.</span></span>

* `completion`     

<span data-ttu-id="866a0-114">La finalización de la operación asincrónica con un valor MCDAppServiceResponseStatus que indica el estado de la operación de envío.</span><span class="sxs-lookup"><span data-stu-id="866a0-114">The completion of the asynchronous operation with an MCDAppServiceResponseStatus value indicating the status of the send operation.</span></span>