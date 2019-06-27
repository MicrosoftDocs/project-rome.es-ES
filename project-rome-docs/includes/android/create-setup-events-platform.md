---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 559752038bb8d73c95d853dcc39be061e64b322f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800297"
---
### <a name="create-the-platform"></a><span data-ttu-id="22a31-103">Creación de la plataforma</span><span class="sxs-lookup"><span data-stu-id="22a31-103">Create the platform</span></span>

<span data-ttu-id="22a31-104">Para empezar, simplemente crea una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="22a31-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="22a31-105">Suscripción a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="22a31-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="22a31-106">La plataforma requiere un usuario autenticado para acceder a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="22a31-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="22a31-107">Deberás suscribirte a eventos **ConnectedDevicesAccountManager** para garantizar que se usa una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="22a31-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="22a31-108">Suscripción a eventos ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="22a31-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="22a31-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="22a31-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="22a31-110">Por lo tanto, debes suscribirte a los eventos **ConnectedDevicesNotificationRegistrationManager** para garantizar que los estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="22a31-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="22a31-111">Comprueba el estado con **ConnectedDevicesNotificationRegistrationState**.</span><span class="sxs-lookup"><span data-stu-id="22a31-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```