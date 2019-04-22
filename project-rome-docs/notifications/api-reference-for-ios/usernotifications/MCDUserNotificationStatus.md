---
title: MCDUserNotificationStatus
description: Contiene valores que determina si la notificación se ha eliminado o no. Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma. Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800817"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="8dafc-106">Enum `MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="8dafc-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="8dafc-107">Contiene valores que determina si la notificación se ha eliminado o no.</span><span class="sxs-lookup"><span data-stu-id="8dafc-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="8dafc-108">Notificaciones eliminadas seguirán estando en el almacén de notificación y se devuelve el lector antes de que se produce la limpieza de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="8dafc-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="8dafc-109">Un filtro de lector UserNotificationStatusFilter correspondientes puede aplicarse a impedir que estas notificaciones aparecen en el lector de notificación.</span><span class="sxs-lookup"><span data-stu-id="8dafc-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="8dafc-110">Nombre</span><span class="sxs-lookup"><span data-stu-id="8dafc-110">Name</span></span> | <span data-ttu-id="8dafc-111">Valor</span><span class="sxs-lookup"><span data-stu-id="8dafc-111">Value</span></span> | <span data-ttu-id="8dafc-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="8dafc-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="8dafc-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="8dafc-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="8dafc-114">0</span><span class="sxs-lookup"><span data-stu-id="8dafc-114">0</span></span>| <span data-ttu-id="8dafc-115">La notificación es sigue activo y persistente dentro de la tienda de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="8dafc-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="8dafc-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="8dafc-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="8dafc-117">1</span><span class="sxs-lookup"><span data-stu-id="8dafc-117">1</span></span>| <span data-ttu-id="8dafc-118">Se ha eliminado la notificación.</span><span class="sxs-lookup"><span data-stu-id="8dafc-118">The notification has been deleted.</span></span>|