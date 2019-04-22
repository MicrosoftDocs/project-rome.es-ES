---
title: MCDUserNotificationStatusFilter
description: Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación. Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801497"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="a9def-105">Enum `MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="a9def-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="a9def-106">Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación.</span><span class="sxs-lookup"><span data-stu-id="a9def-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="a9def-107">Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos.</span><span class="sxs-lookup"><span data-stu-id="a9def-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="a9def-108">Nombre</span><span class="sxs-lookup"><span data-stu-id="a9def-108">Name</span></span> | <span data-ttu-id="a9def-109">Valor</span><span class="sxs-lookup"><span data-stu-id="a9def-109">Value</span></span> | <span data-ttu-id="a9def-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="a9def-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="a9def-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="a9def-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="a9def-112">0</span><span class="sxs-lookup"><span data-stu-id="a9def-112">0</span></span>| <span data-ttu-id="a9def-113">Incluir todas las notificaciones, independientemente del valor de estado.</span><span class="sxs-lookup"><span data-stu-id="a9def-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="a9def-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="a9def-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="a9def-115">1</span><span class="sxs-lookup"><span data-stu-id="a9def-115">1</span></span>| <span data-ttu-id="a9def-116">Incluyen las notificaciones que están activas y persisten en el almacén de notificación de plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="a9def-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="a9def-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="a9def-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="a9def-118">2</span><span class="sxs-lookup"><span data-stu-id="a9def-118">2</span></span>| <span data-ttu-id="a9def-119">Incluir solo las notificaciones eliminadas.</span><span class="sxs-lookup"><span data-stu-id="a9def-119">Include deleted notifications only.</span></span>|