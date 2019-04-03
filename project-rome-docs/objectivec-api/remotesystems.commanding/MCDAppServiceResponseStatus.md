---
title: MCDAppServiceResponseStatus
description: Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 395c2669af7178ef90ff7fd2dc8bafe9b1044028
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908947"
---
# <a name="enum-mcdappserviceresponsestatus"></a><span data-ttu-id="62290-104">Enum `MCDAppServiceResponseStatus`</span><span class="sxs-lookup"><span data-stu-id="62290-104">enum `MCDAppServiceResponseStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDAppServiceResponseStatus)
```

<span data-ttu-id="62290-105">Contiene valores que describen el estado de un mensaje de respuesta de un servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="62290-105">Contains values that describe the status of a response message from a remote app service.</span></span>

|<span data-ttu-id="62290-106">Nombre</span><span class="sxs-lookup"><span data-stu-id="62290-106">Name</span></span>         | <span data-ttu-id="62290-107">Valor</span><span class="sxs-lookup"><span data-stu-id="62290-107">Value</span></span>  | <span data-ttu-id="62290-108">Descripción</span><span class="sxs-lookup"><span data-stu-id="62290-108">Description</span></span>    |                           
|--------|-------------|-----|
|<span data-ttu-id="62290-109">MCDAppServiceResponseStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="62290-109">MCDAppServiceResponseStatusSuccess</span></span> |<span data-ttu-id="62290-110">0</span><span class="sxs-lookup"><span data-stu-id="62290-110">0</span></span>| <span data-ttu-id="62290-111">El servicio de aplicación correctamente había recibido y procesado el mensaje.</span><span class="sxs-lookup"><span data-stu-id="62290-111">The app service successfully received and processed the message.</span></span>|
|<span data-ttu-id="62290-112">MCDAppServiceResponseStatusFailure</span><span class="sxs-lookup"><span data-stu-id="62290-112">MCDAppServiceResponseStatusFailure</span></span> |<span data-ttu-id="62290-113">1</span><span class="sxs-lookup"><span data-stu-id="62290-113">1</span></span>| <span data-ttu-id="62290-114">El servicio de aplicación no se pudo recibir y procesar el mensaje.</span><span class="sxs-lookup"><span data-stu-id="62290-114">The app service failed to receive and process the message.</span></span>|
|<span data-ttu-id="62290-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span><span class="sxs-lookup"><span data-stu-id="62290-115">MCDAppServiceResponseStatusResourceLimitsExceeded</span></span> |<span data-ttu-id="62290-116">2</span><span class="sxs-lookup"><span data-stu-id="62290-116">2</span></span>| <span data-ttu-id="62290-117">El servicio de aplicación se cerró porque no hay suficientes recursos, no estaban disponibles.</span><span class="sxs-lookup"><span data-stu-id="62290-117">The app service exited because not enough resources were available.</span></span>|
|<span data-ttu-id="62290-118">MCDAppServiceResponseStatusUnknown</span><span class="sxs-lookup"><span data-stu-id="62290-118">MCDAppServiceResponseStatusUnknown</span></span> |<span data-ttu-id="62290-119">3</span><span class="sxs-lookup"><span data-stu-id="62290-119">3</span></span>| <span data-ttu-id="62290-120">Se produjo un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="62290-120">An unknown error occurred.</span></span>|
|<span data-ttu-id="62290-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span><span class="sxs-lookup"><span data-stu-id="62290-121">MCDAppServiceResponseStatusRemoteSystemUnavailable</span></span> |<span data-ttu-id="62290-122">4</span><span class="sxs-lookup"><span data-stu-id="62290-122">4</span></span>| <span data-ttu-id="62290-123">El dispositivo al que se envió el mensaje no está disponible.</span><span class="sxs-lookup"><span data-stu-id="62290-123">The device to which the message was sent is not available.</span></span>|
|<span data-ttu-id="62290-124">MCDAppServiceResponseStatusMessageTooLarge</span><span class="sxs-lookup"><span data-stu-id="62290-124">MCDAppServiceResponseStatusMessageTooLarge</span></span> |<span data-ttu-id="62290-125">5</span><span class="sxs-lookup"><span data-stu-id="62290-125">5</span></span>| <span data-ttu-id="62290-126">El servicio de aplicación no se pudo procesar el mensaje porque es demasiado grande.</span><span class="sxs-lookup"><span data-stu-id="62290-126">The app service failed to process the message because it is too large.</span></span>|
|<span data-ttu-id="62290-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span><span class="sxs-lookup"><span data-stu-id="62290-127">MCDAppServiceResponseStatusAppServiceConnectionClosed</span></span>|<span data-ttu-id="62290-128">6</span><span class="sxs-lookup"><span data-stu-id="62290-128">6</span></span>| <span data-ttu-id="62290-129">Se cerró la conexión de servicio de aplicación antes de que se envió una respuesta.</span><span class="sxs-lookup"><span data-stu-id="62290-129">The app service connection was closed before a response was sent.</span></span>|