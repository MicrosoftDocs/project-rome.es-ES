---
title: UserNotificationReaderOptions
description: Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.
keywords: Microsoft, windows, las notificaciones de Graph, Windows procedimientos
ms.openlocfilehash: dda9187dccd013f719d564f62b51fd9ac7be8444
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801387"
---
# <a name="class-usernotificationreaderoptions"></a><span data-ttu-id="9aa09-104">Clase `UserNotificationReaderOptions`</span><span class="sxs-lookup"><span data-stu-id="9aa09-104">class `UserNotificationReaderOptions`</span></span>

```C#
public sealed class UserNotificationReaderOptions : IUserNotificationReaderOptions
```

<span data-ttu-id="9aa09-105">Esta clase permite que la aplicación proporcionar opciones en el lector de notificación, como recibir solo notificaciones de usuario nuevas y actualizaciones de notificación no existente.</span><span class="sxs-lookup"><span data-stu-id="9aa09-105">This class allows the app to provide options on the notification reader, such as only receiving new user notifications and not existing notification updates.</span></span> 

## <a name="constructors"></a><span data-ttu-id="9aa09-106">Constructores</span><span class="sxs-lookup"><span data-stu-id="9aa09-106">Constructors</span></span>

### <a name="usernotificationreaderoptions"></a><span data-ttu-id="9aa09-107">UserNotificationReaderOptions</span><span class="sxs-lookup"><span data-stu-id="9aa09-107">UserNotificationReaderOptions</span></span>
<span data-ttu-id="9aa09-108">Crea e inicializa una nueva instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9aa09-108">Creates and initializes a new instance of UserNotificationReaderOptions.</span></span>

```C#
public UserNotificationReaderOptions()
```

### <a name="usernotificationreaderoptionsusernotificationreaderstartposition-usernotificationstatusfilter-usernotificationreadstatefilter-usernotificationuseractionstatefilter"></a><span data-ttu-id="9aa09-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span><span class="sxs-lookup"><span data-stu-id="9aa09-109">UserNotificationReaderOptions(UserNotificationReaderStartPosition, UserNotificationStatusFilter, UserNotificationReadStateFilter, UserNotificationUserActionStateFilter)</span></span>
<span data-ttu-id="9aa09-110">Crea e inicializa una nueva instancia de UserNotificationReaderOptions con filtros y la posición de inicio especificada.</span><span class="sxs-lookup"><span data-stu-id="9aa09-110">Creates and initializes a new instance of UserNotificationReaderOptions with filters and start position specified.</span></span> 

```C#
public UserNotificationReaderOptions(UserNotificationReaderStartPosition startPosition, UserNotificationStatusFilter statusFilter, UserNotificationReadStateFilter readStateFilter, UserNotificationUserActionStateFilter userActionStateFilter)
```

## <a name="properties"></a><span data-ttu-id="9aa09-111">Propiedades</span><span class="sxs-lookup"><span data-stu-id="9aa09-111">Properties</span></span>

|<span data-ttu-id="9aa09-112">Name</span><span class="sxs-lookup"><span data-stu-id="9aa09-112">Name</span></span> | <span data-ttu-id="9aa09-113">Descripción</span><span class="sxs-lookup"><span data-stu-id="9aa09-113">Description</span></span> |
|:-- |:-- |
|<span data-ttu-id="9aa09-114">StartPosition</span><span class="sxs-lookup"><span data-stu-id="9aa09-114">StartPosition</span></span> |<span data-ttu-id="9aa09-115">Obtiene o establece la posición inicial de esta instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9aa09-115">Get or set the start position for this instance of UserNotificationReaderOptions.</span></span>|
|   <span data-ttu-id="9aa09-116">StatusFilter</span><span class="sxs-lookup"><span data-stu-id="9aa09-116">StatusFilter</span></span> |<span data-ttu-id="9aa09-117">Obtiene o establece el filtro de estado para este lector de notificación de usuario que desee crear.</span><span class="sxs-lookup"><span data-stu-id="9aa09-117">Get or set the status filter for this user notification reader you desire to create.</span></span>| 
|   <span data-ttu-id="9aa09-118">ReadStateFilter</span><span class="sxs-lookup"><span data-stu-id="9aa09-118">ReadStateFilter</span></span> |<span data-ttu-id="9aa09-119">Obtiene o establece el filtro de estado de lectura que se establece para esta instancia de UserNotificationReaderOptions.</span><span class="sxs-lookup"><span data-stu-id="9aa09-119">Get or set the read state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 
|   <span data-ttu-id="9aa09-120">UserActionStateFilter</span><span class="sxs-lookup"><span data-stu-id="9aa09-120">UserActionStateFilter</span></span>|<span data-ttu-id="9aa09-121">El filtro de estado de acción de usuario que se establece para esta instancia de UserNotificationReaderOptions Getor Set.</span><span class="sxs-lookup"><span data-stu-id="9aa09-121">Getor set  the user action state filter that’s set for this instance of UserNotificationReaderOptions.</span></span>| 




