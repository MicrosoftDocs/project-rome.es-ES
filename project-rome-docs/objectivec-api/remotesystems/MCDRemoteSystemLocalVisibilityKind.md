---
title: MCDRemoteSystemLocalVisibilityKind
description: Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908867"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a><span data-ttu-id="33931-104">Enum `MCDRemoteSystemLocalVisibilityKind`</span><span class="sxs-lookup"><span data-stu-id="33931-104">enum `MCDRemoteSystemLocalVisibilityKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
<span data-ttu-id="33931-105">Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.</span><span class="sxs-lookup"><span data-stu-id="33931-105">Contains values that describe the local application visibility preference when discovering remote systems.</span></span>

## <a name="fields"></a><span data-ttu-id="33931-106">Campos</span><span class="sxs-lookup"><span data-stu-id="33931-106">Fields</span></span>

| <span data-ttu-id="33931-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="33931-107">Name</span></span>                              | <span data-ttu-id="33931-108">Valor</span><span class="sxs-lookup"><span data-stu-id="33931-108">Value</span></span> | <span data-ttu-id="33931-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="33931-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="33931-110">MCDRemoteSystemLocalVisibilityKindShowAll</span><span class="sxs-lookup"><span data-stu-id="33931-110">MCDRemoteSystemLocalVisibilityKindShowAll</span></span> | <span data-ttu-id="33931-111">0</span><span class="sxs-lookup"><span data-stu-id="33931-111">0</span></span> | <span data-ttu-id="33931-112">Mostrar todas las aplicaciones reconocibles, incluida la aplicación que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="33931-112">Show all discoverable applications, including the calling app.</span></span>
| <span data-ttu-id="33931-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span><span class="sxs-lookup"><span data-stu-id="33931-113">MCDRemoteSystemLocalVisibilityKindHideLocalApp</span></span> | <span data-ttu-id="33931-114">1</span><span class="sxs-lookup"><span data-stu-id="33931-114">1</span></span> | <span data-ttu-id="33931-115">Ocultar la aplicación que realiza la llamada.</span><span class="sxs-lookup"><span data-stu-id="33931-115">Hide the calling application.</span></span>