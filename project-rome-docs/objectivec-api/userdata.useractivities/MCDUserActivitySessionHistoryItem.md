---
title: MCDUserActivitySessionHistoryItem
description: Esta clase proporciona la hora de inicio y finalización que un usuario estaba implicado en una actividad concreta.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801637"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a><span data-ttu-id="962ba-104">Clase `MCDUserActivitySessionHistoryItem`</span><span class="sxs-lookup"><span data-stu-id="962ba-104">class `MCDUserActivitySessionHistoryItem`</span></span>

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

<span data-ttu-id="962ba-105">Esta clase proporciona la hora de inicio y finalización que un usuario estaba implicado en una actividad concreta.</span><span class="sxs-lookup"><span data-stu-id="962ba-105">This class provides the start and end time that a user was engaged in a particular activity.</span></span>


## <a name="properties"></a><span data-ttu-id="962ba-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="962ba-106">Properties</span></span>

### <a name="useractivity"></a><span data-ttu-id="962ba-107">userActivity</span><span class="sxs-lookup"><span data-stu-id="962ba-107">userActivity</span></span>
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

<span data-ttu-id="962ba-108">La actividad del usuario cuyo historial que representa esta instancia de clase.</span><span class="sxs-lookup"><span data-stu-id="962ba-108">The user activity whose history this class instance represents.</span></span>

### <a name="starttime"></a><span data-ttu-id="962ba-109">startTime</span><span class="sxs-lookup"><span data-stu-id="962ba-109">startTime</span></span>
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

<span data-ttu-id="962ba-110">La hora en que el usuario inició atractivo en la actividad asociada.</span><span class="sxs-lookup"><span data-stu-id="962ba-110">The time when the user started engaging in the associated activity.</span></span>

### <a name="endtime"></a><span data-ttu-id="962ba-111">endTime</span><span class="sxs-lookup"><span data-stu-id="962ba-111">endTime</span></span>
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

<span data-ttu-id="962ba-112">El tiempo cuando el usuario detuvo la participación en la actividad asociada.</span><span class="sxs-lookup"><span data-stu-id="962ba-112">The time when the user stopped engaging in the associated activity.</span></span>

### <a name="remotesystemid"></a><span data-ttu-id="962ba-113">remoteSystemId</span><span class="sxs-lookup"><span data-stu-id="962ba-113">remoteSystemId</span></span>
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

<span data-ttu-id="962ba-114">La cadena que indica el identificador del sistema remoto del dispositivo del usuario dedicados a esta actividad.</span><span class="sxs-lookup"><span data-stu-id="962ba-114">The string indicating the remote system id of the device the user engaged this activity on.</span></span>