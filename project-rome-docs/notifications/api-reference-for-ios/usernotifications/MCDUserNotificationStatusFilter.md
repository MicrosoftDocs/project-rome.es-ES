---
title: MCDUserNotificationStatusFilter
description: Contiene valores que indican un filtro de estado de lectura al crear un lector de notificaciones. Esto determina si la aplicación desea recibir todas las notificaciones, solo las leídas o solo las no leídas.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: 09e165c98a557b16214d7c1103734d6e17407b6f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801497"
---
# <a name="enum-mcdusernotificationstatusfilter"></a><span data-ttu-id="19e60-105">enumeración`MCDUserNotificationStatusFilter`</span><span class="sxs-lookup"><span data-stu-id="19e60-105">enum `MCDUserNotificationStatusFilter`</span></span>

```
typedef NS_ENUM(NSInteger, MCDUserNotificationStatusFilter)
```

<span data-ttu-id="19e60-106">Contiene valores que indican un filtro de estado de lectura al crear un lector de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="19e60-106">Contains values that indicates a read state filter when creating a notification reader.</span></span> <span data-ttu-id="19e60-107">Esto determina si la aplicación desea recibir todas las notificaciones, solo las leídas o solo las no leídas.</span><span class="sxs-lookup"><span data-stu-id="19e60-107">This determines whether the app wants to receive all notifications, only read ones, or only unread ones.</span></span> 

|<span data-ttu-id="19e60-108">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="19e60-108">Name</span></span> | <span data-ttu-id="19e60-109">Valor</span><span class="sxs-lookup"><span data-stu-id="19e60-109">Value</span></span> | <span data-ttu-id="19e60-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="19e60-110">Description</span></span> |
|:-- |:-- |:-- |
|   <span data-ttu-id="19e60-111">MCDUserNotificationStatusFilterAny</span><span class="sxs-lookup"><span data-stu-id="19e60-111">MCDUserNotificationStatusFilterAny</span></span> | <span data-ttu-id="19e60-112">0</span><span class="sxs-lookup"><span data-stu-id="19e60-112">0</span></span>| <span data-ttu-id="19e60-113">Incluya todas las notificaciones independientemente del valor de estado.</span><span class="sxs-lookup"><span data-stu-id="19e60-113">Include all notifications regardless of status value.</span></span> |
|   <span data-ttu-id="19e60-114">MCDUserNotificationStatusFilterActive</span><span class="sxs-lookup"><span data-stu-id="19e60-114">MCDUserNotificationStatusFilterActive</span></span> |<span data-ttu-id="19e60-115">1</span><span class="sxs-lookup"><span data-stu-id="19e60-115">1</span></span>| <span data-ttu-id="19e60-116">Incluye notificaciones que están activas y guardadas en el almacén de notificaciones de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="19e60-116">Include notifications that are active and persisted in Connected Devices Platform notification store.</span></span> |
|   <span data-ttu-id="19e60-117">MCDUserNotificationStatusFilterDeleted</span><span class="sxs-lookup"><span data-stu-id="19e60-117">MCDUserNotificationStatusFilterDeleted</span></span> | <span data-ttu-id="19e60-118">2</span><span class="sxs-lookup"><span data-stu-id="19e60-118">2</span></span>| <span data-ttu-id="19e60-119">Incluir solo las notificaciones eliminadas.</span><span class="sxs-lookup"><span data-stu-id="19e60-119">Include deleted notifications only.</span></span>|