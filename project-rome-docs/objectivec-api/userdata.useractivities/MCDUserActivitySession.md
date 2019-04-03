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
# <a name="class-mcduseractivitysession"></a>Clase `MCDUserActivitySession`

```
@interface MCDUserActivitySession : NSObject
```

Esta clase realiza el seguimiento de engagement para una actividad de usuario especificado ([MCDUserActivity](MCDUserActivity.md) instancia).

Un [MCDUserActivity](MCDUserActivity.md) está asociado con un MCDUserActivitySession que realiza el seguimiento de cuánto tiempo el usuario está ocupado en esa actividad. Por ejemplo, puede producirse una actividad, como ver una película activado y desactivado durante el transcurso de varios días. Cuando el usuario inicia por primera vez la nueva actividad de cómo se ve una película, se debe crear un MCDUserActivitySession. Debe eliminarse cuando el usuario cambia a otra actividad. Cuando se reanuda el usuario, la aplicación debe crear otra **MCDUserActivitySession** del original [MCDUserActivity](MCDUserActivity.md) para realizar un seguimiento de la actividad siempre que el usuario está viendo la película.


## <a name="properties"></a>Propiedades

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

Un identificador único para el MCDUserActivity asociado con este MCDUserActivitySession.

## <a name="methods"></a>Métodos

### <a name="stop"></a>stop
`- (void)stop;`

Detiene esta sesión de la actividad. Esto se debe llamar cuando el usuario ya no participa en la actividad asociada a esta sesión.