---
title: MCDRemoteLauncher
description: Una clase que se utiliza para iniciar una aplicación en un dispositivo remoto mediante un URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: aa0211c1edc33e8a277c4954d94fbcbb6565c923
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907387"
---
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="e7a6d-104">Clase `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="e7a6d-104">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="e7a6d-105">Una clase que se utiliza para iniciar una aplicación en un dispositivo remoto mediante un URI.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-105">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="e7a6d-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="e7a6d-106">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="e7a6d-107">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="e7a6d-107">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="e7a6d-108">Inicia un URI con el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="e7a6d-108">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="e7a6d-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7a6d-109">Parameters</span></span>
* <span data-ttu-id="e7a6d-110">`uri` El URI que hará que el inicio de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-110">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="e7a6d-111">Si el destino es Windows, se elegirá la aplicación de destino en función de esquema.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-111">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="e7a6d-112">Si el destino es que no son de Windows, la aplicación de destino se elegirá según la MCDRemoteSystemConnectionRequest.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-112">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="e7a6d-113">`connection` Especifica qué sistema remoto o una aplicación para conectarse a.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-113">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="e7a6d-114">`completionBlock` El bloque para invocar la finalización.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-114">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="e7a6d-115">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="e7a6d-115">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="e7a6d-116">Inicia un URI con las opciones en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="e7a6d-116">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="e7a6d-117">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7a6d-117">Parameters</span></span>
* <span data-ttu-id="e7a6d-118">`uri` El URI que hará que el inicio de una aplicación, según su esquema.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-118">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="e7a6d-119">`connection` Especifica qué sistema remoto o una aplicación para conectarse a.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-119">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="e7a6d-120">`options` Las especificaciones de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-120">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="e7a6d-121">`completionBlock` El bloque para invocar la finalización.</span><span class="sxs-lookup"><span data-stu-id="e7a6d-121">`completionBlock` The block to invoke upon completion.</span></span>