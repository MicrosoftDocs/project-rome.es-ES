---
title: MCDRemoteLauncher
description: Obtenga información sobre la clase MCDRemoteLauncher. Esta clase se usa para iniciar una aplicación en un dispositivo remoto mediante un URI.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: e5231897241e54c44b4f3fb299adf68af396cac9
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760749"
---
# <a name="class-mcdremotelauncher"></a><span data-ttu-id="e7326-105">las `MCDRemoteLauncher`</span><span class="sxs-lookup"><span data-stu-id="e7326-105">class `MCDRemoteLauncher`</span></span> 

```
@interface MCDRemoteLauncher : NSObject
```  

<span data-ttu-id="e7326-106">Una clase que se usa para iniciar una aplicación en un dispositivo remoto mediante un URI.</span><span class="sxs-lookup"><span data-stu-id="e7326-106">A class used to launch an app on a remote device using a URI.</span></span>


## <a name="methods"></a><span data-ttu-id="e7326-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="e7326-107">Methods</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="e7326-108">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="e7326-108">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="e7326-109">Inicia un URI en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="e7326-109">Launches a URI against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="e7326-110">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7326-110">Parameters</span></span>
* <span data-ttu-id="e7326-111">`uri` El URI que hará que se inicie una aplicación.</span><span class="sxs-lookup"><span data-stu-id="e7326-111">`uri` The URI which will cause the launching of an app.</span></span>  <span data-ttu-id="e7326-112">Si el destino es Windows, la aplicación de destino se elegirá según el esquema.</span><span class="sxs-lookup"><span data-stu-id="e7326-112">If the target is Windows, the target app will be chosen based on scheme.</span></span> <span data-ttu-id="e7326-113">Si el destino no es Windows, la aplicación de destino se elegirá en función de MCDRemoteSystemConnectionRequest.</span><span class="sxs-lookup"><span data-stu-id="e7326-113">If the target is non-Windows, the target app will be chosen based on the MCDRemoteSystemConnectionRequest.</span></span>

* <span data-ttu-id="e7326-114">`connection` Especifica a qué sistema o aplicación remoto se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="e7326-114">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="e7326-115">`completionBlock` Bloque que se va a invocar al finalizar.</span><span class="sxs-lookup"><span data-stu-id="e7326-115">`completionBlock` The block to invoke upon completion.</span></span>

### <a name="launchuriasync"></a><span data-ttu-id="e7326-116">launchUriAsync</span><span class="sxs-lookup"><span data-stu-id="e7326-116">launchUriAsync</span></span>
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

<span data-ttu-id="e7326-117">Inicia un URI con opciones en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span><span class="sxs-lookup"><span data-stu-id="e7326-117">Launches a URI with options against the Remote System specified in an [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).</span></span>

#### <a name="parameters"></a><span data-ttu-id="e7326-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e7326-118">Parameters</span></span>
* <span data-ttu-id="e7326-119">`uri` El URI que hará que se inicie una aplicación, según su esquema.</span><span class="sxs-lookup"><span data-stu-id="e7326-119">`uri` The URI which will cause the launching of an app, according to its scheme.</span></span>
* <span data-ttu-id="e7326-120">`connection` Especifica a qué sistema o aplicación remoto se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="e7326-120">`connection` Specifies which remote system or application to connect to.</span></span>
* <span data-ttu-id="e7326-121">`options` Especificaciones de inicio de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e7326-121">`options` The launch specifications for the app.</span></span>
* <span data-ttu-id="e7326-122">`completionBlock` Bloque que se va a invocar al finalizar.</span><span class="sxs-lookup"><span data-stu-id="e7326-122">`completionBlock` The block to invoke upon completion.</span></span>