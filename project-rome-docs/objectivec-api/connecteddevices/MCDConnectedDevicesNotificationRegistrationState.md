---
title: MCDConnectedDevicesNotificationRegistrationState
description: Valores que se usa para comunicar el estado de registro en la nube.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: be390f4f8e5d3c026d35bb8998e2818b9db05e86
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800717"
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