---
title: Archivo de inclusión
description: Archivo de inclusión
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: d94808ae1e97d12649f24ed89ad17a7962665d5e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805179"
---
### <a name="set-up-authentication-and-account-management"></a>Configurar la autenticación y la cuenta de administración

La plataforma de dispositivos conectados requiere un token de OAuth válido para usarse en el proceso de registro.  Puede usar el método preferido para generar y administrar los tokens de OAuth.  Sin embargo, para ayudar a los desarrolladores empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) que genera y administra los tokens de actualización para su comodidad.

Si desea implementar la **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interfaz usted mismo, tome nota de la siguiente información: 

Si usa una MSA, deberá incluir los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`. 

Si usa una cuenta de AAD, deberá solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, y `"https://activity.microsoft.com"`.

Si usas proporcionado **ConnectedDevicesAccountManager** implementación o no, si usas AAD deberá especificar los siguientes permisos en el registro de la aplicación en Azure portal (portal.azure.com > Azure Active Directory > registros de aplicaciones): 
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
