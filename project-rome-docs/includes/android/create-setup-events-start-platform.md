---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d498d192b6ac909e8b3978b54e6996eef98d2814
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907507"
---
### <a name="create-the-platform"></a><span data-ttu-id="7fea9-103">Creación de la plataforma</span><span class="sxs-lookup"><span data-stu-id="7fea9-103">Create the platform</span></span>


<span data-ttu-id="7fea9-104">Para empezar a crear simplemente una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="7fea9-104">To get started simply instantiate the platform.</span></span>

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a><span data-ttu-id="7fea9-105">Suscribirse a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="7fea9-105">Subscribe to ConnectedDevicesAccountManager events to handle the user account</span></span> 

<span data-ttu-id="7fea9-106">La plataforma requiere que un usuario autenticado tener acceso a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="7fea9-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="7fea9-107">Necesitará suscribirse a **ConnectedDevicesAccountManager** se usa eventos para asegurar una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="7fea9-107">You'll need to subscribe to **ConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span> 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a><span data-ttu-id="7fea9-108">Suscribirse a eventos ConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="7fea9-108">Subscribe to ConnectedDevicesNotificationRegistrationManager events</span></span>

<span data-ttu-id="7fea9-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="7fea9-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="7fea9-110">Por lo tanto, debe suscribirse a la **ConnectedDevicesNotificationRegistrationManager** eventos para asegurar los Estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="7fea9-110">Therefore, you must subscribe to the **ConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="7fea9-111">Compruebe el uso de estado **ConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="7fea9-111">Verify the the state using **ConnectedDevicesNotificationRegistrationState**</span></span>

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a><span data-ttu-id="7fea9-112">Iniciar la plataforma</span><span class="sxs-lookup"><span data-stu-id="7fea9-112">Start the platform</span></span>
<span data-ttu-id="7fea9-113">Ahora que se inicializa la plataforma y los controladores de eventos están en su lugar, está listo para comenzar a detectar los dispositivos del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="7fea9-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="7fea9-114">Recuperar las cuentas de usuario que se sabe que la aplicación</span><span class="sxs-lookup"><span data-stu-id="7fea9-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="7fea9-115">Es importante asegurarse de que la lista de cuentas de usuario que se sabe que la aplicación se ha sincronizado correctamente con el **ConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="7fea9-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **ConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="7fea9-116">Use **ConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="7fea9-116">Use **ConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

<span data-ttu-id="7fea9-117">Para quitar una cuenta no válida, puede usar **ConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="7fea9-117">To remove an invalid account you can use **ConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```