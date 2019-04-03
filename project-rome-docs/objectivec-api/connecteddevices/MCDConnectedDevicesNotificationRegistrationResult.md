---
title: MCDConnectedDevicesNotificationRegistrationResult
description: Se comunica el resultado asincrónico de registrar información de notificación de una cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907747"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a>Clase `MCDConnectedDevicesNotificationRegistrationResult` 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
MCDConnectedDevicesNotificationRegistrationResult se comunica el resultado asincrónico de registrar información de notificación de una cuenta. Los Estados de error que se comunica a través de este resultado se deben usar por la aplicación para volver a intentar el registro en el caso de ciertas condiciones transitorias como la red no esté disponible.

## <a name="properties"></a>Propiedades

### <a name="status"></a>status

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

Enumeración de estado de la operación de registro.