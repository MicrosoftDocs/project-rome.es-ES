---
title: MCDRemoteSystem
description: Una clase para representar un sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5f0ab2108d4efa486b992bf7bc8c8847692623da
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801767"
---
# <a name="class-mcdremotesystem"></a>Clase `MCDRemoteSystem` 

```
@interface MCDRemoteSystem : NSObject
```  

Una clase para representar un sistema remoto.

## <a name="properties"></a>Propiedades

### <a name="kind"></a>Tipo
`@property(nonatomic, readonly, nonnull) NSString* kind;`

El tipo de dispositivo de este sistema remoto.

### <a name="systemid"></a>systemId
`@property(nonatomic, readonly, nonnull) NSString* systemId;`

El identificador para este sistema remoto.

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

El nombre de un sistema remoto concreto.

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemStatus status;`

El estado de disponibilidad del sistema remoto.

> [!NOTE]
Se usa la presencia WNS para los informes de disponibilidad para los dispositivos de Windows y las aplicaciones que usan WNS como tipo de notificación.  RemoteSystem se marcará como "disponible" cuando el dispositivo se considera disponible (Windows) o cuando una de las aplicaciones subyacentes notifica su presencia como disponible (iOS y Android). 

### <a name="manufacturerdisplayname"></a>manufacturerDisplayName
`@property(nonatomic, readonly, nonnull) NSString* manufacturerDisplayName;`

El nombre del fabricante del sistema remoto determinado.

### <a name="modeldisplayname"></a>modelDisplayName
`@property(nonatomic, readonly, nonnull) NSString* modelDisplayName;`

El nombre del modelo de un sistema remoto concreto.

### <a name="apps"></a>aplicaciones
`@property(nonatomic, readonly, nonnull) NSArray<MCDRemoteSystemApp*>* apps;`

Una matriz de las aplicaciones en este sistema remoto que están disponibles para la conectividad.

### <a name="platform"></a>Plataforma
`@property(nonatomic, readonly) MCDRemoteSystemPlatform platform;`

La administración de la actividad del sistema remoto MCDRemoteSystemPlatform.