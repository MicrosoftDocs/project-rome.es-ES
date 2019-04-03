---
title: MCDRemoteSystemConnectionInfo
description: Una clase que proporciona más información acerca de una instancia de MCDAppServiceConnection especificada.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: cdfe9dec49e90013f8c967223803144ad655378e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907057"
---
# <a name="class-mcdremotesystemconnectioninfo"></a><span data-ttu-id="0f6be-104">Clase `MCDRemoteSystemConnectionInfo`</span><span class="sxs-lookup"><span data-stu-id="0f6be-104">class `MCDRemoteSystemConnectionInfo`</span></span> 

```
@interface MCDRemoteSystemConnectionInfo : NSObject
```  

<span data-ttu-id="0f6be-105">Una clase que proporciona más información acerca de un determinado **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instancia.</span><span class="sxs-lookup"><span data-stu-id="0f6be-105">A class that provides further information about a given **[MCDAppServiceConnection](MCDAppServiceConnection.md)** instance.</span></span>

## <a name="properties"></a><span data-ttu-id="0f6be-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0f6be-106">Properties</span></span>

### <a name="proximal"></a><span data-ttu-id="0f6be-107">proximal</span><span class="sxs-lookup"><span data-stu-id="0f6be-107">proximal</span></span>
`@property(nonatomic, readonly, getter=isProximal) BOOL proximal;`

<span data-ttu-id="0f6be-108">Muestra si la conexión asociada es una conexión articulaciones próximas (**Sí**) o no (**n**).</span><span class="sxs-lookup"><span data-stu-id="0f6be-108">Displays whether the associated connection is a proximal connection (**YES**) or not (**NO**).</span></span>

## <a name="constructors"></a><span data-ttu-id="0f6be-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="0f6be-109">Constructors</span></span>

### <a name="trycreatefromappserviceconnection"></a><span data-ttu-id="0f6be-110">tryCreateFromAppServiceConnection</span><span class="sxs-lookup"><span data-stu-id="0f6be-110">tryCreateFromAppServiceConnection</span></span>
`+ (nullable instancetype)tryCreateFromAppServiceConnection:(nonnull MCDAppServiceConnection*)appServiceConnection;`

<span data-ttu-id="0f6be-111">Crea una instancia de esta clase de la conexión de servicio de aplicación determinada.</span><span class="sxs-lookup"><span data-stu-id="0f6be-111">Creates an instance of this class from the given app service connection.</span></span>

#### <a name="parameters"></a><span data-ttu-id="0f6be-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="0f6be-112">Parameters</span></span>
* `appServiceConnection` 

<span data-ttu-id="0f6be-113">Un **MCDAppServiceConnection** instancia.</span><span class="sxs-lookup"><span data-stu-id="0f6be-113">An **MCDAppServiceConnection** instance.</span></span>

#### <a name="returns"></a><span data-ttu-id="0f6be-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="0f6be-114">Returns</span></span>
<span data-ttu-id="0f6be-115">Devuelve una instancia de esta clase correspondiente a la conexión de servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="0f6be-115">Returns an instance of this class corresponding to the app service connection.</span></span>