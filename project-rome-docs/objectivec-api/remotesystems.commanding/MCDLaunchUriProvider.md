---
title: MCDLaunchUriProvider
description: Obtenga información sobre el protocolo MCDLaunchUriProvider. Este protocolo se utiliza para administrar el control de un URI a través del inicio de una aplicación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 3339f9b5c8ab14dddf519618795c4150b69dfe3e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760759"
---
# <a name="protocol-mcdlaunchuriprovider"></a><span data-ttu-id="fc5b0-105">n° `MCDLaunchUriProvider`</span><span class="sxs-lookup"><span data-stu-id="fc5b0-105">protocol `MCDLaunchUriProvider`</span></span>

```
@protocol MCDLaunchUriProvider <NSObject>
```

<span data-ttu-id="fc5b0-106">Esta clase administra el control de un identificador URI mediante el inicio de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-106">This class manages the handling of a URI through the launching of an application.</span></span>

## <a name="properties"></a><span data-ttu-id="fc5b0-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="fc5b0-107">Properties</span></span> 
### <a name="supportedurischemes"></a><span data-ttu-id="fc5b0-108">supportedUriSchemes</span><span class="sxs-lookup"><span data-stu-id="fc5b0-108">supportedUriSchemes</span></span>
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

<span data-ttu-id="fc5b0-109">Matriz de cadenas que representan los esquemas de URI admitidos.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-109">An array of strings representing supported URI schemes.</span></span>

## <a name="methods"></a><span data-ttu-id="fc5b0-110">Métodos</span><span class="sxs-lookup"><span data-stu-id="fc5b0-110">Methods</span></span>

### <a name="onlaunchuriasync"></a><span data-ttu-id="fc5b0-111">onLaunchUriAsync</span><span class="sxs-lookup"><span data-stu-id="fc5b0-111">onLaunchUriAsync</span></span>
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

<span data-ttu-id="fc5b0-112">Se llama a este método cuando un dispositivo remoto intenta iniciar un URI en este dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-112">This method is called when a remote device attempts to launch a URI on this device.</span></span>

#### <a name="parameters"></a><span data-ttu-id="fc5b0-113">Parámetros</span><span class="sxs-lookup"><span data-stu-id="fc5b0-113">Parameters</span></span> 
* <span data-ttu-id="fc5b0-114">`uri` URI que se va a iniciar.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-114">`uri` The URI to launch.</span></span>
* <span data-ttu-id="fc5b0-115">`options` Conjunto de opciones para iniciar el URI.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-115">`options` A set of options for launching the URI.</span></span> <span data-ttu-id="fc5b0-116">El URI de reserva es solo una de las opciones posibles que se pueden establecer.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-116">The fallback URI is only one of the possible options that can be set.</span></span>
* <span data-ttu-id="fc5b0-117">`completionBlock` Bloque de código que se va a ejecutar cuando se complete.</span><span class="sxs-lookup"><span data-stu-id="fc5b0-117">`completionBlock` The code block to execute upon completion.</span></span>