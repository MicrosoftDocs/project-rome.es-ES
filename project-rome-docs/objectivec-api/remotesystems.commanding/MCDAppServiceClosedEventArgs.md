---
title: MCDAppServiceClosedEventArgs
description: Devuelve MCDAppServiceConnection.serviceClosed para informar a la que se ha cerrado el MCDAppServiceConnection y proporcionar un motivo del evento de cierre.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801297"
---
# <a name="class-mcdappserviceclosedeventargs"></a><span data-ttu-id="8e3ff-104">Clase `MCDAppServiceClosedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="8e3ff-104">class `MCDAppServiceClosedEventArgs`</span></span> 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

<span data-ttu-id="8e3ff-105">Devuelve MCDAppServiceConnection.serviceClosed para informar a la que se ha cerrado el MCDAppServiceConnection y proporcionar un motivo del evento de cierre.</span><span class="sxs-lookup"><span data-stu-id="8e3ff-105">Returned by MCDAppServiceConnection.serviceClosed to inform that the MCDAppServiceConnection has been closed and provide a reason behind the close event.</span></span>

## <a name="properties"></a><span data-ttu-id="8e3ff-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="8e3ff-106">Properties</span></span>

### <a name="status"></a><span data-ttu-id="8e3ff-107">status</span><span class="sxs-lookup"><span data-stu-id="8e3ff-107">status</span></span>
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

<span data-ttu-id="8e3ff-108">El estado de cómo se cerró el servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="8e3ff-108">The status of how the app service closed.</span></span>