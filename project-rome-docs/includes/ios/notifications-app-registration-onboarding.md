---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 771ceeb1-638f-4fba-8c34-953870b5d855
ms.localizationpriority: medium
ms.openlocfilehash: 49538cfee916d048160bdd8cd1e82a7490b979d6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908937"
---
### <a name="msa-and-aad-authentication-registration"></a>MSA y registro de la autenticación de AAD

Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).

A continuación, si utilizas MSA como la autenticación y el marco de identidad para los usuarios, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/) (si no tiene un Microsoft cuenta de desarrollador, debe crear una primera). Debería recibir una cadena de identificador de cliente de la aplicación; Asegúrese de recordar la ubicación o guardar esto. Más adelante se usará durante la incorporación de notificaciones de gráfico. Tenga en cuenta que una aplicación mediante la autenticación de MSA debe estar registrada como una aplicación de SDK de Live.
![Portal de registro de aplicación](../../notifications/media/msa_app_registration/app_registration_portal.png)

Si está escribiendo una aplicación que usa AAD como cuenta profesional o educativa autenticación y cuentas marco de identidad, debe registrar la aplicación a través de [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) con el fin de obtener el identificador de cliente. 
 ![Portal de registro de AAD](../../notifications/media/aad_registration_portal/aad_registration_portal.png) al crear un nuevo registro de aplicación, hay algunos permisos necesarios para poder usar las notificaciones de Graph y otras capacidades de plataforma de dispositivo conectado. Consulte a continuación. 
![AAD Portal: configuración – requiere permisos de registro de](../../notifications/media/aad_registration_portal/aad_registration_portal_permissions.png)
* Agregue el permiso de inicio de sesión de usuario.
![Permisos necesarios: perfil de usuario AAD](../../notifications/media/aad_registration_portal/permissions_1_user.png)
* Agregar permisos de servicio de comandos para obtener información del dispositivo.
![Permisos necesarios: los dispositivos](../../notifications/media/aad_registration_portal/permissions_2_devices.png)
* Agregue el permiso de Graph notificaciones en las API de servicios de fuente de actividad.
![Permisos necesarios: los dispositivos](../../notifications/media/aad_registration_portal/permissions_3_graph_notifications.png)
* Al final, si está escribiendo aplicaciones multiplataforma incluida una aplicación de UWP que se ejecutan en Windows, asegúrese de agregar permiso de servicio de notificación de Windows.
![Permisos necesarios: WNS](../../notifications/media/aad_registration_portal/permissions_4_wns_push.png)
