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
# <a name="class-mcduserdatafeednotificationtypes"></a><span data-ttu-id="bd889-105">las `MCDUserDataFeedNotificationTypes`</span><span class="sxs-lookup"><span data-stu-id="bd889-105">class `MCDUserDataFeedNotificationTypes`</span></span>

```
@interface MCDUserDataFeedNotificationTypes : NSObject
```

<span data-ttu-id="bd889-106">Esta clase proporciona los tipos de notificación válidos para MCDUserDataFeedSyncScope. notificationType.</span><span class="sxs-lookup"><span data-stu-id="bd889-106">This class provides the valid notification types for MCDUserDataFeedSyncScope.notificationType.</span></span>


## <a name="properties"></a><span data-ttu-id="bd889-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="bd889-107">Properties</span></span>

### <a name="notificationwithpayload"></a><span data-ttu-id="bd889-108">notificationWithPayload</span><span class="sxs-lookup"><span data-stu-id="bd889-108">notificationWithPayload</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationWithPayload;`

<span data-ttu-id="bd889-109">Representa las notificaciones de envío entrantes.</span><span class="sxs-lookup"><span data-stu-id="bd889-109">Represents the incoming push notifications.</span></span>  <span data-ttu-id="bd889-110">No hay ninguna rescrictions para las notificaciones de envío que no sean restricciones de dominio o servidor.</span><span class="sxs-lookup"><span data-stu-id="bd889-110">There are no rescrictions to push notifications other than domain/server restrictions.</span></span>

### <a name="notificationonly"></a><span data-ttu-id="bd889-111">notificationOnly</span><span class="sxs-lookup"><span data-stu-id="bd889-111">notificationOnly</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* notificationOnly;`

<span data-ttu-id="bd889-112">Disminuir de nivel todas las notificaciones de envío a una notificación que solo indique al sistema que se sincronice para recibir los datos, incluso si los datos se pueden incluir en la notificación de extracción.</span><span class="sxs-lookup"><span data-stu-id="bd889-112">Demote all push notifications to a notification only telling the system to sync to receive the data, even if the data could be contained in the push notification.</span></span>


### <a name="nonotification"></a><span data-ttu-id="bd889-113">nonotification</span><span class="sxs-lookup"><span data-stu-id="bd889-113">noNotification</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* noNotification;`

<span data-ttu-id="bd889-114">Impedir las notificaciones para los nuevos datos de usuario, recibir solo datos nuevos cuando se llama a UserDataFeed. startSync o al interactuar con el servidor de otras maneras</span><span class="sxs-lookup"><span data-stu-id="bd889-114">Prevent any notifications for new user data, only receive new data when UserDataFeed.startSync is called, or when interacting with the server in other ways</span></span>
