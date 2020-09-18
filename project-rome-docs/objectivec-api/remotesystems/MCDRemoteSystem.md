---
title: MCDRemoteSystem
description: Obtenga información sobre la clase MCDRemoteSystem y sus propiedades. Esta clase se utiliza para representar un sistema remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: e211de33117f48cc221152cf40645015693dcddc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760999"
---
# <a name="class-mcdremotesystem"></a><span data-ttu-id="a2a15-105">las `MCDRemoteSystem`</span><span class="sxs-lookup"><span data-stu-id="a2a15-105">class `MCDRemoteSystem`</span></span> 

```
@interface MCDRemoteSystem : NSObject
```  

<span data-ttu-id="a2a15-106">Una clase para representar un sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="a2a15-106">A class to represent a remote system.</span></span>

## <a name="properties"></a><span data-ttu-id="a2a15-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a2a15-107">Properties</span></span>

### <a name="kind"></a><span data-ttu-id="a2a15-108">kind</span><span class="sxs-lookup"><span data-stu-id="a2a15-108">kind</span></span>
`@property(nonatomic, readonly, nonnull) NSString* kind;`

<span data-ttu-id="a2a15-109">El tipo de dispositivo de este sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="a2a15-109">The device type of this remote system.</span></span>

### <a name="systemid"></a><span data-ttu-id="a2a15-110">systemId</span><span class="sxs-lookup"><span data-stu-id="a2a15-110">systemId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

<span data-ttu-id="a2a15-111">Identificador de este sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="a2a15-111">The identifier for this remote system.</span></span>

### <a name="displayname"></a><span data-ttu-id="a2a15-112">DisplayName</span><span class="sxs-lookup"><span data-stu-id="a2a15-112">displayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

<span data-ttu-id="a2a15-113">Nombre del sistema remoto especificado.</span><span class="sxs-lookup"><span data-stu-id="a2a15-113">The name of the given remote system.</span></span>

### <a name="status"></a><span data-ttu-id="a2a15-114">status</span><span class="sxs-lookup"><span data-stu-id="a2a15-114">status</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

<span data-ttu-id="a2a15-115">El estado de disponibilidad de este sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="a2a15-115">The status of this remote system's availability.</span></span>

> [!NOTE]
<span data-ttu-id="a2a15-116">La presencia de WNS se usa para notificar la disponibilidad de los dispositivos y las aplicaciones de Windows que usan WNS como tipo de notificación.</span><span class="sxs-lookup"><span data-stu-id="a2a15-116">WNS presence is used for reporting availability for Windows devices and apps which use WNS as notification type.</span></span>  <span data-ttu-id="a2a15-117">RemoteSystem se marcará como "disponible" cuando el dispositivo se considere disponible (Windows) o cuando una de las aplicaciones subyacentes notifique su presencia como disponible (iOS y Android).</span><span class="sxs-lookup"><span data-stu-id="a2a15-117">RemoteSystem will be marked as "available" when the device is considered available (Windows) or when one of the underlying apps reports their presence as available (iOS and Android).</span></span> 

### <a name="manufacturerdisplayname"></a><span data-ttu-id="a2a15-118">manufacturerDisplayName</span><span class="sxs-lookup"><span data-stu-id="a2a15-118">manufacturerDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

<span data-ttu-id="a2a15-119">Nombre del fabricante del sistema remoto especificado.</span><span class="sxs-lookup"><span data-stu-id="a2a15-119">The manufacturer name of the given remote system.</span></span>

### <a name="modeldisplayname"></a><span data-ttu-id="a2a15-120">modelDisplayName</span><span class="sxs-lookup"><span data-stu-id="a2a15-120">modelDisplayName</span></span>
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

<span data-ttu-id="a2a15-121">Nombre del modelo del sistema remoto especificado.</span><span class="sxs-lookup"><span data-stu-id="a2a15-121">The model name of the given remote system.</span></span>

### <a name="apps"></a><span data-ttu-id="a2a15-122">aplicaciones</span><span class="sxs-lookup"><span data-stu-id="a2a15-122">apps</span></span>
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

<span data-ttu-id="a2a15-123">Una matriz de las aplicaciones de este sistema remoto que están disponibles para la conectividad.</span><span class="sxs-lookup"><span data-stu-id="a2a15-123">An array of the applications on this remote system that are available for connectivity.</span></span>

### <a name="platform"></a><span data-ttu-id="a2a15-124">platform</span><span class="sxs-lookup"><span data-stu-id="a2a15-124">platform</span></span>
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

<span data-ttu-id="a2a15-125">La MCDRemoteSystemPlatform administración de la actividad del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="a2a15-125">The MCDRemoteSystemPlatform managing remote system activity.</span></span>