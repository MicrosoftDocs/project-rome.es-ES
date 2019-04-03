---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 60a4e282fc5446e38a80e72979e12daad51b2026
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907217"
---
### <a name="create-an-instance-of-the-platform"></a><span data-ttu-id="3de09-103">Cree una instancia de la plataforma</span><span class="sxs-lookup"><span data-stu-id="3de09-103">Create an instance of the platform</span></span>

<span data-ttu-id="3de09-104">Para empezar a crear simplemente una instancia de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="3de09-104">To get started simply instantiate the platform.</span></span>

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="3de09-105">Suscríbase a MCDConnectedDevicesAccountManager</span><span class="sxs-lookup"><span data-stu-id="3de09-105">Subscribe to MCDConnectedDevicesAccountManager</span></span>

<span data-ttu-id="3de09-106">La plataforma requiere que un usuario autenticado tener acceso a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="3de09-106">The platform requires an authenticated user to access the platform.</span></span>  <span data-ttu-id="3de09-107">Necesitará suscribirse a **MCDConnectedDevicesAccountManager** se usa eventos para asegurar una cuenta válida.</span><span class="sxs-lookup"><span data-stu-id="3de09-107">You'll need to subscribe to **MCDConnectedDevicesAccountManager** events to ensure a valid account is being used.</span></span>

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="3de09-108">Suscríbase a MCDConnectedDevicesNotificationRegistrationManager</span><span class="sxs-lookup"><span data-stu-id="3de09-108">Subscribe to MCDConnectedDevicesNotificationRegistrationManager</span></span>

<span data-ttu-id="3de09-109">De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3de09-109">Similarly, the platform uses notifications to deliver commands between devices.</span></span>  <span data-ttu-id="3de09-110">Por lo tanto, debe suscribirse a la **MCDConnectedDevicesNotificationRegistrationManager** eventos para asegurar los Estados de registro en la nube son válidos para la cuenta utilizada.</span><span class="sxs-lookup"><span data-stu-id="3de09-110">Therefore, you must subscribe to the **MCDConnectedDevicesNotificationRegistrationManager** events to ensure the cloud registration states are valid for the account being used.</span></span>  <span data-ttu-id="3de09-111">Compruebe el uso de estado **MCDConnectedDevicesNotificationRegistrationState**</span><span class="sxs-lookup"><span data-stu-id="3de09-111">Verify the the state using **MCDConnectedDevicesNotificationRegistrationState**</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a><span data-ttu-id="3de09-112">Iniciar la plataforma</span><span class="sxs-lookup"><span data-stu-id="3de09-112">Start the platform</span></span>
<span data-ttu-id="3de09-113">Ahora que se inicializa la plataforma y los controladores de eventos están en su lugar, está listo para comenzar a detectar los dispositivos del sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="3de09-113">Now that the platform is initialized and event handlers are in place, you are ready to start discovering remote system devices.</span></span>  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a><span data-ttu-id="3de09-114">Recuperar las cuentas de usuario que se sabe que la aplicación</span><span class="sxs-lookup"><span data-stu-id="3de09-114">Retrieve user accounts known to the app</span></span>

<span data-ttu-id="3de09-115">Es importante asegurarse de que la lista de cuentas de usuario que se sabe que la aplicación se ha sincronizado correctamente con el **MCDConnectedDevicesAccountManager**.</span><span class="sxs-lookup"><span data-stu-id="3de09-115">It is important to ensure that the list of user accounts known to the app are properly synchronized with the **MCDConnectedDevicesAccountManager**.</span></span>

<span data-ttu-id="3de09-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="3de09-116">Use **MCDConnectedDevicesAccountManager.addAccountAsync** to add a new user account.</span></span>

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

<span data-ttu-id="3de09-117">Para quitar una cuenta no válida, puede usar **MCDConnectedDevicesAccountManager.removeAccountAsync**</span><span class="sxs-lookup"><span data-stu-id="3de09-117">To remove an invalid account you can use **MCDConnectedDevicesAccountManager.removeAccountAsync**</span></span>

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```