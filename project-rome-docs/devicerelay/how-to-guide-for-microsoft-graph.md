---
title: Uso de las API de REST de Retransmisión de dispositivo de Microsoft Graph
description: Aprenda a usar las API REST de retransmisión de dispositivos de Microsoft Graph para detectar sus dispositivos, iniciar aplicaciones e interactuar con App Services.
ms.openlocfilehash: a2433e5a16f36edb9e8283d885f9ebf3d05b64d1
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760809"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="5f3e8-103">Uso de las API de REST de Retransmisión de dispositivo de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="5f3e8-103">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="5f3e8-104">Las características de retransmisión de dispositivo se pueden implementar a través de llamadas de API de REST con Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="5f3e8-104">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="5f3e8-105">Puedes encontrar más información y documentación de referencia de API en la [sección Project Rome de la documentación de Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span><span class="sxs-lookup"><span data-stu-id="5f3e8-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="5f3e8-106">La implementación con Microsoft Graph permite detectar los dispositivos, iniciar aplicaciones e interactuar con servicios de aplicaciones desde cualquier dispositivo capaz de realizar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="5f3e8-106">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="5f3e8-107">Microsoft Graph consigue que la implementación de estos escenarios resulte más sencilla que en los SDK de la plataforma nativa, pero no admite todas las características que ofrece Project Rome ni cuenta con un modelo de objetos nativo.</span><span class="sxs-lookup"><span data-stu-id="5f3e8-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>