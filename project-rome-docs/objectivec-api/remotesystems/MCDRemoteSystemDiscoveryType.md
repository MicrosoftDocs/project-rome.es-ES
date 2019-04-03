---
title: MCDRemoteSystemDiscoveryType
description: Contiene valores que describen los sistemas remotos cómo pueden detectarse.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907037"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a><span data-ttu-id="5a057-104">Enum `MCDRemoteSystemDiscoveryType`</span><span class="sxs-lookup"><span data-stu-id="5a057-104">enum `MCDRemoteSystemDiscoveryType`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

<span data-ttu-id="5a057-105">Contiene valores que describen los sistemas remotos cómo pueden detectarse.</span><span class="sxs-lookup"><span data-stu-id="5a057-105">Contains values that describe how remote systems are able to be discovered.</span></span> 

## <a name="fields"></a><span data-ttu-id="5a057-106">Campos</span><span class="sxs-lookup"><span data-stu-id="5a057-106">Fields</span></span>

| <span data-ttu-id="5a057-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="5a057-107">Name</span></span>                              | <span data-ttu-id="5a057-108">Valor</span><span class="sxs-lookup"><span data-stu-id="5a057-108">Value</span></span> | <span data-ttu-id="5a057-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="5a057-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="5a057-110">MCDRemoteSystemDiscoveryTypeAny</span><span class="sxs-lookup"><span data-stu-id="5a057-110">MCDRemoteSystemDiscoveryTypeAny</span></span>   | <span data-ttu-id="5a057-111">0</span><span class="sxs-lookup"><span data-stu-id="5a057-111">0</span></span>     | <span data-ttu-id="5a057-112">Los sistemas remotos son reconocibles a través de cualquier conexión.</span><span class="sxs-lookup"><span data-stu-id="5a057-112">Remote systems are discoverable through any connection.</span></span>  |
| <span data-ttu-id="5a057-113">MCDRemoteSystemDiscoveryTypeProximal</span><span class="sxs-lookup"><span data-stu-id="5a057-113">MCDRemoteSystemDiscoveryTypeProximal</span></span> | <span data-ttu-id="5a057-114">1</span><span class="sxs-lookup"><span data-stu-id="5a057-114">1</span></span>     | <span data-ttu-id="5a057-115">Los sistemas remotos solo son reconocibles a través de una conexión articulaciones próximas, como una variable local</span><span class="sxs-lookup"><span data-stu-id="5a057-115">Remote systems are only discoverable through a proximal connection, such as a local</span></span>
<span data-ttu-id="5a057-116">red o la conexión Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="5a057-116">network or Bluetooth connection.</span></span> |
| <span data-ttu-id="5a057-117">MCDRemoteSystemDiscoveryTypeCloud</span><span class="sxs-lookup"><span data-stu-id="5a057-117">MCDRemoteSystemDiscoveryTypeCloud</span></span> | <span data-ttu-id="5a057-118">2</span><span class="sxs-lookup"><span data-stu-id="5a057-118">2</span></span>     | <span data-ttu-id="5a057-119">Los sistemas remotos solo son reconocibles a través de la conexión en la nube.</span><span class="sxs-lookup"><span data-stu-id="5a057-119">Remote systems are only discoverable through cloud connection.</span></span> |
| <span data-ttu-id="5a057-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span><span class="sxs-lookup"><span data-stu-id="5a057-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span></span> | <span data-ttu-id="5a057-121">3</span><span class="sxs-lookup"><span data-stu-id="5a057-121">3</span></span>     | <span data-ttu-id="5a057-122">Los sistemas remotos son reconocibles a través de una conexión articulaciones próximas y se esperan que sean</span><span class="sxs-lookup"><span data-stu-id="5a057-122">Remote systems are discoverable through a proximal connection and are expected to be</span></span>
<span data-ttu-id="5a057-123">espacialmente cerca del dispositivo de cliente (en el intervalo de Bluetooth, por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="5a057-123">spatially near to the client device (in Bluetooth range, for example).</span></span>  |

