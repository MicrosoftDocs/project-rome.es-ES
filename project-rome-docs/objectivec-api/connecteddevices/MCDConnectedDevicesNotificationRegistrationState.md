---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valores que se usa para comunicar el estado de registro en la nube.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909237"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>Clase `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
Valores que se usa para comunicar el estado de registro en la nube.

## <a name="fields"></a>Campos

| Nombre                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | Registro nunca se ha iniciado.
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | Complete el registro. |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | El registro está a punto de expirar y por lo que la aplicación debe realizar el registro nuevo. |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | Registro ha expirado y, por lo que la aplicación debe realizar el registro nuevo. |