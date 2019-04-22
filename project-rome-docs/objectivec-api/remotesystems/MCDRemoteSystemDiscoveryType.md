---
title: MCDRemoteSystemDiscoveryType
description: Contiene valores que describen los sistemas remotos cómo pueden detectarse.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: dc94b92311cb666fd2ffd3949b3d4d66a49e6e5b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800507"
---
# <a name="enum-mcdremotesystemdiscoverytype"></a><span data-ttu-id="09960-104">Enum `MCDRemoteSystemDiscoveryType`</span><span class="sxs-lookup"><span data-stu-id="09960-104">enum `MCDRemoteSystemDiscoveryType`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemDiscoveryType)
```  

<span data-ttu-id="09960-105">Contiene valores que describen los sistemas remotos cómo pueden detectarse.</span><span class="sxs-lookup"><span data-stu-id="09960-105">Contains values that describe how remote systems are able to be discovered.</span></span> 

## <a name="fields"></a><span data-ttu-id="09960-106">Campos</span><span class="sxs-lookup"><span data-stu-id="09960-106">Fields</span></span>

| <span data-ttu-id="09960-107">Name</span><span class="sxs-lookup"><span data-stu-id="09960-107">Name</span></span>                              | <span data-ttu-id="09960-108">Valor</span><span class="sxs-lookup"><span data-stu-id="09960-108">Value</span></span> | <span data-ttu-id="09960-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="09960-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="09960-110">MCDRemoteSystemDiscoveryTypeAny</span><span class="sxs-lookup"><span data-stu-id="09960-110">MCDRemoteSystemDiscoveryTypeAny</span></span>   | <span data-ttu-id="09960-111">0</span><span class="sxs-lookup"><span data-stu-id="09960-111">0</span></span>     | <span data-ttu-id="09960-112">Los sistemas remotos son reconocibles a través de cualquier conexión.</span><span class="sxs-lookup"><span data-stu-id="09960-112">Remote systems are discoverable through any connection.</span></span>  |
| <span data-ttu-id="09960-113">MCDRemoteSystemDiscoveryTypeProximal</span><span class="sxs-lookup"><span data-stu-id="09960-113">MCDRemoteSystemDiscoveryTypeProximal</span></span> | <span data-ttu-id="09960-114">1</span><span class="sxs-lookup"><span data-stu-id="09960-114">1</span></span>     | <span data-ttu-id="09960-115">Los sistemas remotos solo son reconocibles a través de una conexión articulaciones próximas, como una variable local</span><span class="sxs-lookup"><span data-stu-id="09960-115">Remote systems are only discoverable through a proximal connection, such as a local</span></span>
<span data-ttu-id="09960-116">red o la conexión Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="09960-116">network or Bluetooth connection.</span></span> |
| <span data-ttu-id="09960-117">MCDRemoteSystemDiscoveryTypeCloud</span><span class="sxs-lookup"><span data-stu-id="09960-117">MCDRemoteSystemDiscoveryTypeCloud</span></span> | <span data-ttu-id="09960-118">2</span><span class="sxs-lookup"><span data-stu-id="09960-118">2</span></span>     | <span data-ttu-id="09960-119">Los sistemas remotos solo son reconocibles a través de la conexión en la nube.</span><span class="sxs-lookup"><span data-stu-id="09960-119">Remote systems are only discoverable through cloud connection.</span></span> |
| <span data-ttu-id="09960-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span><span class="sxs-lookup"><span data-stu-id="09960-120">MCDRemoteSystemDiscoveryTypeSpatiallyProximal</span></span> | <span data-ttu-id="09960-121">3</span><span class="sxs-lookup"><span data-stu-id="09960-121">3</span></span>     | <span data-ttu-id="09960-122">Los sistemas remotos son reconocibles a través de una conexión articulaciones próximas y se esperan que sean</span><span class="sxs-lookup"><span data-stu-id="09960-122">Remote systems are discoverable through a proximal connection and are expected to be</span></span>
<span data-ttu-id="09960-123">espacialmente cerca del dispositivo de cliente (en el intervalo de Bluetooth, por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="09960-123">spatially near to the client device (in Bluetooth range, for example).</span></span>  |

