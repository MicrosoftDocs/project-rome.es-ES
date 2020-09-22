---
title: Uso de API de REST de Actividades del usuario de Microsoft Graph
description: Use API REST de actividades de usuario de Microsoft Graph para crear, publicar, actualizar y leer las actividades de usuario con el estilo de Windows.
ms.openlocfilehash: 7ec7a2f285ed0b1875bf8d945534b8b89de566f3
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760079"
---
# <a name="using-microsoft-graphs-user-activities-rest-apis"></a>Uso de API de REST de Actividades del usuario de Microsoft Graph

La característica Actividades del usuario se puede implementar a través de llamadas a API de REST con Microsoft Graph. Puedes encontrar más información y documentación de referencia de API en la [sección Project Rome de la documentación de Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview#activities).

Esta opción te permite crear, publicar, actualizar y leer las actividades del usuario de estilo Windows desde cualquier dispositivo capaz de realizar solicitudes HTTP. Microsoft Graph consigue que la implementación de estos escenarios resulte más sencilla que en los SDK de la plataforma nativa, pero no admite todas las características de Project Rome ni cuenta con un modelo de objetos nativo.