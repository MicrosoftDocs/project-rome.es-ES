---
title: Archivo de inclusión
description: Archivo de inclusión
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: a79123257cd2dc7214fcf691849ea6f56b3b2b70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/07/2019
ms.locfileid: "66755794"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="11d7b-103">Configurar la autenticación y la cuenta de administración</span><span class="sxs-lookup"><span data-stu-id="11d7b-103">Set up authentication and account management</span></span>

<span data-ttu-id="11d7b-104">La plataforma de dispositivos conectados requiere un token de OAuth válido para usarse en el proceso de registro.</span><span class="sxs-lookup"><span data-stu-id="11d7b-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="11d7b-105">Puede usar el método preferido para generar y administrar los tokens de OAuth.</span><span class="sxs-lookup"><span data-stu-id="11d7b-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="11d7b-106">Sin embargo, para ayudar a los desarrolladores empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que puede usar para generar y administrar los tokens de actualización en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="11d7b-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="11d7b-107">Si no usa el código proporcionado, deberá implementar la **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interfaz usted mismo.</span><span class="sxs-lookup"><span data-stu-id="11d7b-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="11d7b-108">Si usa una MSA, incluyen los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="11d7b-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

> [!NOTE]
> <span data-ttu-id="11d7b-109">No se admiten las cuentas de Azure Active Directory (AAD) con las API de Relay de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="11d7b-109">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="11d7b-110">Si usa una cuenta de AAD, deberá solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, y `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="11d7b-110">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="11d7b-111">Si usas proporcionado **MCDConnectedDevicesAccountManager** implementación o no, si usas AAD deberá especificar los siguientes permisos en el registro de la aplicación en Azure portal (portal.azure.com > Azure Active Directory > registros de aplicaciones):</span><span class="sxs-lookup"><span data-stu-id="11d7b-111">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="11d7b-112">Servicio de la fuente de actividades de Microsoft</span><span class="sxs-lookup"><span data-stu-id="11d7b-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="11d7b-113">Entregar y modificar las notificaciones de usuario para esta aplicación</span><span class="sxs-lookup"><span data-stu-id="11d7b-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="11d7b-114">Leer y escribir la actividad de la aplicación a la fuente de actividades de los usuarios</span><span class="sxs-lookup"><span data-stu-id="11d7b-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="11d7b-115">Servicio de notificación de Windows</span><span class="sxs-lookup"><span data-stu-id="11d7b-115">Windows Notification Service</span></span>
  * <span data-ttu-id="11d7b-116">Conectar el dispositivo al servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="11d7b-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="11d7b-117">Servicio de directorio de dispositivos de Microsoft</span><span class="sxs-lookup"><span data-stu-id="11d7b-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="11d7b-118">Consulte la lista de dispositivos</span><span class="sxs-lookup"><span data-stu-id="11d7b-118">See your list of devices</span></span>
  * <span data-ttu-id="11d7b-119">Se agrega a la lista de dispositivos y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="11d7b-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="11d7b-120">Microsoft Command Service</span><span class="sxs-lookup"><span data-stu-id="11d7b-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="11d7b-121">Comunicarse con dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="11d7b-121">Communicate with user devices</span></span>
  * <span data-ttu-id="11d7b-122">Dispositivos de usuario de lectura</span><span class="sxs-lookup"><span data-stu-id="11d7b-122">Read user devices</span></span>
