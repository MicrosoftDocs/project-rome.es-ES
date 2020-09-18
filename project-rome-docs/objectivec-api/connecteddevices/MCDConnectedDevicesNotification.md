---
title: MCDConnectedDevicesNotification
description: Obtenga información sobre la clase MCDConnectedDevicesNotification. Esta clase es el resultado del procesamiento de una notificación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: c05ac896113b8196d1dd3854a14ef5730552435f
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761019"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="f4aee-105">las `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="f4aee-105">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="f4aee-106">Resultado del procesamiento de una notificación.</span><span class="sxs-lookup"><span data-stu-id="f4aee-106">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="f4aee-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="f4aee-107">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="f4aee-108">tryParse</span><span class="sxs-lookup"><span data-stu-id="f4aee-108">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="f4aee-109">Intenta analizar un MCDConnectedDevicesNotification a partir de un mapa con formato de APNS.</span><span class="sxs-lookup"><span data-stu-id="f4aee-109">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f4aee-110">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f4aee-110">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="f4aee-111">Asignación recibida de la notificación de APNS a la plataforma de dispositivos conectados para su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="f4aee-111">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
