---
title: MCDUserActivitySession
description: Esta clase realiza el seguimiento de una actividad de usuario ([MCDUserActivity](MCDUserActivity.md) instancia) mientras el usuario está ocupado en esa actividad.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 2ae85e637bb059e811a60e5bde5f33ea767c8314
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909637"
---
# <a name="class-mcduseractivitysession"></a><span data-ttu-id="a0aeb-104">Clase `MCDUserActivitySession`</span><span class="sxs-lookup"><span data-stu-id="a0aeb-104">class `MCDUserActivitySession`</span></span>

```
@interface MCDUserActivitySession : NSObject
```

<span data-ttu-id="a0aeb-105">Esta clase realiza el seguimiento de engagement para una actividad de usuario especificado ([MCDUserActivity](MCDUserActivity.md) instancia).</span><span class="sxs-lookup"><span data-stu-id="a0aeb-105">This class tracks engagement for a specified user activity ([MCDUserActivity](MCDUserActivity.md) instance).</span></span>

<span data-ttu-id="a0aeb-106">Un [MCDUserActivity](MCDUserActivity.md) está asociado con un MCDUserActivitySession que realiza el seguimiento de cuánto tiempo el usuario está ocupado en esa actividad.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-106">A [MCDUserActivity](MCDUserActivity.md) is associated with an MCDUserActivitySession which tracks how long the user is engaged in that activity.</span></span> <span data-ttu-id="a0aeb-107">Por ejemplo, puede producirse una actividad, como ver una película activado y desactivado durante el transcurso de varios días.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-107">For example, an activity such as watching a movie can occur on-and-off over the course of multiple days.</span></span> <span data-ttu-id="a0aeb-108">Cuando el usuario inicia por primera vez la nueva actividad de cómo se ve una película, se debe crear un MCDUserActivitySession.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-108">When the user first starts the new activity of watching a movie, a MCDUserActivitySession must be created.</span></span> <span data-ttu-id="a0aeb-109">Debe eliminarse cuando el usuario cambia a otra actividad.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-109">It should be disposed when the user switches to a different activity.</span></span> <span data-ttu-id="a0aeb-110">Cuando se reanuda el usuario, la aplicación debe crear otra **MCDUserActivitySession** del original [MCDUserActivity](MCDUserActivity.md) para realizar un seguimiento de la actividad siempre que el usuario está viendo la película.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-110">When the user resumes, the app should create another **MCDUserActivitySession** from the original [MCDUserActivity](MCDUserActivity.md) to track the activity as long as the user is watching the movie.</span></span>


## <a name="properties"></a><span data-ttu-id="a0aeb-111">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a0aeb-111">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="a0aeb-112">activityId</span><span class="sxs-lookup"><span data-stu-id="a0aeb-112">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="a0aeb-113">Un identificador único para el MCDUserActivity asociado con este MCDUserActivitySession.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-113">A unique ID for the MCDUserActivity associated with this MCDUserActivitySession.</span></span>

## <a name="methods"></a><span data-ttu-id="a0aeb-114">Métodos</span><span class="sxs-lookup"><span data-stu-id="a0aeb-114">Methods</span></span>

### <a name="stop"></a><span data-ttu-id="a0aeb-115">stop</span><span class="sxs-lookup"><span data-stu-id="a0aeb-115">stop</span></span>
`- (void)stop;`

<span data-ttu-id="a0aeb-116">Detiene esta sesión de la actividad.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-116">Stops this activity session.</span></span> <span data-ttu-id="a0aeb-117">Esto se debe llamar cuando el usuario ya no participa en la actividad asociada a esta sesión.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-117">This should be called when the user is no longer engaged in the activity associated with this session.</span></span>