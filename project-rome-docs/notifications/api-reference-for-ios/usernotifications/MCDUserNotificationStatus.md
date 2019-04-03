---
title: MCDUserNotificationStatus
description: Contiene valores que determina si la notificación se ha eliminado o no. Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma. Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907247"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="b7786-106">Enum `MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="b7786-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="b7786-107">Contiene valores que determina si la notificación se ha eliminado o no.</span><span class="sxs-lookup"><span data-stu-id="b7786-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="b7786-108">Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b7786-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="b7786-109">Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación.</span><span class="sxs-lookup"><span data-stu-id="b7786-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="b7786-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="b7786-110">Name</span></span> | <span data-ttu-id="b7786-111">Valor</span><span class="sxs-lookup"><span data-stu-id="b7786-111">Value</span></span> | <span data-ttu-id="b7786-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="b7786-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="b7786-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="b7786-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="b7786-114">0</span><span class="sxs-lookup"><span data-stu-id="b7786-114">0</span></span>| <span data-ttu-id="b7786-115">La notificación es sigue activo y persistente dentro de la tienda de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="b7786-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="b7786-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="b7786-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="b7786-117">1</span><span class="sxs-lookup"><span data-stu-id="b7786-117">1</span></span>| <span data-ttu-id="b7786-118">Se ha eliminado la notificación.</span><span class="sxs-lookup"><span data-stu-id="b7786-118">The notification has been deleted.</span></span>|