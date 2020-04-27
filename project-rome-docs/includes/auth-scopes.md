---
title: include file
description: include file
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: a6e92df6114443827b22dc85cf877d631e5fcfdf
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755775"
---
### <a name="set-up-authentication-and-account-management"></a>Configuración de la autenticación y la administración de cuentas

La plataforma de dispositivos conectados requiere que se utilice un token OAuth válido en el proceso de registro.  Puedes usar el método preferido para generar y administrar los tokens OAuth.  Sin embargo, para ayudar a los desarrolladores a empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) que se encarga de generar y administrar los tokens de actualización.

Si deseas implementar tú mismo la interfaz **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** , tome nota de la siguiente información: 

Si usas una cuenta MSA, debes incluir los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`. 

Si usas una cuenta de AAD, deberás solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` y `"https://activity.microsoft.com"`.

> [!NOTE]
> No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.

Tanto si usas la implementación de **ConnectedDevicesAccountManager** proporcionada como si no, si utilizas AAD tendrás que especificar los siguientes permisos en el registro de la aplicación en Azure Portal (portal.azure.com > Azure Active Directory > Registros de aplicaciones): 
* Microsoft Activity Feed Service (Servicio de fuentes de actividad de Microsoft) 
  * Entregar y modificar notificaciones del usuario para esta aplicación
  * Leer y escribir la actividad de la aplicación en la fuente de actividades de los usuarios
* Servicio de notificaciones de Windows
  * Conectar su dispositivo al Servicio de notificaciones de Windows 
* Microsoft Device Directory Service (Servicio de directorios de dispositivo de Microsoft)
  * Ver la lista de dispositivos
  * Se agregará a su lista de dispositivos y aplicaciones 
* Microsoft Command Service (Servicio de comandos de Microsoft)
  * Comunicarse con los dispositivos de usuario
  * Leer dispositivos de usuario
