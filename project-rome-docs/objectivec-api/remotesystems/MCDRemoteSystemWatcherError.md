---
title: MCDRemoteSystemWatcherError
description: Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801727"
---
# <a name="enum-mcdremotesystemwatchererror"></a><span data-ttu-id="1bded-104">Enum `MCDRemoteSystemWatcherError`</span><span class="sxs-lookup"><span data-stu-id="1bded-104">enum `MCDRemoteSystemWatcherError`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 <span data-ttu-id="1bded-105">Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.</span><span class="sxs-lookup"><span data-stu-id="1bded-105">Contains values that the describe an error encountered by a remote system watcher object during the discovery process.</span></span>

## <a name="fields"></a><span data-ttu-id="1bded-106">Campos</span><span class="sxs-lookup"><span data-stu-id="1bded-106">Fields</span></span>

| <span data-ttu-id="1bded-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="1bded-107">Name</span></span>                              | <span data-ttu-id="1bded-108">Valor</span><span class="sxs-lookup"><span data-stu-id="1bded-108">Value</span></span> | <span data-ttu-id="1bded-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="1bded-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="1bded-110">MCDRemoteSystemWatcherErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="1bded-110">MCDRemoteSystemWatcherErrorUnknown</span></span> | <span data-ttu-id="1bded-111">0</span><span class="sxs-lookup"><span data-stu-id="1bded-111">0</span></span> | <span data-ttu-id="1bded-112">El monitor encontró un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="1bded-112">The watcher encountered an unknown error.</span></span> |
| <span data-ttu-id="1bded-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span><span class="sxs-lookup"><span data-stu-id="1bded-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span></span> | <span data-ttu-id="1bded-114">1</span><span class="sxs-lookup"><span data-stu-id="1bded-114">1</span></span> | <span data-ttu-id="1bded-115">Se produjo el error porque se ha perdido la conexión a Internet.</span><span class="sxs-lookup"><span data-stu-id="1bded-115">The error occurred because the Internet connection was lost.</span></span> |
| <span data-ttu-id="1bded-116">MCDRemoteSystemWatcherErrorAuthenticationError</span><span class="sxs-lookup"><span data-stu-id="1bded-116">MCDRemoteSystemWatcherErrorAuthenticationError</span></span> | <span data-ttu-id="1bded-117">2</span><span class="sxs-lookup"><span data-stu-id="1bded-117">2</span></span> | <span data-ttu-id="1bded-118">Se produjo el error porque no se pudo autenticar un ConnectedDevicesAccount que se usa para ejecutar la detección.</span><span class="sxs-lookup"><span data-stu-id="1bded-118">The error occurred because a ConnectedDevicesAccount being used to run the discovery could not be authenticated.</span></span> | 
