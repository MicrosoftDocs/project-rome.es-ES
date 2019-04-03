---
title: MCDRemoteSystemWatcherError
description: Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907707"
---
# <a name="enum-mcdremotesystemwatchererror"></a><span data-ttu-id="4ae82-104">Enum `MCDRemoteSystemWatcherError`</span><span class="sxs-lookup"><span data-stu-id="4ae82-104">enum `MCDRemoteSystemWatcherError`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 <span data-ttu-id="4ae82-105">Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.</span><span class="sxs-lookup"><span data-stu-id="4ae82-105">Contains values that the describe an error encountered by a remote system watcher object during the discovery process.</span></span>

## <a name="fields"></a><span data-ttu-id="4ae82-106">Campos</span><span class="sxs-lookup"><span data-stu-id="4ae82-106">Fields</span></span>

| <span data-ttu-id="4ae82-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="4ae82-107">Name</span></span>                              | <span data-ttu-id="4ae82-108">Valor</span><span class="sxs-lookup"><span data-stu-id="4ae82-108">Value</span></span> | <span data-ttu-id="4ae82-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="4ae82-109">Description</span></span>                    |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="4ae82-110">MCDRemoteSystemWatcherErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="4ae82-110">MCDRemoteSystemWatcherErrorUnknown</span></span> | <span data-ttu-id="4ae82-111">0</span><span class="sxs-lookup"><span data-stu-id="4ae82-111">0</span></span> | <span data-ttu-id="4ae82-112">El monitor encontró un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="4ae82-112">The watcher encountered an unknown error.</span></span> |
| <span data-ttu-id="4ae82-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span><span class="sxs-lookup"><span data-stu-id="4ae82-113">MCDRemoteSystemWatcherErrorInternetNotAvailable</span></span> | <span data-ttu-id="4ae82-114">1</span><span class="sxs-lookup"><span data-stu-id="4ae82-114">1</span></span> | <span data-ttu-id="4ae82-115">Se produjo el error porque se ha perdido la conexión a Internet.</span><span class="sxs-lookup"><span data-stu-id="4ae82-115">The error occurred because the Internet connection was lost.</span></span> |
| <span data-ttu-id="4ae82-116">MCDRemoteSystemWatcherErrorAuthenticationError</span><span class="sxs-lookup"><span data-stu-id="4ae82-116">MCDRemoteSystemWatcherErrorAuthenticationError</span></span> | <span data-ttu-id="4ae82-117">2</span><span class="sxs-lookup"><span data-stu-id="4ae82-117">2</span></span> | <span data-ttu-id="4ae82-118">Se produjo el error porque no se pudo autenticar un ConnectedDevicesAccount que se usa para ejecutar la detección.</span><span class="sxs-lookup"><span data-stu-id="4ae82-118">The error occurred because a ConnectedDevicesAccount being used to run the discovery could not be authenticated.</span></span> | 
