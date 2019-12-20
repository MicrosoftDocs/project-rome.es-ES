---
title: Uso de API de REST de Actividades del usuario de Microsoft Graph
ms.openlocfilehash: efb5b591ca4c1f3024e1fb19dceee783dc75dc8c
ms.sourcegitcommit: 5670ff536ea9bfcd678cfde54f262a1ec5c8add4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75207904"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="13c29-102">Uso de API de REST de Actividades del usuario de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="13c29-102">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="13c29-103">La característica Actividades del usuario se puede implementar a través de llamadas a API de REST con Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="13c29-103">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="13c29-104">Puedes encontrar más información y documentación de referencia de API en la [sección Project Rome de la documentación de Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span><span class="sxs-lookup"><span data-stu-id="13c29-104">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).</span></span>

<span data-ttu-id="13c29-105">Esta opción te permite crear, publicar, actualizar y leer las actividades del usuario de estilo Windows desde cualquier dispositivo capaz de realizar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="13c29-105">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="13c29-106">Microsoft Graph consigue que la implementación de estos escenarios resulte más sencilla que en los SDK de la plataforma nativa, pero no admite todas las características de Project Rome ni cuenta con un modelo de objetos nativo.</span><span class="sxs-lookup"><span data-stu-id="13c29-106">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>