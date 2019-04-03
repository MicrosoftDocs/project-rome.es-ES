---
title: MCDUserDataFeedSyncScope
description: Esta clase representa los datos de usuario que se sincronizan con la plataforma de dispositivos conectados de back-end cuando la aplicación usa cierta funcionalidad de dispositivos conectados específicos del usuario.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907177"
---
# <a name="class-mcduserdatafeedsyncscope"></a>Clase `MCDUserDataFeedSyncScope`

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 Esta interfaz representa los datos de usuario que se sincronizan con la plataforma de dispositivos conectados de back-end cuando la aplicación usa cierta funcionalidad de dispositivos conectados específicos del usuario, como las actividades del usuario. Una instancia se recupera de forma estática desde la clase que administra dicha funcionalidad (por ejemplo, **MCDUserActivityChannel**), y se usa en la construcción de **MCDUserDataFeed**.

## <a name="properties"></a>Propiedades

### <a name="platform"></a>Plataforma
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

El **ConnectedDevicesPlatform** instancia que se ha inicializado para la funcionalidad de dispositivos conectados a esta aplicación.

### <a name="syncscopeflags"></a>syncScopeFlags
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

Establezca cualquier indicador opcional para filtrar las actividades entrantes.

### <a name="notificationtype"></a>notificationType
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

Establecer tipo de cambio de tipo de notificación para recibir para el ámbito de sincronización de la fuente de datos de usuario

```