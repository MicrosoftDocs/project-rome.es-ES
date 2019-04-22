---
title: Archivo de inclusión
description: Archivo de inclusión
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: 1aa6b0d971feb7d2f9f8d31708fda31d05b5aca9
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805183"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="f323c-103">Configurar la autenticación y la cuenta de administración</span><span class="sxs-lookup"><span data-stu-id="f323c-103">Set up authentication and account management</span></span>

<span data-ttu-id="f323c-104">La plataforma de dispositivos conectados requiere un token de OAuth válido para usarse en el proceso de registro.</span><span class="sxs-lookup"><span data-stu-id="f323c-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="f323c-105">Puede usar el método preferido para generar y administrar los tokens de OAuth.</span><span class="sxs-lookup"><span data-stu-id="f323c-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="f323c-106">Sin embargo, para ayudar a los desarrolladores empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que puede usar para generar y administrar los tokens de actualización en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="f323c-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="f323c-107">Si no usa el código proporcionado, deberá implementar la **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interfaz usted mismo.</span><span class="sxs-lookup"><span data-stu-id="f323c-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="f323c-108">Si usa una MSA, incluyen los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="f323c-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

<span data-ttu-id="f323c-109">Si usa una cuenta de AAD, deberá solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, y `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="f323c-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="f323c-110">Si usas proporcionado **MCDConnectedDevicesAccountManager** implementación o no, si usas AAD deberá especificar los siguientes permisos en el registro de la aplicación en Azure portal (portal.azure.com > Azure Active Directory > registros de aplicaciones):</span><span class="sxs-lookup"><span data-stu-id="f323c-110">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="f323c-111">Servicio de la fuente de actividades de Microsoft</span><span class="sxs-lookup"><span data-stu-id="f323c-111">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="f323c-112">Entregar y modificar las notificaciones de usuario para esta aplicación</span><span class="sxs-lookup"><span data-stu-id="f323c-112">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="f323c-113">Leer y escribir la actividad de la aplicación a la fuente de actividades de los usuarios</span><span class="sxs-lookup"><span data-stu-id="f323c-113">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="f323c-114">Servicio de notificación de Windows</span><span class="sxs-lookup"><span data-stu-id="f323c-114">Windows Notification Service</span></span>
  * <span data-ttu-id="f323c-115">Conectar el dispositivo al servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="f323c-115">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="f323c-116">Servicio de directorio de dispositivos de Microsoft</span><span class="sxs-lookup"><span data-stu-id="f323c-116">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="f323c-117">Consulte la lista de dispositivos</span><span class="sxs-lookup"><span data-stu-id="f323c-117">See your list of devices</span></span>
  * <span data-ttu-id="f323c-118">Se agrega a la lista de dispositivos y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="f323c-118">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="f323c-119">Microsoft Command Service</span><span class="sxs-lookup"><span data-stu-id="f323c-119">Microsoft Command Service</span></span>
  * <span data-ttu-id="f323c-120">Comunicarse con dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="f323c-120">Communicate with user devices</span></span>
  * <span data-ttu-id="f323c-121">Dispositivos de usuario de lectura</span><span class="sxs-lookup"><span data-stu-id="f323c-121">Read user devices</span></span>
