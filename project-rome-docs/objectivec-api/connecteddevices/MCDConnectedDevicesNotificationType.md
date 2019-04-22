---
title: MCDConnectedDevicesNotificationType
description: Contiene valores que describen el tipo (servicio) de una notificación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: eb537450a9e8a970bd07652fe201e94071211d92
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801697"
---
# <a name="enum-mcdconnecteddevicesnotificationtype"></a><span data-ttu-id="0a6bb-104">Enum `MCDConnectedDevicesNotificationType`</span><span class="sxs-lookup"><span data-stu-id="0a6bb-104">enum `MCDConnectedDevicesNotificationType`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationType)
```  
<span data-ttu-id="0a6bb-105">Contiene valores que describen el tipo (servicio) de una notificación.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-105">Contains values that describe the type (service) of a notification.</span></span>

## <a name="fields"></a><span data-ttu-id="0a6bb-106">Campos</span><span class="sxs-lookup"><span data-stu-id="0a6bb-106">Fields</span></span>

| <span data-ttu-id="0a6bb-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="0a6bb-107">Name</span></span>                              |   <span data-ttu-id="0a6bb-108">Valor</span><span class="sxs-lookup"><span data-stu-id="0a6bb-108">Value</span></span>     | <span data-ttu-id="0a6bb-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="0a6bb-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="0a6bb-110">MCDNotificationTypeUnknown</span><span class="sxs-lookup"><span data-stu-id="0a6bb-110">MCDNotificationTypeUnknown</span></span> | <span data-ttu-id="0a6bb-111">0</span><span class="sxs-lookup"><span data-stu-id="0a6bb-111">0</span></span> | <span data-ttu-id="0a6bb-112">ConnectedDevicesNotificationType es desconocido.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-112">ConnectedDevicesNotificationType is unknown.</span></span> |
| <span data-ttu-id="0a6bb-113">MCDNotificationTypeWNS</span><span class="sxs-lookup"><span data-stu-id="0a6bb-113">MCDNotificationTypeWNS</span></span> | <span data-ttu-id="0a6bb-114">1</span><span class="sxs-lookup"><span data-stu-id="0a6bb-114">1</span></span> | <span data-ttu-id="0a6bb-115">Servicios de notificación de inserción de Windows.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-115">Windows Push Notification Services.</span></span> |
| <span data-ttu-id="0a6bb-116">MCDNotificationTypeGCM</span><span class="sxs-lookup"><span data-stu-id="0a6bb-116">MCDNotificationTypeGCM</span></span> | <span data-ttu-id="0a6bb-117">2</span><span class="sxs-lookup"><span data-stu-id="0a6bb-117">2</span></span> | <span data-ttu-id="0a6bb-118">Google Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-118">Google Cloud Messaging.</span></span> |
| <span data-ttu-id="0a6bb-119">MCDNotificationTypeFCM</span><span class="sxs-lookup"><span data-stu-id="0a6bb-119">MCDNotificationTypeFCM</span></span> | <span data-ttu-id="0a6bb-120">3</span><span class="sxs-lookup"><span data-stu-id="0a6bb-120">3</span></span> | <span data-ttu-id="0a6bb-121">Firebase Cloud Messaging.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-121">Firebase Cloud Messaging.</span></span>|
| <span data-ttu-id="0a6bb-122">MCDNotificationTypeAPN</span><span class="sxs-lookup"><span data-stu-id="0a6bb-122">MCDNotificationTypeAPN</span></span> | <span data-ttu-id="0a6bb-123">4</span><span class="sxs-lookup"><span data-stu-id="0a6bb-123">4</span></span> | <span data-ttu-id="0a6bb-124">Servicio de notificaciones Push de Apple.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-124">Apple Push Notification Service.</span></span> |
| <span data-ttu-id="0a6bb-125">MCDNotificationTypePolling</span><span class="sxs-lookup"><span data-stu-id="0a6bb-125">MCDNotificationTypePolling</span></span> | <span data-ttu-id="0a6bb-126">5</span><span class="sxs-lookup"><span data-stu-id="0a6bb-126">5</span></span> | <span data-ttu-id="0a6bb-127">Ningún servicio de notificación en la nube; en su lugar un sondeo para las respuestas entrantes.</span><span class="sxs-lookup"><span data-stu-id="0a6bb-127">No cloud notification service; instead poll for incoming responses.</span></span> |
