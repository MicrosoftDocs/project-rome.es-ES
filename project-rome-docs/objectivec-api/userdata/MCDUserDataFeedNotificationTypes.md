---
title: MCDUserDataFeedNotificationTypes
description: Esta clase es responsable de proporcionar los tipos de notificación
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801149"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>Clase `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

Esta clase proporciona los tipos de notificación válidas para MCDUserDataFeedSyncScope.notificationType.


## <a name="properties"></a>Propiedades

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

Representa las notificaciones push entrante.  No hay ningún rescrictions para enviar notificaciones push que no sea de restricciones de dominio o servidor.

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

Disminuir el nivel de todas las notificaciones de inserción a una notificación solo indica al sistema para sincronizar para recibir los datos, incluso si los datos podrían incluirse en la notificación de inserción.


### <a name="nonotification"></a>noNotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

Impedir que las notificaciones para los nuevos datos de usuario, sólo recibirá datos nuevos cuando se llama a UserDataFeed.startSync, o al interactuar con el servidor de otras maneras
