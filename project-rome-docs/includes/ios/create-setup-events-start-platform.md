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
### <a name="create-an-instance-of-the-platform"></a>Cree una instancia de la plataforma

Para empezar a crear simplemente una instancia de la plataforma.

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a>Suscríbase a MCDConnectedDevicesAccountManager

La plataforma requiere que un usuario autenticado tener acceso a la plataforma.  Necesitará suscribirse a **MCDConnectedDevicesAccountManager** se usa eventos para asegurar una cuenta válida.

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a>Suscríbase a MCDConnectedDevicesNotificationRegistrationManager

De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.  Por lo tanto, debe suscribirse a la **MCDConnectedDevicesNotificationRegistrationManager** eventos para asegurar los Estados de registro en la nube son válidos para la cuenta utilizada.  Compruebe el uso de estado **MCDConnectedDevicesNotificationRegistrationState**

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a>Iniciar la plataforma
Ahora que se inicializa la plataforma y los controladores de eventos están en su lugar, está listo para comenzar a detectar los dispositivos del sistema remoto.  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a>Recuperar las cuentas de usuario que se sabe que la aplicación

Es importante asegurarse de que la lista de cuentas de usuario que se sabe que la aplicación se ha sincronizado correctamente con el **MCDConnectedDevicesAccountManager**.

Use **MCDConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

Para quitar una cuenta no válida, puede usar **MCDConnectedDevicesAccountManager.removeAccountAsync**

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```