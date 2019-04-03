---
title: MCDAppServiceConnectionOpenedInfo
description: Esta clase proporciona datos para el evento MCDAppServiceProvider.connectionDidOpen, que se produce cuando un dispositivo remoto abre una conexión a un servicio de aplicación local.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907557"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a><span data-ttu-id="85159-104">Clase `MCDAppServiceConnectionOpenedInfo`</span><span class="sxs-lookup"><span data-stu-id="85159-104">class `MCDAppServiceConnectionOpenedInfo`</span></span> 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

<span data-ttu-id="85159-105">Esta clase proporciona datos para el evento MCDAppServiceProvider.connectionDidOpen, que se produce cuando un dispositivo remoto abre una conexión a un servicio de aplicación local.</span><span class="sxs-lookup"><span data-stu-id="85159-105">This class provides data for the MCDAppServiceProvider.connectionDidOpen event, which is raised when a remote device opens a connection to a local app service.</span></span>

## <a name="properties"></a><span data-ttu-id="85159-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="85159-106">Properties</span></span>

### <a name="appserviceconnection"></a><span data-ttu-id="85159-107">appServiceConnection</span><span class="sxs-lookup"><span data-stu-id="85159-107">appServiceConnection</span></span>
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

<span data-ttu-id="85159-108">Una instancia de MCDAppServiceConnection que representa la conexión entre el servicio de aplicación local y el dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="85159-108">An MCDAppServiceConnection instance representing the connection between the local app service and the remote device.</span></span>

### <a name="remotesystemapp"></a><span data-ttu-id="85159-109">remoteSystemApp</span><span class="sxs-lookup"><span data-stu-id="85159-109">remoteSystemApp</span></span>
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

<span data-ttu-id="85159-110">La aplicación remota MCDRemoteSystemApp que inician una conexión con el servicio de aplicación local.</span><span class="sxs-lookup"><span data-stu-id="85159-110">The MCDRemoteSystemApp remote application that initiated a connection to the local app service.</span></span>