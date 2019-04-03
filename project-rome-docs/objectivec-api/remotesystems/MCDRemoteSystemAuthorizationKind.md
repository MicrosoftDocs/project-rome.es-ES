---
title: MCDRemoteSystemAuthorizationKind
description: Contiene valores que describen los posibles tipos de autorización (ámbitos de autorización basada en la cuenta de usuario) para la detección de sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907637"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a><span data-ttu-id="872bd-104">Enum `MCDRemoteSystemAuthorizationKind`</span><span class="sxs-lookup"><span data-stu-id="872bd-104">enum `MCDRemoteSystemAuthorizationKind`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

<span data-ttu-id="872bd-105">Contiene valores que describen los posibles tipos de autorización (ámbitos de autorización basada en la cuenta de usuario) para la detección de sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="872bd-105">Contains values that describe the potential authorization kinds (user-account-based authorization scopes) for remote system discovery.</span></span> 

## <a name="fields"></a><span data-ttu-id="872bd-106">Campos</span><span class="sxs-lookup"><span data-stu-id="872bd-106">Fields</span></span>

| <span data-ttu-id="872bd-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="872bd-107">Name</span></span>                              | <span data-ttu-id="872bd-108">Valor</span><span class="sxs-lookup"><span data-stu-id="872bd-108">Value</span></span> | <span data-ttu-id="872bd-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="872bd-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="872bd-110">MCDRemoteSystemAuthorizationKindSameUser</span><span class="sxs-lookup"><span data-stu-id="872bd-110">MCDRemoteSystemAuthorizationKindSameUser</span></span>   | <span data-ttu-id="872bd-111">0</span><span class="sxs-lookup"><span data-stu-id="872bd-111">0</span></span>     | <span data-ttu-id="872bd-112">El sistema sólo puede detectar y conectarse a dispositivos que inició sesión con la misma cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="872bd-112">The system can only discover and connect with devices signed onto by the same user account.</span></span>   |
| <span data-ttu-id="872bd-113">MCDRemoteSystemAuthorizationKindAnonymous</span><span class="sxs-lookup"><span data-stu-id="872bd-113">MCDRemoteSystemAuthorizationKindAnonymous</span></span> | <span data-ttu-id="872bd-114">1</span><span class="sxs-lookup"><span data-stu-id="872bd-114">1</span></span>     | <span data-ttu-id="872bd-115">El sistema puede descubrir y conectarse a dispositivos de otros usuarios, siempre que se encuentran en la proximidad y permiten la detección anónimo.</span><span class="sxs-lookup"><span data-stu-id="872bd-115">The system can discover and connect with other users' devices, provided they are in proximity and allow anonymous discovery.</span></span>  |

