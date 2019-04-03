---
title: MCDRemoteSystem
description: Una clase para representar un sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5f0ab2108d4efa486b992bf7bc8c8847692623da
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909267"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="fd3ac-104">Clase `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="fd3ac-104">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="fd3ac-105">Una clase para representar un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-105">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="fd3ac-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="fd3ac-106">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="fd3ac-107">Tipo</span><span class="sxs-lookup"><span data-stu-id="fd3ac-107">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="fd3ac-108">El tipo de dispositivo de este sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-108">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="fd3ac-109">systemId</span><span class="sxs-lookup"><span data-stu-id="fd3ac-109">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="fd3ac-110">El identificador para este sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-110">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="fd3ac-111">displayName</span><span class="sxs-lookup"><span data-stu-id="fd3ac-111">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="fd3ac-112">El nombre de un sistema remoto concreto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-112">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="fd3ac-113">status</span><span class="sxs-lookup"><span data-stu-id="fd3ac-113">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="fd3ac-114">El estado de disponibilidad del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-114">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="fd3ac-115">Se usa la presencia WNS para los informes de disponibilidad para los dispositivos de Windows y las aplicaciones que usan WNS como tipo de notificación.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-115">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="fd3ac-116">RemoteSystem se marcará como "disponible" cuando el dispositivo se considera disponible (Windows) o cuando una de las aplicaciones subyacentes notifica su presencia como disponible (iOS y Android).</span><span class="sxs-lookup"><span data-stu-id="fd3ac-116">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="fd3ac-117">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="fd3ac-117">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="fd3ac-118">El nombre del fabricante del sistema remoto determinado.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-118">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="fd3ac-119">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="fd3ac-119">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="fd3ac-120">El nombre del modelo de un sistema remoto concreto.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-120">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="fd3ac-121">aplicaciones</span><span class="sxs-lookup"><span data-stu-id="fd3ac-121">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="fd3ac-122">Una matriz de las aplicaciones en este sistema remoto que están disponibles para la conectividad.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-122">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="fd3ac-123">Plataforma</span><span class="sxs-lookup"><span data-stu-id="fd3ac-123">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="fd3ac-124">La administración de la actividad del sistema remoto MCDRemoteSystemPlatform.</span><span class="sxs-lookup"><span data-stu-id="fd3ac-124">The MCDRemoteSystemPlatform managing remote system activity.</span></span>