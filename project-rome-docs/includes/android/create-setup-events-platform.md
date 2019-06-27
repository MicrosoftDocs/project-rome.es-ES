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
### <a name="create-the-platform"></a>Creación de la plataforma

Para empezar, simplemente crea una instancia de la plataforma.

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>Suscripción a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario 

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