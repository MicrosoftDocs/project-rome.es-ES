---
title: MCDConnectedDevicesNotificationRegistrationState
description: Obtenga información sobre la clase MCDConnectedDevicesNotificationRegistrationState. Estos valores se usan para comunicar el estado del registro en la nube.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761119"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="20abc-105">las `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="20abc-105">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="20abc-106">Valores usados para comunicar el estado del registro en la nube.</span><span class="sxs-lookup"><span data-stu-id="20abc-106">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="20abc-107">Campos</span><span class="sxs-lookup"><span data-stu-id="20abc-107">Fields</span></span>

| <span data-ttu-id="20abc-108">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="20abc-108">Name</span></span>                              |   <span data-ttu-id="20abc-109">Valor</span><span class="sxs-lookup"><span data-stu-id="20abc-109">Value</span></span>     | <span data-ttu-id="20abc-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="20abc-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="20abc-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="20abc-111">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="20abc-112">0</span><span class="sxs-lookup"><span data-stu-id="20abc-112">0</span></span> | <span data-ttu-id="20abc-113">No se ha iniciado nunca el registro.</span><span class="sxs-lookup"><span data-stu-id="20abc-113">Registration has never been started.</span></span>
| <span data-ttu-id="20abc-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="20abc-114">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="20abc-115">1</span><span class="sxs-lookup"><span data-stu-id="20abc-115">1</span></span> | <span data-ttu-id="20abc-116">El registro ha finalizado.</span><span class="sxs-lookup"><span data-stu-id="20abc-116">Registration has finished.</span></span> |
| <span data-ttu-id="20abc-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="20abc-117">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="20abc-118">2</span><span class="sxs-lookup"><span data-stu-id="20abc-118">2</span></span> | <span data-ttu-id="20abc-119">El registro está a punto de expirar y, por tanto, la aplicación debe realizar el registro de nuevo.</span><span class="sxs-lookup"><span data-stu-id="20abc-119">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="20abc-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="20abc-120">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="20abc-121">3</span><span class="sxs-lookup"><span data-stu-id="20abc-121">3</span></span> | <span data-ttu-id="20abc-122">El registro ha expirado y, por lo tanto, la aplicación debe volver a realizar el registro.</span><span class="sxs-lookup"><span data-stu-id="20abc-122">Registration has expired and so the app must perform registration again.</span></span> |