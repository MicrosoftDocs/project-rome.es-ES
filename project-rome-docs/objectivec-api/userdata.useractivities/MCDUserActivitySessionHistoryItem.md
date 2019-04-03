---
title: MCDUserActivitySessionHistoryItem
description: Esta clase proporciona la hora de inicio y finalización que un usuario estaba implicado en una actividad concreta.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 3a480d9d0d028973554c13ee162b359502c8a772
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907407"
---
# <a name="class-mcduseractivitysessionhistoryitem"></a>Clase `MCDUserActivitySessionHistoryItem`

```
@interface MCDUserActivitySessionHistoryItem : NSObject
```

Esta clase proporciona la hora de inicio y finalización que un usuario estaba implicado en una actividad concreta.


## <a name="properties"></a>Propiedades

### <a name="useractivity"></a>userActivity
`@property(nonatomic, readonly, nonnull) MCDUserActivity* userActivity;`

La actividad del usuario cuyo historial que representa esta instancia de clase.

### <a name="starttime"></a>startTime
`@property(nonatomic, readonly, nonnull) NSDate* startTime;`

La hora en que el usuario inició atractivo en la actividad asociada.

### <a name="endtime"></a>endTime
`@property(nonatomic, readonly, nullable) NSDate* endTime;`

El tiempo cuando el usuario detuvo la participación en la actividad asociada.

### <a name="remotesystemid"></a>remoteSystemId
`@property(nonatomic, readonly, nullable) NSString* remoteSystemId;`

La cadena que indica el identificador del sistema remoto del dispositivo del usuario dedicados a esta actividad.