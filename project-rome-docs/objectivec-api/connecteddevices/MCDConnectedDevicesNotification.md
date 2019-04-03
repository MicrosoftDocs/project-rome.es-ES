---
title: MCDConnectedDevicesNotification
description: Resultado de procesar una notificación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 2a60e2cab26c3d2df39314aa5b61a65de1529356
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908717"
---
# <a name="class-mcdconnecteddevicesnotification"></a><span data-ttu-id="b7204-104">Clase `MCDConnectedDevicesNotification`</span><span class="sxs-lookup"><span data-stu-id="b7204-104">class `MCDConnectedDevicesNotification`</span></span> 

```
@interface MCDConnectedDevicesNotification : NSObject
```  
<span data-ttu-id="b7204-105">Resultado de procesar una notificación.</span><span class="sxs-lookup"><span data-stu-id="b7204-105">Result of processing a notification.</span></span>

## <a name="methods"></a><span data-ttu-id="b7204-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="b7204-106">Methods</span></span>

### <a name="tryparse"></a><span data-ttu-id="b7204-107">tryParse</span><span class="sxs-lookup"><span data-stu-id="b7204-107">tryParse</span></span>

`+ (nullable instancetype)tryParse:(NSDictionary* _Nonnull)dictionary;`

<span data-ttu-id="b7204-108">Intenta analizar un MCDConnectedDevicesNotification desde un APN tiene un formato de mapa.</span><span class="sxs-lookup"><span data-stu-id="b7204-108">Attempts to parse a MCDConnectedDevicesNotification from an APNS formatted map.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b7204-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b7204-109">Parameters</span></span> 
* `dictionary` 

<span data-ttu-id="b7204-110">El mapa recibido de la notificación de APNS para la plataforma de dispositivos conectados para su procesamiento.</span><span class="sxs-lookup"><span data-stu-id="b7204-110">The map received from the APNS notification to the Connected Devices platform for processing.</span></span>
