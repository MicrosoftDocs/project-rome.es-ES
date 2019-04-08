---
title: MCDUserNotificationStatusFilter
description: Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación. Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909147"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="69c22-105">Enum `MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="69c22-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="69c22-106">Contiene valores que indica un filtro de estado de lectura al crear un lector de notificación.</span><span class="sxs-lookup"><span data-stu-id="69c22-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="69c22-107">Esto determina si desea recibir todas las notificaciones, la aplicación de solo lectura, o solo los no leídos.</span><span class="sxs-lookup"><span data-stu-id="69c22-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="69c22-108">Nombre</span><span class="sxs-lookup"><span data-stu-id="69c22-108">Name</span></span> | <span data-ttu-id="69c22-109">Valor</span><span class="sxs-lookup"><span data-stu-id="69c22-109">Value</span></span> | <span data-ttu-id="69c22-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="69c22-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="69c22-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="69c22-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="69c22-112">0</span><span class="sxs-lookup"><span data-stu-id="69c22-112">0</span></span>| <span data-ttu-id="69c22-113">Incluir todas las notificaciones, independientemente del valor de estado.</span><span class="sxs-lookup"><span data-stu-id="69c22-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="69c22-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="69c22-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="69c22-115">1</span><span class="sxs-lookup"><span data-stu-id="69c22-115">1</span></span>| <span data-ttu-id="69c22-116">Incluyen las notificaciones que están activas y persisten en el almacén de notificación de plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="69c22-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="69c22-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="69c22-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="69c22-118">2</span><span class="sxs-lookup"><span data-stu-id="69c22-118">2</span></span>| <span data-ttu-id="69c22-119">Incluir solo las notificaciones eliminadas.</span><span class="sxs-lookup"><span data-stu-id="69c22-119">Include deleted notifications only.</span></span>|