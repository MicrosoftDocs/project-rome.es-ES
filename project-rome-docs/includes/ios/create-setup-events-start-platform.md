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
### <a name="create-an-instance-of-the-platform"></a>Creación de una instancia de la plataforma

Para empezar, simplemente crea una instancia de la plataforma.

`MCDConnectedDevicesPlatform* platform = [MCDConnectedDevicesPlatform new];`

### <a name="subscribe-to-mcdconnecteddevicesaccountmanager"></a>Suscripción a MCDConnectedDevicesAccountManager

La plataforma requiere un usuario autenticado para acceder a la plataforma.  Deberás suscribirte a eventos **MCDConnectedDevicesAccountManager** para garantizar que se usa una cuenta válida.

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

### <a name="subscribe-to-mcdconnecteddevicesnotificationregistrationmanager"></a>Suscripción a MCDConnectedDevicesNotificationRegistrationManager

De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.  Por lo tanto, debes suscribirte a los eventos **MCDConnectedDevicesNotificationRegistrationManager** para garantizar que los estados de registro en la nube son válidos para la cuenta utilizada.  Comprueba el estado con **MCDConnectedDevicesNotificationRegistrationState**.

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.notificationRegistrationManager.notificationRegistrationStateChanged
     subscribe:^(MCDConnectedDevicesNotificationRegistrationManager* manager __unused,
                 MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs* args __unused) {

                     // Check state using MCDConnectedDevicesNotificationRegistrationState enum

                 }

```

### <a name="start-the-platform"></a>Inicio de la plataforma
Ahora que la plataforma se ha inicializado y ya dispones de los controladores de evento, puedes comenzar a detectar los dispositivos del sistema remoto.  

`[MCDConnectedDevicesPlatform* platform start];`

### <a name="retrieve-user-accounts-known-to-the-app"></a>Recuperación de cuentas de usuario conocidas por la aplicación

Es importante asegurarse de que la lista de cuentas de usuario conocidas por la aplicación se sincronizan correctamente con la clase **MCDConnectedDevicesAccountManager**.

Usa **MCDConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.

```ObjectiveC
[MCDConnectedDevicesPlatform* platform.accountManager
     addAccountAsync:self.mcdAccount
     callback:^(MCDConnectedDevicesAddAccountResult* _Nonnull result, NSError* _Nullable error) {

     // Check state using **MCDConnectedDevicesAccountAddedStatus** enum

     }
```

Para quitar una cuenta no válida, puedes usar **MCDConnectedDevicesAccountManager.removeAccountAsync**.

```ObjectiveC
 [MCDConnectedDevicesPlatform* platform.accountManager
     removeAccountAsync:existingAccount
     callback:^(MCDConnectedDevicesRemoveAccountResult* _Nonnull result __unused, NSError* _Nullable error) {

                    // Remove invalid user account

     }
```