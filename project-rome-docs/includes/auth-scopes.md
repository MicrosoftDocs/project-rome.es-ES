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
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="81447-103">Configurar la autenticación y la cuenta de administración</span><span class="sxs-lookup"><span data-stu-id="81447-103">Set up authentication and account management</span></span>

<span data-ttu-id="81447-104">La plataforma de dispositivos conectados requiere un token de OAuth válido para usarse en el proceso de registro.</span><span class="sxs-lookup"><span data-stu-id="81447-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="81447-105">Puede usar el método preferido para generar y administrar los tokens de OAuth.</span><span class="sxs-lookup"><span data-stu-id="81447-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="81447-106">Sin embargo, para ayudar a los desarrolladores empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) que genera y administra los tokens de actualización para su comodidad.</span><span class="sxs-lookup"><span data-stu-id="81447-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="81447-107">Si desea implementar la **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interfaz usted mismo, tome nota de la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="81447-107">If you wish to implement the **[ConnectedDevicesAccountManager](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="81447-108">Si usa una MSA, deberá incluir los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="81447-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="81447-109">Si usa una cuenta de AAD, deberá solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, y `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="81447-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="81447-110">Si usas proporcionado **ConnectedDevicesAccountManager** implementación o no, si usas AAD deberá especificar los siguientes permisos en el registro de la aplicación en Azure portal (portal.azure.com > Azure Active Directory > registros de aplicaciones):</span><span class="sxs-lookup"><span data-stu-id="81447-110">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="81447-111">Servicio de la fuente de actividades de Microsoft</span><span class="sxs-lookup"><span data-stu-id="81447-111">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="81447-112">Entregar y modificar las notificaciones de usuario para esta aplicación</span><span class="sxs-lookup"><span data-stu-id="81447-112">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="81447-113">Leer y escribir la actividad de la aplicación a la fuente de actividades de los usuarios</span><span class="sxs-lookup"><span data-stu-id="81447-113">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="81447-114">Servicio de notificación de Windows</span><span class="sxs-lookup"><span data-stu-id="81447-114">Windows Notification Service</span></span>
  * <span data-ttu-id="81447-115">Conectar el dispositivo al servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="81447-115">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="81447-116">Servicio de directorio de dispositivos de Microsoft</span><span class="sxs-lookup"><span data-stu-id="81447-116">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="81447-117">Consulte la lista de dispositivos</span><span class="sxs-lookup"><span data-stu-id="81447-117">See your list of devices</span></span>
  * <span data-ttu-id="81447-118">Se agrega a la lista de dispositivos y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="81447-118">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="81447-119">Microsoft Command Service</span><span class="sxs-lookup"><span data-stu-id="81447-119">Microsoft Command Service</span></span>
  * <span data-ttu-id="81447-120">Comunicarse con dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="81447-120">Communicate with user devices</span></span>
  * <span data-ttu-id="81447-121">Dispositivos de usuario de lectura</span><span class="sxs-lookup"><span data-stu-id="81447-121">Read user devices</span></span>
