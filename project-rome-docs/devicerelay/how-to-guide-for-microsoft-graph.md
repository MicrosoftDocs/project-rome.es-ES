---
title: Uso de las API de REST de Retransmisión de dispositivo de Microsoft Graph
ms.openlocfilehash: 887ebff8788ac4300036512761df80c6b8e5e97f
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "75207824"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="0fe17-102">Uso de las API de REST de Retransmisión de dispositivo de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="0fe17-102">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="0fe17-103">Las características de retransmisión de dispositivo se pueden implementar a través de llamadas de API de REST con Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="0fe17-103">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="0fe17-104">Puedes encontrar más información y documentación de referencia de API en la [sección Project Rome de la documentación de Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span><span class="sxs-lookup"><span data-stu-id="0fe17-104">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="0fe17-105">La implementación con Microsoft Graph permite detectar los dispositivos, iniciar aplicaciones e interactuar con servicios de aplicaciones desde cualquier dispositivo capaz de realizar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="0fe17-105">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="0fe17-106">Microsoft Graph consigue que la implementación de estos escenarios resulte más sencilla que en los SDK de la plataforma nativa, pero no admite todas las características que ofrece Project Rome ni cuenta con un modelo de objetos nativo.</span><span class="sxs-lookup"><span data-stu-id="0fe17-106">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>