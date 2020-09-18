---
title: MCDConnectedDevicesNotificationRegistrationState
description: Obtenga información sobre la clase MCDConnectedDevicesNotificationRegistrationState. Estos valores se usan para comunicar el estado del registro en la nube.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 8b69443b53532280df3deeef51025f18e70fecac
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761119"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstate"></a>las `MCDConnectedDevicesNotificationRegistrationState` 

```
typedef NS_ENUM(NSUInteger, MCDConnectedDevicesNotificationRegistrationState)
```  
Valores usados para comunicar el estado del registro en la nube.

## <a name="fields"></a>Campos

| NOMBRE                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStateUnregistered | 0 | No se ha iniciado nunca el registro.
| MCDConnectedDevicesNotificationRegistrationStateRegistered | 1 | El registro ha finalizado. |
| MCDConnectedDevicesNotificationRegistrationStateExpiring | 2 | El registro está a punto de expirar y, por tanto, la aplicación debe realizar el registro de nuevo. |
| MCDConnectedDevicesNotificationRegistrationStateExpired | 3 | El registro ha expirado y, por lo tanto, la aplicación debe volver a realizar el registro. |