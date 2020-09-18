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
# <a name="class-mcdremotesystem"></a>las `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

Una clase para representar un sistema remoto.

## <a name="properties"></a>Propiedades

### <a name="kind"></a>kind
`@property(nonatomic, readonly, nonnull) NSString* kind;`

El tipo de dispositivo de este sistema remoto.

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

Identificador de este sistema remoto.

### <a name="displayname"></a>DisplayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

Nombre del sistema remoto especificado.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

El estado de disponibilidad de este sistema remoto.

> [!NOTE]
La presencia de WNS se usa para notificar la disponibilidad de los dispositivos y las aplicaciones de Windows que usan WNS como tipo de notificación.  RemoteSystem se marcará como "disponible" cuando el dispositivo se considere disponible (Windows) o cuando una de las aplicaciones subyacentes notifique su presencia como disponible (iOS y Android). 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

Nombre del fabricante del sistema remoto especificado.

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

Nombre del modelo del sistema remoto especificado.

### <a name="apps"></a>aplicaciones
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

Una matriz de las aplicaciones de este sistema remoto que están disponibles para la conectividad.

### <a name="platform"></a>platform
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

La MCDRemoteSystemPlatform administración de la actividad del sistema remoto.