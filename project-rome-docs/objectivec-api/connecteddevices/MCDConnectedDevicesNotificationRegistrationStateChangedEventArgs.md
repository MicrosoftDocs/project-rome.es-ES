---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908447"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a>Clase `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs` 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration. Esto sirve para asegurarse de que la aplicación obtiene informa acerca de nuevos mensajes de la plataforma de dispositivos conectados a través del mecanismo de notificación correcto.

## <a name="properties"></a>Propiedades

### <a name="account"></a>cuenta
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

La cuenta para el que ha cambiado el estado de registro de notificación para.

### <a name="registration"></a>Registro
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

La información de instancia de registro cuyo estado ha cambiado.

### <a name="state"></a>Estado
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

El nuevo estado de registro.