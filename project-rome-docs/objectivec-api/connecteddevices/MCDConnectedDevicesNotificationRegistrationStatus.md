---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: Obtenga información sobre la clase MCDConnectedDevicesNotificationRegistrationStatus. Estos valores se usan para comunicar el estado del registro en la nube.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: a7dd06a4593203f60275a540702ccfc164aa6b59
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761109"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a>las `MCDConnectedDevicesNotificationRegistrationStatus` 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
Enumeración que indica el estado de la operación de registro.
Los Estados de error indican condiciones transitorias en las que el desarrollador de la aplicación puede querer volver a intentar el registro.

## <a name="fields"></a>Campos

| NOMBRE                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesNotificationRegistrationStatusSuccess | 0 | Operación completada correctamente.
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork | 1 | La red no estaba disponible. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure | 2 | Error en un servicio Web. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber | 3 | Ningún suscriptor de solicitudes de token respondió. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed | 4 | Error en la solicitud de token. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound | 5 | No se encontró la cuenta para la que se va a registrar la información. |
| MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown | 6 | La operación encontró un error desconocido. |