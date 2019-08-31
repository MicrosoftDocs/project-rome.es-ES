---
title: MCDUserNotificationStatus
description: Contiene valores que determinan si la notificación se ha eliminado o no. Las notificaciones eliminadas seguirán estando en el almacén de notificaciones y las devolverá el lector antes de que se produzca la limpieza de la plataforma. Se puede aplicar un filtro de lector correspondiente UserNotificationStatusFilter para evitar que estas notificaciones se muestren en el lector de notificaciones.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 2d2ce28b08442c51ecdb4652ba33cb96f091b8ce
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800817"
---
# <a name="enum-mcdusernotificationstatus"></a><span data-ttu-id="59b05-106">enumeración`MCDUserNotificationStatus`</span><span class="sxs-lookup"><span data-stu-id="59b05-106">enum `MCDUserNotificationStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatus)
```

<span data-ttu-id="59b05-107">Contiene valores que determinan si la notificación se ha eliminado o no.</span><span class="sxs-lookup"><span data-stu-id="59b05-107">Contains values that determines whether the notification is deleted or not.</span></span> <span data-ttu-id="59b05-108">Las notificaciones eliminadas seguirán estando en el almacén de notificaciones y las devolverá el lector antes de que se produzca la limpieza de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="59b05-108">Deleted notifications will still be in the notification store and be returned by the reader before the platform cleanup happens.</span></span> <span data-ttu-id="59b05-109">Se puede aplicar un filtro de lector correspondiente UserNotificationStatusFilter para evitar que estas notificaciones se muestren en el lector de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="59b05-109">A corresponding reader filter UserNotificationStatusFilter can be applied to prevent these notifications from showing up in notification reader.</span></span> 

|<span data-ttu-id="59b05-110">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="59b05-110">Name</span></span> | <span data-ttu-id="59b05-111">Valor</span><span class="sxs-lookup"><span data-stu-id="59b05-111">Value</span></span> | <span data-ttu-id="59b05-112">Descripción</span><span class="sxs-lookup"><span data-stu-id="59b05-112">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="59b05-113">MCDUserNotificationStatusActive</span><span class="sxs-lookup"><span data-stu-id="59b05-113">MCDUserNotificationStatusActive</span></span> |<span data-ttu-id="59b05-114">0</span><span class="sxs-lookup"><span data-stu-id="59b05-114">0</span></span>| <span data-ttu-id="59b05-115">La notificación todavía está activa y se conserva dentro del almacén de plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="59b05-115">The notification is still active and persisted inside Connected Devices Platform store.</span></span> |
|   <span data-ttu-id="59b05-116">MCDUserNotificationStatusDeleted</span><span class="sxs-lookup"><span data-stu-id="59b05-116">MCDUserNotificationStatusDeleted</span></span> | <span data-ttu-id="59b05-117">1</span><span class="sxs-lookup"><span data-stu-id="59b05-117">1</span></span>| <span data-ttu-id="59b05-118">La notificación se ha eliminado.</span><span class="sxs-lookup"><span data-stu-id="59b05-118">The notification has been deleted.</span></span>|