---
title: MCDUserDataFeedNotificationTypes
description: Esta clase es responsable de proporcionar los tipos de notificación
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 49f13fd2dbb13c439993f79a2b7275d4a705826a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908917"
---
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="a1a83-104">Clase `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="a1a83-104">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="a1a83-105">Esta clase proporciona los tipos de notificación válidas para MCDUserDataFeedSyncScope.notificationType.</span><span class="sxs-lookup"><span data-stu-id="a1a83-105">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="a1a83-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a1a83-106">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="a1a83-107">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="a1a83-107">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="a1a83-108">Representa las notificaciones push entrante.</span><span class="sxs-lookup"><span data-stu-id="a1a83-108">Represents the incoming push notifications.</span></span>  <span data-ttu-id="a1a83-109">No hay ningún rescrictions para enviar notificaciones push que no sea de restricciones de dominio o servidor.</span><span class="sxs-lookup"><span data-stu-id="a1a83-109">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="a1a83-110">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="a1a83-110">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="a1a83-111">Disminuir el nivel de todas las notificaciones de inserción a una notificación solo indica al sistema para sincronizar para recibir los datos, incluso si los datos podrían incluirse en la notificación de inserción.</span><span class="sxs-lookup"><span data-stu-id="a1a83-111">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="a1a83-112">noNotification</span><span class="sxs-lookup"><span data-stu-id="a1a83-112">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="a1a83-113">Impedir que las notificaciones para los nuevos datos de usuario, sólo recibirá datos nuevos cuando se llama a UserDataFeed.startSync, o al interactuar con el servidor de otras maneras</span><span class="sxs-lookup"><span data-stu-id="a1a83-113">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>
