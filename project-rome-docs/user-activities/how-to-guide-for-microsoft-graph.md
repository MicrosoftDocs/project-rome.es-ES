---
title: Uso de API de REST de Actividades del usuario de Microsoft Graph
description: Use API REST de actividades de usuario de Microsoft Graph para crear, publicar, actualizar y leer las actividades de usuario con el estilo de Windows.
ms.openlocfilehash: 3bd2a5258c11936ceb3adbcbd102e7f546cac1ab
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901663"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a><span data-ttu-id="f2dd2-103">Uso de API de REST de Actividades del usuario de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="f2dd2-103">Using Microsoft Graph's User Activities REST APIs</span></span>

<span data-ttu-id="f2dd2-104">La característica Actividades del usuario se puede implementar a través de llamadas a API de REST con Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="f2dd2-104">The User Activities feature can be implemented through REST API calls with Microsoft Graph.</span></span> <span data-ttu-id="f2dd2-105">Puedes encontrar más información y documentación de referencia de API en la [sección Project Rome de la documentación de Microsoft Graph](/graph/api/resources/project-rome-overview#activities).</span><span class="sxs-lookup"><span data-stu-id="f2dd2-105">You can find more information and API reference documentation in the [Project Rome section of the Microsoft Graph docs](/graph/api/resources/project-rome-overview#activities).</span></span>

<span data-ttu-id="f2dd2-106">Esta opción te permite crear, publicar, actualizar y leer las actividades del usuario de estilo Windows desde cualquier dispositivo capaz de realizar solicitudes HTTP.</span><span class="sxs-lookup"><span data-stu-id="f2dd2-106">This allows you to create, publish, update, and read Windows-style User Activities from any device capable of making HTTP requests.</span></span> <span data-ttu-id="f2dd2-107">Microsoft Graph consigue que la implementación de estos escenarios resulte más sencilla que en los SDK de la plataforma nativa, pero no admite todas las características de Project Rome ni cuenta con un modelo de objetos nativo.</span><span class="sxs-lookup"><span data-stu-id="f2dd2-107">Microsoft Graph makes these scenarios simpler to implement than on the native platform SDKs, but it does not support all of the Project Rome features or provide a native object model.</span></span>