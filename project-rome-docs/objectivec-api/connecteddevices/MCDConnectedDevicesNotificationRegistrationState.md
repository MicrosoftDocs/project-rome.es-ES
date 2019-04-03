---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valores que se usa para comunicar el estado de registro en la nube.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909237"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a><span data-ttu-id="043ff-104">Clase `MCDConnectedDevicesNotificationRegistrationState`</span><span class="sxs-lookup"><span data-stu-id="043ff-104">class `MCDConnectedDevicesNotificationRegistrationState`</span></span> 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
<span data-ttu-id="043ff-105">Valores que se usa para comunicar el estado de registro en la nube.</span><span class="sxs-lookup"><span data-stu-id="043ff-105">Values used to communicate the status of cloud registration.</span></span>

## <a name="fields"></a><span data-ttu-id="043ff-106">Campos</span><span class="sxs-lookup"><span data-stu-id="043ff-106">Fields</span></span>

| <span data-ttu-id="043ff-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="043ff-107">Name</span></span>                              |   <span data-ttu-id="043ff-108">Valor</span><span class="sxs-lookup"><span data-stu-id="043ff-108">Value</span></span>     | <span data-ttu-id="043ff-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="043ff-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="043ff-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span><span class="sxs-lookup"><span data-stu-id="043ff-110">MCDConnectedDevicesNotificationRegistrationStateUnregistered</span></span> | <span data-ttu-id="043ff-111">0</span><span class="sxs-lookup"><span data-stu-id="043ff-111">0</span></span> | <span data-ttu-id="043ff-112">Registro nunca se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="043ff-112">Registration has never been started.</span></span>
| <span data-ttu-id="043ff-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span><span class="sxs-lookup"><span data-stu-id="043ff-113">MCDConnectedDevicesNotificationRegistrationStateRegistered</span></span> | <span data-ttu-id="043ff-114">1</span><span class="sxs-lookup"><span data-stu-id="043ff-114">1</span></span> | <span data-ttu-id="043ff-115">Complete el registro.</span><span class="sxs-lookup"><span data-stu-id="043ff-115">Registration has finished.</span></span> |
| <span data-ttu-id="043ff-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span><span class="sxs-lookup"><span data-stu-id="043ff-116">MCDConnectedDevicesNotificationRegistrationStateExpiring</span></span> | <span data-ttu-id="043ff-117">2</span><span class="sxs-lookup"><span data-stu-id="043ff-117">2</span></span> | <span data-ttu-id="043ff-118">El registro está a punto de expirar y por lo que la aplicación debe realizar el registro nuevo.</span><span class="sxs-lookup"><span data-stu-id="043ff-118">Registration is about to expire and so the app should perform registration again.</span></span> |
| <span data-ttu-id="043ff-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span><span class="sxs-lookup"><span data-stu-id="043ff-119">MCDConnectedDevicesNotificationRegistrationStateExpired</span></span> | <span data-ttu-id="043ff-120">3</span><span class="sxs-lookup"><span data-stu-id="043ff-120">3</span></span> | <span data-ttu-id="043ff-121">Registro ha expirado y, por lo que la aplicación debe realizar el registro nuevo.</span><span class="sxs-lookup"><span data-stu-id="043ff-121">Registration has expired and so the app must perform registration again.</span></span> |