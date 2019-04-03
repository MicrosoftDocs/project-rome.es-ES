---
title: MCDAppServiceProvider
description: Este protocolo contiene métodos para hacer que un servicio de aplicación local puede tener acceso a los dispositivos remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: f5af56a2c87e3b4335a2a59a0130ef3622af6c26
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908667"
---
# <a name="protocol-mcdappserviceprovider"></a><span data-ttu-id="706db-104">Protocolo `MCDAppServiceProvider`</span><span class="sxs-lookup"><span data-stu-id="706db-104">protocol `MCDAppServiceProvider`</span></span>

```
@protocol MCDAppServiceProvider<NSObject>
```

<span data-ttu-id="706db-105">Este protocolo contiene métodos para hacer que un servicio de aplicación local puede tener acceso a los dispositivos remotos.</span><span class="sxs-lookup"><span data-stu-id="706db-105">This protocol contains methods for making a local app service accessible to remote devices.</span></span> <span data-ttu-id="706db-106">Los desarrolladores deben implementar este protocolo para que sus servicios de aplicación esté disponible para la conectividad remota.</span><span class="sxs-lookup"><span data-stu-id="706db-106">Developers must implement this protocol to make their app services available for remote connectivity.</span></span>

## <a name="properties"></a><span data-ttu-id="706db-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="706db-107">Properties</span></span>
 
### <a name="appserviceinfo"></a><span data-ttu-id="706db-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="706db-108">appServiceInfo</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="706db-109">La información descriptiva acerca de este servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="706db-109">The descriptive information about this app service.</span></span>

## <a name="methods"></a><span data-ttu-id="706db-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="706db-110">Methods</span></span>

### <a name="connectiondidopen"></a><span data-ttu-id="706db-111">connectionDidOpen</span><span class="sxs-lookup"><span data-stu-id="706db-111">connectionDidOpen</span></span>
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

<span data-ttu-id="706db-112">Este método se llama cuando se abre una conexión de servicio de aplicación remota para este servicio de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="706db-112">This method is called when a remote app service connection is opened to this app service.</span></span>

#### <a name="parameters"></a><span data-ttu-id="706db-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="706db-113">Parameters</span></span> 
* `openedInfo`

<span data-ttu-id="706db-114">Una instancia de MDCAppServiceConnectionOpenedInfo que contiene información para la mensajería de remoto con el servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="706db-114">A MDCAppServiceConnectionOpenedInfo instance containing information for remote messaging with the app service.</span></span>