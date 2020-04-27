---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "59805181"
---
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="4f57d-103">Creación de una instancia de la plataforma</span><span class="sxs-lookup"><span data-stu-id="4f57d-103">Create an instance of the platform</span></span>

<span data-ttu-id="4f57d-104">Para empezar, simplemente crea una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="4f57d-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="4f57d-105">Suscripción a MCDConnectedDevicesAccountManager</span><span class="sxs-lookup"><span data-stu-id="4f57d-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="4f57d-106">La plataforma requiere un usuario autenticado para acceder a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="4f57d-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="4f57d-107">Deberás suscribirte a eventos **MCDConnectedDevicesAccountManager** para garantizar que se usa una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="4f57d-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager.accessTokenRequested
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenRequestedEventArgs* _Nonnull request __unused) {

                    // Get access token

                 }
```

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.platform.accountManager.accessTokenInvalidated
     subscribe:^(MCDConnectedDevicesAccountManager* _Nonnull manager __unused,
                 MCDConnectedDevicesAccessTokenInvalidatedEventArgs* _Nonnull request) {

                      // Refresh and renew existing access token

                 }
```

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="4f57d-108">Suscripción a MCDConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="4f57d-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="4f57d-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="4f57d-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="4f57d-110">Por lo tanto, debes suscribirte a los eventos **MCDConnectedDevicesNotificationRegistrationManager** para garantizar que los estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="4f57d-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="4f57d-111">Comprueba el estado con **MCDConnectedDevicesNotificationRegistrationState**.</span><span class="sxs-lookup"><span data-stu-id="4f57d-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="4f57d-112">Inicio de la plataforma</span><span class="sxs-lookup"><span data-stu-id="4f57d-112">Start the platform</span></span>
<span data-ttu-id="4f57d-113">Ahora que la plataforma se ha inicializado y ya dispones de los controladores de evento, puedes comenzar a detectar los dispositivos del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="4f57d-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="4f57d-114">Recuperación de cuentas de usuario conocidas por la aplicación</span><span class="sxs-lookup"><span data-stu-id="4f57d-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="4f57d-115">Es importante asegurarse de que la lista de cuentas de usuario conocidas por la aplicación se sincronizan correctamente con la clase **MCDConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="4f57d-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="4f57d-116">Usa **MCDConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="4f57d-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="4f57d-117">Para quitar una cuenta no válida, puedes usar **MCDConnectedDevicesAccountManager.removeAccountAsync**.</span><span class="sxs-lookup"><span data-stu-id="4f57d-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```