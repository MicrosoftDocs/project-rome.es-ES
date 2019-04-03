---
title: Archivo de inclusión
description: Archivo de inclusión
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: 1aa6b0d971feb7d2f9f8d31708fda31d05b5aca9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907907"
---
### <a name="set-up-authentication-and-account-management"></a>Configurar la autenticación y la cuenta de administración

La plataforma de dispositivos conectados requiere un token de OAuth válido para usarse en el proceso de registro.  Puede usar el método preferido para generar y administrar los tokens de OAuth.  Sin embargo, para ayudar a los desarrolladores empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que puede usar para generar y administrar los tokens de actualización en la aplicación.

Si no usa el código proporcionado, deberá implementar la **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interfaz usted mismo.

Si usa una MSA, incluyen los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.

Si usa una cuenta de AAD, deberá solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, y `"https://activity.microsoft.com"`.

Si usas proporcionado **MCDConnectedDevicesAccountManager** implementación o no, si usas AAD deberá especificar los siguientes permisos en el registro de la aplicación en Azure portal (portal.azure.com > Azure Active Directory > registros de aplicaciones):
* Servicio de la fuente de actividades de Microsoft 
  * Entregar y modificar las notificaciones de usuario para esta aplicación
  * Leer y escribir la actividad de la aplicación a la fuente de actividades de los usuarios
* Servicio de notificación de Windows
  * Conectar el dispositivo al servicio de notificaciones de Windows 
* Servicio de directorio de dispositivos de Microsoft
  * Consulte la lista de dispositivos
  * Se agrega a la lista de dispositivos y aplicaciones 
* Microsoft Command Service
  * Comunicarse con dispositivos de usuario
  * Dispositivos de usuario de lectura
