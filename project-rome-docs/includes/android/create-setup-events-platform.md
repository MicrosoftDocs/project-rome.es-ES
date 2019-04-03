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
### <a name="create-the-platform"></a>Creación de la plataforma

Para empezar a crear simplemente una instancia de la plataforma.

`ConnectedDevicesPlatform sPlatform = new ConnectedDevicesPlatform(context);`

## <a name="subscribe-to-connecteddevicesaccountmanager-events-to-handle-the-user-account"></a>Suscribirse a eventos ConnectedDevicesAccountManager para controlar la cuenta de usuario 

La plataforma requiere que un usuario autenticado tener acceso a la plataforma.  Necesitará suscribirse a **ConnectedDevicesAccountManager** se usa eventos para asegurar una cuenta válida. 

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


### <a name="subscribe-to-connecteddevicesnotificationregistrationmanager-events"></a>Suscribirse a eventos ConnectedDevicesNotificationRegistrationManager

De forma similar, la plataforma utiliza notificaciones para entregar comandos entre dispositivos.  Por lo tanto, debe suscribirse a la **ConnectedDevicesNotificationRegistrationManager** eventos para asegurar los Estados de registro en la nube son válidos para la cuenta utilizada.  Compruebe el uso de estado **ConnectedDevicesNotificationRegistrationState**

```Java
ConnectedDevicesPlatform sPlatform.getNotificationRegistrationManager().notificationRegistrationStateChanged().subscribe((notificationRegistrationManager, args) -> {
    
    // Check state using ConnectedDevicesNotificationRegistrationState enum

}
```