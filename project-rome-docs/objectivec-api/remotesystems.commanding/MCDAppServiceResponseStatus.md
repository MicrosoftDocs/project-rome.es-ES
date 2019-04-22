---
title: MCDAppServiceResponseStatus
description: Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800337"
---
# <a name="enum-mcdappserviceresponsestatus"></a><span data-ttu-id="f174f-104">Enum `MCDAppServiceResponseStatus`</span><span class="sxs-lookup"><span data-stu-id="f174f-104">enum `MCDAppServiceResponseStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

<span data-ttu-id="f174f-105">Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="f174f-105">Contains values that describe the status of a response message from a remote app service.</span></span>

|<span data-ttu-id="f174f-106">Name</span><span class="sxs-lookup"><span data-stu-id="f174f-106">Name</span></span>         | <span data-ttu-id="f174f-107">Valor</span><span class="sxs-lookup"><span data-stu-id="f174f-107">Value</span></span>  | <span data-ttu-id="f174f-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="f174f-108">Description</span></span>    |                           
|--------|-------------|-----|
|<span data-ttu-id="f174f-109">MCDAppServiceResponseStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="f174f-109">MCDAppServiceResponseStatusSuccess</span></span> |<span data-ttu-id="f174f-110">0</span><span class="sxs-lookup"><span data-stu-id="f174f-110">0</span></span>| <span data-ttu-id="f174f-111">El servicio de aplicación correctamente había recibido y procesado el mensaje.</span><span class="sxs-lookup"><span data-stu-id="f174f-111">The app service successfully received and processed the message.</span></span>|
|<span data-ttu-id="f174f-112">MCDAppServiceResponseStatusFailure</span><span class="sxs-lookup"><span data-stu-id="f174f-112">MCDAppServiceResponseStatusFailure</span></span> |<span data-ttu-id="f174f-113">1</span><span class="sxs-lookup"><span data-stu-id="f174f-113">1</span></span>| <span data-ttu-id="f174f-114">El servicio de aplicación no se pudo recibir y procesar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="f174f-114">The app service failed to receive and process the message.</span></span>|
|<span data-ttu-id="f174f-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="f174f-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="f174f-116">2</span><span class="sxs-lookup"><span data-stu-id="f174f-116">2</span></span>| <span data-ttu-id="f174f-117">El servicio de aplicación se cerró porque no hay suficientes recursos, no estaban disponibles.</span><span class="sxs-lookup"><span data-stu-id="f174f-117">The app service exited because not enough resources were available.</span></span>|
|<span data-ttu-id="f174f-118">MCDAppServiceResponseStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="f174f-118">MCDAppServiceResponseStatusUnknown</span></span> |<span data-ttu-id="f174f-119">3</span><span class="sxs-lookup"><span data-stu-id="f174f-119">3</span></span>| <span data-ttu-id="f174f-120">Se produjo un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="f174f-120">An unknown error occurred.</span></span>|
|<span data-ttu-id="f174f-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="f174f-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span></span> |<span data-ttu-id="f174f-122">4</span><span class="sxs-lookup"><span data-stu-id="f174f-122">4</span></span>| <span data-ttu-id="f174f-123">El dispositivo al que se envió el mensaje no está disponible.</span><span class="sxs-lookup"><span data-stu-id="f174f-123">The device to which the message was sent is not available.</span></span>|
|<span data-ttu-id="f174f-124">MCDAppServiceResponseStatusMessageTooLarge</span><span class="sxs-lookup"><span data-stu-id="f174f-124">MCDAppServiceResponseStatusMessageTooLarge</span></span> |<span data-ttu-id="f174f-125">5</span><span class="sxs-lookup"><span data-stu-id="f174f-125">5</span></span>| <span data-ttu-id="f174f-126">El servicio de aplicación no se pudo procesar el mensaje porque es demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="f174f-126">The app service failed to process the message because it is too large.</span></span>|
|<span data-ttu-id="f174f-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="f174f-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span></span>|<span data-ttu-id="f174f-128">6</span><span class="sxs-lookup"><span data-stu-id="f174f-128">6</span></span>| <span data-ttu-id="f174f-129">Se cerró la conexión de servicio de aplicación antes de que se envió una respuesta.</span><span class="sxs-lookup"><span data-stu-id="f174f-129">The app service connection was closed before a response was sent.</span></span>|