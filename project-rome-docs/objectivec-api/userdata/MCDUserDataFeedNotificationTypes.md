---
title: MCDUserDataFeedNotificationTypes
description: Obtenga información sobre la clase MCDUserDataFeedNotificationTypes. Esta clase es responsable de proporcionar los tipos de notificación.
keywords: Microsoft, Windows, actividades de usuario, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a9bb9b41309e32a429926c52769da9bc767ef5bc
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760989"
---
# <a name="class-mcduserdatafeednotificationtypes"></a>las `MCDUserDataFeedNotificationTypes`

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

Esta clase proporciona los tipos de notificación válidos para MCDUserDataFeedSyncScope. notificationType.


## <a name="properties"></a>Propiedades

### <a name="notificationwithpayload"></a>notificationWithPayload
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

Representa las notificaciones de envío entrantes.  No hay ninguna rescrictions para las notificaciones de envío que no sean restricciones de dominio o servidor.

### <a name="notificationonly"></a>notificationOnly
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

Disminuir de nivel todas las notificaciones de envío a una notificación que solo indique al sistema que se sincronice para recibir los datos, incluso si los datos se pueden incluir en la notificación de extracción.


### <a name="nonotification"></a>nonotification
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

Impedir las notificaciones para los nuevos datos de usuario, recibir solo datos nuevos cuando se llama a UserDataFeed. startSync o al interactuar con el servidor de otras maneras
