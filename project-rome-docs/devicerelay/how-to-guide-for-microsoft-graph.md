---
ms.openlocfilehash: 1d32d509e7c76507626cf0271a28f876f4749ab1
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800287"
---
# <a name="using-microsoft-graphs-device-relay-rest-apis"></a><span data-ttu-id="eb5a4-101">Con la retransmisión de dispositivo de Microsoft Graph API de REST</span><span class="sxs-lookup"><span data-stu-id="eb5a4-101">Using Microsoft Graph's Device Relay REST APIs</span></span>

<span data-ttu-id="eb5a4-102">Características de retransmisión de dispositivo pueden implementarse a través de llamadas de API de REST con Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="eb5a4-102">Device Relay features can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="eb5a4-103">Puede encontrar más información y documentación de referencia de API en el [sección Roma de proyecto de los documentos de Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span><span class="sxs-lookup"><span data-stu-id="eb5a4-103">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#devices).</span></span>

<span data-ttu-id="eb5a4-104">Implementación con Microsoft Graph permite detectar los dispositivos, iniciar aplicaciones e interactuar con servicios de aplicaciones desde cualquier dispositivo capaz de realizar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb5a4-104">Implementing with Microsoft Graph allows you to discover your devices, launch apps, and interact with app services from any device capable of making HTTP requests.</span></span> <span data-ttu-id="eb5a4-105">Microsoft Graph hace más fácil de implementar que en el SDK de plataforma nativo estos escenarios, pero no admite todas las características de las características de proyecto Roma ni ofrece un modelo de objeto nativo.</span><span class="sxs-lookup"><span data-stu-id="eb5a4-105">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the features Project Rome features or offer a native object model.</span></span>