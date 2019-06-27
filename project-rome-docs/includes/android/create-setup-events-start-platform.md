---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 0ac6a543cc63be9154e40482e587a8f373f56798
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755791"
---
### <a name="create-the-platform"></a><span data-ttu-id="858b3-103">Creación de la plataforma</span><span class="sxs-lookup"><span data-stu-id="858b3-103">Create the platform</span></span>


<span data-ttu-id="858b3-104">Para empezar, simplemente crea una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="858b3-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="858b3-105">Suscripción a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="858b3-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="858b3-106">La plataforma requiere un usuario autenticado para acceder a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="858b3-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="858b3-107">Deberás suscribirte a eventos **ConnectedDevicesAccountManager** para garantizar que se usa una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="858b3-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="858b3-108">Suscripción a eventos ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="858b3-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="858b3-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="858b3-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="858b3-110">Por lo tanto, debes suscribirte a los eventos **ConnectedDevicesNotificationRegistrationManager** para garantizar que los estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="858b3-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="858b3-111">Comprueba el estado con **ConnectedDevicesNotificationRegistrationState**.</span><span class="sxs-lookup"><span data-stu-id="858b3-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="858b3-112">Inicio de la plataforma</span><span class="sxs-lookup"><span data-stu-id="858b3-112">Start the platform</span></span>
<span data-ttu-id="858b3-113">Ahora que la plataforma se ha inicializado y ya dispones de los controladores de evento, puedes comenzar a detectar los dispositivos del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="858b3-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="858b3-114">Recuperación de cuentas de usuario conocidas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="858b3-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="858b3-115">Es importante asegurarse de que la lista de cuentas de usuario conocidas por la aplicación se sincronizan correctamente con la clase **ConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="858b3-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="858b3-116">Usa **ConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="858b3-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="858b3-117">Para quitar una cuenta no válida, puedes usar **ConnectedDevicesAccountManager.removeAccountAsync**.</span><span class="sxs-lookup"><span data-stu-id="858b3-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```