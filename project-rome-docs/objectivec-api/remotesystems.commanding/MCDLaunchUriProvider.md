---
title: MCDLaunchUriProvider
description: ''
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4cbfaa9fd1e88345f4ce35987508b061e479854e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907467"
---
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="f9f1c-103">Protocolo `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="f9f1c-103">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="f9f1c-104">Esta clase administra el control de un identificador URI mediante el inicio de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-104">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="f9f1c-105">Propiedades</span><span class="sxs-lookup"><span data-stu-id="f9f1c-105">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="f9f1c-106">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="f9f1c-106">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="f9f1c-107">Una matriz de cadenas que representan admite esquemas de URI.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-107">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="f9f1c-108">Métodos</span><span class="sxs-lookup"><span data-stu-id="f9f1c-108">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="f9f1c-109">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="f9f1c-109">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="f9f1c-110">Este método se llama cuando un dispositivo remoto intenta iniciar un URI de este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-110">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f9f1c-111">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f9f1c-111">Parameters</span></span> 
* <span data-ttu-id="f9f1c-112">`uri` El URI para iniciar.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-112">`uri` The URI to launch.</span></span>
* <span data-ttu-id="f9f1c-113">`options` Un conjunto de opciones para iniciar el URI.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-113">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="f9f1c-114">URI de la reserva es sólo una de las opciones posibles que se pueden establecer.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-114">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="f9f1c-115">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="f9f1c-115">`completionBlock` The code block to execute upon completion.</span></span>