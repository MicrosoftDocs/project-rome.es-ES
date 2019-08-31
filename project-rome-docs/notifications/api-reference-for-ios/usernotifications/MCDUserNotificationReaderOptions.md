---
title: MCDUserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes.
keywords: Microsoft, Windows, notificaciones de grafos, iOS y procedimientos de iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58907987"
---
# <a name="class-mcdusernotificationreaderoptions"></a><span data-ttu-id="a04a3-104">las`MCDUserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="a04a3-104">class `MCDUserNotificationReaderOptions`</span></span>

```
@interface MCDUserNotificationReaderOptions : NSObject
```

<span data-ttu-id="a04a3-105">Esta clase permite que la aplicación proporcione opciones en el lector de notificaciones, como recibir solo notificaciones de usuario nuevas y no actualizaciones de notificación existentes.</span><span class="sxs-lookup"><span data-stu-id="a04a3-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="properties"></a><span data-ttu-id="a04a3-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a04a3-106">Properties</span></span>

### <a name="startposition"></a><span data-ttu-id="a04a3-107">startPosition</span><span class="sxs-lookup"><span data-stu-id="a04a3-107">startPosition</span></span>
<span data-ttu-id="a04a3-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;`Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a04a3-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>

### <a name="statusfilter"></a><span data-ttu-id="a04a3-109">statusFilter</span><span class="sxs-lookup"><span data-stu-id="a04a3-109">statusFilter</span></span>
<span data-ttu-id="a04a3-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;`Obtenga o establezca el filtro de estado para este lector de notificaciones de usuario que desea crear.</span><span class="sxs-lookup"><span data-stu-id="a04a3-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Get or set the status filter for this user notification reader you desire to create.</span></span>

### <a name="readstatefilter"></a><span data-ttu-id="a04a3-111">readStateFilter</span><span class="sxs-lookup"><span data-stu-id="a04a3-111">readStateFilter</span></span>
<span data-ttu-id="a04a3-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;`Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="a04a3-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions</span></span>

### <a name="useractionstatefilter"></a><span data-ttu-id="a04a3-113">userActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="a04a3-113">userActionStateFilter</span></span>
<span data-ttu-id="a04a3-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;`Getor establezca el filtro de estado de acción del usuario que se establece para esta instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="a04a3-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>

## <a name="constructors"></a><span data-ttu-id="a04a3-115">Constructores</span><span class="sxs-lookup"><span data-stu-id="a04a3-115">Constructors</span></span>

### <a name="options"></a><span data-ttu-id="a04a3-116">opciones</span><span class="sxs-lookup"><span data-stu-id="a04a3-116">options</span></span>
<span data-ttu-id="a04a3-117">`+ (nullable instancetype)options;`Crea e inicializa una nueva instancia de opciones para las notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="a04a3-117">`+ (nullable instancetype)options;` Creates and initializes a new instance of options for User Notifications.</span></span>