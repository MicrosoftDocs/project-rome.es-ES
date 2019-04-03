---
title: MCDUserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.
keywords: Microsoft, windows, las notificaciones de Graph, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: d5ea9072af0f35f614557192ef782754c4054b22
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907987"
---
# <a name="class-mcdusernotificationreaderoptions"></a><span data-ttu-id="5e8f3-104">Clase `MCDUserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="5e8f3-104">class `MCDUserNotificationReaderOptions`</span></span>

```
@interface MCDUserNotificationReaderOptions : NSObject
```

<span data-ttu-id="5e8f3-105">Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.</span><span class="sxs-lookup"><span data-stu-id="5e8f3-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="properties"></a><span data-ttu-id="5e8f3-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="5e8f3-106">Properties</span></span>

### <a name="startposition"></a><span data-ttu-id="5e8f3-107">startPosition</span><span class="sxs-lookup"><span data-stu-id="5e8f3-107">startPosition</span></span>
<span data-ttu-id="5e8f3-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="5e8f3-108">`@property(nonatomic, assign) MCDUserNotificationReaderStartPosition startPosition;` Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>

### <a name="statusfilter"></a><span data-ttu-id="5e8f3-109">statusFilter</span><span class="sxs-lookup"><span data-stu-id="5e8f3-109">statusFilter</span></span>
<span data-ttu-id="5e8f3-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Obtiene o establece el filtro de estado para este lector de notificación de usuario que desee crear.</span><span class="sxs-lookup"><span data-stu-id="5e8f3-110">`@property(nonatomic, assign) MCDUserNotificationStatusFilter statusFilter;` Get or set the status filter for this user notification reader you desire to create.</span></span>

### <a name="readstatefilter"></a><span data-ttu-id="5e8f3-111">readStateFilter</span><span class="sxs-lookup"><span data-stu-id="5e8f3-111">readStateFilter</span></span>
<span data-ttu-id="5e8f3-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="5e8f3-112">`@property(nonatomic, assign) MCDUserNotificationReadStateFilter readStateFilter;` Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions</span></span>

### <a name="useractionstatefilter"></a><span data-ttu-id="5e8f3-113">userActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="5e8f3-113">userActionStateFilter</span></span>
<span data-ttu-id="5e8f3-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` El filtro de estado de acción de usuario que se establece para esta instancia de UserNotificationReaderOptions Getor Set.</span><span class="sxs-lookup"><span data-stu-id="5e8f3-114">`@property(nonatomic, assign) MCDUserNotificationUserActionStateFilter userActionStateFilter;` Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>

## <a name="constructors"></a><span data-ttu-id="5e8f3-115">Constructores</span><span class="sxs-lookup"><span data-stu-id="5e8f3-115">Constructors</span></span>

### <a name="options"></a><span data-ttu-id="5e8f3-116">opciones</span><span class="sxs-lookup"><span data-stu-id="5e8f3-116">options</span></span>
<span data-ttu-id="5e8f3-117">`+ (nullable instancetype)options;` Crea e inicializa una nueva instancia de las opciones de notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="5e8f3-117">`+ (nullable instancetype)options;` Creates and initializes a new instance of options for User Notifications.</span></span>