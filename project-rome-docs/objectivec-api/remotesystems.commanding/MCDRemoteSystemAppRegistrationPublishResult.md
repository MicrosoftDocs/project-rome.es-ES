---
title: MCDRemoteSystemAppRegistrationPublishResult
description: Una clase comunica el resultado asincrónico de publicar información de la aplicación de sistema remoto para una cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909927"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a><span data-ttu-id="cc6cb-104">Clase `MCDRemoteSystemAppRegistrationPublishResult`</span><span class="sxs-lookup"><span data-stu-id="cc6cb-104">class `MCDRemoteSystemAppRegistrationPublishResult`</span></span> 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

<span data-ttu-id="cc6cb-105">Esta clase comunica el resultado asincrónico de publicar información de la aplicación de sistema remoto para una cuenta.</span><span class="sxs-lookup"><span data-stu-id="cc6cb-105">This class communicates the async result of publishing remote system app information for an account.</span></span> <span data-ttu-id="cc6cb-106">Los Estados de error que se comunica a través de este resultado se deben usar la aplicación para volver a intentar la publicación en el caso de ciertas condiciones transitorias como la red que no está disponible.</span><span class="sxs-lookup"><span data-stu-id="cc6cb-106">The error statuses communicated through this result should be used by the app to retry publishing in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="cc6cb-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="cc6cb-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="cc6cb-108">status</span><span class="sxs-lookup"><span data-stu-id="cc6cb-108">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

<span data-ttu-id="cc6cb-109">Enumeración de estado de la operación de publicación.</span><span class="sxs-lookup"><span data-stu-id="cc6cb-109">Status enum of the publish operation.</span></span>