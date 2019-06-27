---
ms.openlocfilehash: 8e259cf4bd303a51165868fe0aa6d2a062f52c76
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "58907397"
---
### <a name="msa-and-aad-authentication-registration"></a>Registro de autenticación con MSA y AAD

Todas las características del SDK, incluida Notificaciones, necesitan el registro de autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD), excepto las API de Uso compartido en proximidad. 

Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).

Si después utilizas MSA como marco de autenticación e identidad para los usuarios, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/) (si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla). Debes recibir una cadena de id. de cliente para la aplicación; asegúrate de recordar la ubicación o guardarla. La usarás más adelante durante la incorporación a Notificaciones de Graph. Ten en cuenta que una aplicación que utiliza la autenticación de MSA debe estar registrada como aplicación de SDK de Live, como se muestra a continuación.
![Portal de registro de aplicaciones](../../notifications/media/msa_app_registration/app_registration_portal.png)

Si escribes una aplicación que usa AAD como marco de autenticación e identidad de cuentas profesionales o educativas, debes registrarla a través de las [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) con el fin de obtener el id. de cliente, como se muestra a continuación. 
 ![Portal de registro de AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) Cuando se crea el registro de una nueva aplicación, se necesitan algunos permisos para poder usar las notificaciones de Graph y otras funcionalidades de la plataforma de dispositivos conectados. Consúltalos a continuación. 
![Portal de registro de AAD: configuración, permisos necesarios](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* Agrega el permiso de inicio de sesión del usuario tal como se muestra a continuación.
![Permisos necesarios: perfil de usuario de AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* Agrega permisos del servicio de comandos para la información de dispositivo, tal como se muestra a continuación.
![Permisos necesarios: dispositivos](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* Agrega el permiso para notificaciones de Graph en las API del servicio de fuente de actividades, tal como se muestra a continuación.
![Permisos necesarios: dispositivos](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* Al final, si escribes una aplicación multiplataforma que incluye una aplicación para UWP que se ejecuta en Windows, asegúrate de agregar el permiso del Servicio de notificaciones de Windows, tal como se muestra a continuación. 
![Permisos necesarios: servicios de notificaciones de inserción de Windows](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
