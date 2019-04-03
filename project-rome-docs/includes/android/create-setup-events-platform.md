---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907687"
---
### <a name="create-the-platform"></a><span data-ttu-id="c2f47-103">Creación de la plataforma</span><span class="sxs-lookup"><span data-stu-id="c2f47-103">Create the platform</span></span>

<span data-ttu-id="c2f47-104">Para empezar a crear simplemente una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="c2f47-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="c2f47-105">Suscribirse a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="c2f47-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="c2f47-106">La plataforma requiere que un usuario autenticado tener acceso a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="c2f47-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="c2f47-107">Necesitará suscribirse a **ConnectedDevicesAccountManager** se usa eventos para asegurar una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="c2f47-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenRequested().subscribe((accountManager, args) -> {

    // Get access token
                 
}
```

```Java
 ConnectedDevicesPlatform sPlatform.getAccountManager().accessTokenInvalidated().subscribe((accountManager, args) -> {

    // Refresh and renew existing access token
    
}
```


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="c2f47-108">Suscribirse a eventos ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="c2f47-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="c2f47-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c2f47-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="c2f47-110">Por lo tanto, debe suscribirse a la **ConnectedDevicesNotificationRegistrationManager** eventos para asegurar los Estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="c2f47-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="c2f47-111">Compruebe el uso de estado **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="c2f47-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```