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
### <a name="create-the-platform"></a>Creación de la plataforma


Para empezar, simplemente crea una instancia de la plataforma.

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

### <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>Suscripción a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario 

La plataforma requiere un usuario autenticado para acceder a la plataforma.  Deberás suscribirte a eventos **ConnectedDevicesAccountManager** para garantizar que se usa una cuenta válida. 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>Suscripción a eventos ConnectedDevicesNotificationRegistrationManager

De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.  Por lo tanto, debes suscribirte a los eventos **ConnectedDevicesNotificationRegistrationManager** para garantizar que los estados de registro en la nube son válidos para la cuenta utilizada.  Comprueba el estado con **ConnectedDevicesNotificationRegistrationState**.

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
     // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```
### <a name="start-the-platform"></a>Inicio de la plataforma
Ahora que la plataforma se ha inicializado y ya dispones de los controladores de evento, puedes comenzar a detectar los dispositivos del sistema remoto.  

`ConnectedDevicesPlatform sPlatform.start();`

### <a name="retrieve-user-accounts-known-to-the-app"></a>Recuperación de cuentas de usuario conocidas por la aplicación

Es importante asegurarse de que la lista de cuentas de usuario conocidas por la aplicación se sincronizan correctamente con la clase **ConnectedDevicesAccountManager**.

Usa **ConnectedDevicesAccountManager.addAccountAsync** para agregar una nueva cuenta de usuario.

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> addAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().addAccountAsync(account);
    }
```

Para quitar una cuenta no válida, puedes usar **ConnectedDevicesAccountManager.removeAccountAsync**.

```Java
 public synchronized AsyncOperation<ConnectedDevicesAddAccountResult> removeAccountToAccountManagerAsync(ConnectedDevicesAccount account) {
        return ConnectedDevicesPlatform sPlatform.getAccountManager().removeAccountAsync(account);
    }
```