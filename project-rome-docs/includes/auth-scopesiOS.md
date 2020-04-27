---
title: include file
description: include file
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b8a0de450431adce084919290d49f6326d23d51b
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755794"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="4d1d3-103">Configuración de la autenticación y la administración de cuentas</span><span class="sxs-lookup"><span data-stu-id="4d1d3-103">Set up authentication and account management</span></span>

<span data-ttu-id="4d1d3-104">La plataforma de dispositivos conectados requiere que se utilice un token OAuth válido en el proceso de registro.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="4d1d3-105">Puedes usar el método preferido para generar y administrar los tokens OAuth.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="4d1d3-106">Sin embargo, para ayudar a los desarrolladores a empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de iOS](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) que puedes usar para generar y administrar los tokens de actualización de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample) that you can use to generate and manage refresh tokens in your app.</span></span>

<span data-ttu-id="4d1d3-107">Si no usas el código proporcionado, deberás encargarte de implementar la interfaz **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** .</span><span class="sxs-lookup"><span data-stu-id="4d1d3-107">If you do not use the provided code, you will need to implement the **[MCDConnectedDevicesAccountManager](../objectivec-api/connecteddevices/MCDConnectedDevicesAccountManager.md)** interface yourself.</span></span>

<span data-ttu-id="4d1d3-108">Si usas una cuenta MSA, incluye los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-108">If you're using an MSA, include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span>

> [!NOTE]
> <span data-ttu-id="4d1d3-109">No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-109">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="4d1d3-110">Si usas una cuenta de AAD, deberás solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` y `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="4d1d3-110">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

<span data-ttu-id="4d1d3-111">Tanto si usas la implementación de **MCDConnectedDevicesAccountManager** proporcionada como si no, si utilizas AAD tendrás que especificar los siguientes permisos en el registro de la aplicación en Azure Portal (portal.azure.com > Azure Active Directory > Registros de aplicaciones):</span><span class="sxs-lookup"><span data-stu-id="4d1d3-111">Whether you use the provided **MCDConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span>
* <span data-ttu-id="4d1d3-112">Microsoft Activity Feed Service (Servicio de fuentes de actividad de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="4d1d3-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="4d1d3-113">Entregar y modificar notificaciones del usuario para esta aplicación</span><span class="sxs-lookup"><span data-stu-id="4d1d3-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="4d1d3-114">Leer y escribir la actividad de la aplicación en la fuente de actividades de los usuarios</span><span class="sxs-lookup"><span data-stu-id="4d1d3-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="4d1d3-115">Servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="4d1d3-115">Windows Notification Service</span></span>
  * <span data-ttu-id="4d1d3-116">Conectar su dispositivo al Servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="4d1d3-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="4d1d3-117">Microsoft Device Directory Service (Servicio de directorios de dispositivo de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="4d1d3-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="4d1d3-118">Ver la lista de dispositivos</span><span class="sxs-lookup"><span data-stu-id="4d1d3-118">See your list of devices</span></span>
  * <span data-ttu-id="4d1d3-119">Se agregará a su lista de dispositivos y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="4d1d3-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="4d1d3-120">Microsoft Command Service (Servicio de comandos de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="4d1d3-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="4d1d3-121">Comunicarse con los dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="4d1d3-121">Communicate with user devices</span></span>
  * <span data-ttu-id="4d1d3-122">Leer dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="4d1d3-122">Read user devices</span></span>
