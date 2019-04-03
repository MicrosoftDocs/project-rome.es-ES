---
title: MCDRemoteSystemRemovedEventArgs
description: Argumentos de evento para el evento RemoteSystemWatcher RemoteSystemRemoved.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907047"
---
# <a name="class-mcdremotesystemremovedeventargs"></a><span data-ttu-id="b9716-104">Clase `MCDRemoteSystemRemovedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="b9716-104">class `MCDRemoteSystemRemovedEventArgs`</span></span> 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

<span data-ttu-id="b9716-105">Argumentos de evento para el evento MCDRemoteSystemWatcher.remoteSystemRemoved.</span><span class="sxs-lookup"><span data-stu-id="b9716-105">Event arguments for the MCDRemoteSystemWatcher.remoteSystemRemoved event.</span></span>

## <a name="properties"></a><span data-ttu-id="b9716-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b9716-106">Properties</span></span>

### <a name="remotesystem"></a><span data-ttu-id="b9716-107">remoteSystem</span><span class="sxs-lookup"><span data-stu-id="b9716-107">remoteSystem</span></span>
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

<span data-ttu-id="b9716-108">El sistema remoto MCDRemoteSystem que se ha quitado.</span><span class="sxs-lookup"><span data-stu-id="b9716-108">The MCDRemoteSystem remote system that was removed.</span></span> <span data-ttu-id="b9716-109">Este sistema remoto no debe utilizarse después de este evento.</span><span class="sxs-lookup"><span data-stu-id="b9716-109">This remote system should not be used after this event.</span></span>