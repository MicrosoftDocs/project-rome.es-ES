---
title: include file
description: include file
ms.assetid: 93f45482-14e4-4aec-8185-ee05b592215f
ms.localizationpriority: medium
ms.openlocfilehash: b81da462f97569d322b76ebff36f800c970c06cc
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901582"
---
### <a name="set-up-authentication-and-account-management"></a><span data-ttu-id="c1002-103">Configuración de la autenticación y la administración de cuentas</span><span class="sxs-lookup"><span data-stu-id="c1002-103">Set up authentication and account management</span></span>

<span data-ttu-id="c1002-104">La plataforma de dispositivos conectados requiere que se utilice un token OAuth válido en el proceso de registro.</span><span class="sxs-lookup"><span data-stu-id="c1002-104">The Connected Devices Platform requires a valid OAuth token to be used in the registration process.</span></span>  <span data-ttu-id="c1002-105">Puedes usar el método preferido para generar y administrar los tokens OAuth.</span><span class="sxs-lookup"><span data-stu-id="c1002-105">You may use your preferred method of generating and managing the OAuth tokens.</span></span>  <span data-ttu-id="c1002-106">Sin embargo, para ayudar a los desarrolladores a empezar a usar la plataforma, hemos incluido un proveedor de autenticación como parte de la [aplicación de ejemplo de Android](https://github.com/Microsoft/project-rome/tree/master/Android/samples) que se encarga de generar y administrar los tokens de actualización.</span><span class="sxs-lookup"><span data-stu-id="c1002-106">However, to help developers get started using the platform, we've included an authentication provider as a part of the [Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples) that generates and manages refresh tokens for your convenience.</span></span>

<span data-ttu-id="c1002-107">Si deseas implementar tú mismo la interfaz **[ConnectedDevicesAccountManager](/java/api/com.microsoft.connecteddevices.core._user_account_provider)** , tome nota de la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="c1002-107">If you wish to implement the **[ConnectedDevicesAccountManager](/java/api/com.microsoft.connecteddevices.core._user_account_provider)** interface yourself, take note of the following information:</span></span> 

<span data-ttu-id="c1002-108">Si usas una cuenta MSA, debes incluir los siguientes ámbitos en la solicitud de inicio de sesión: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"` y `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span><span class="sxs-lookup"><span data-stu-id="c1002-108">If you're using an MSA, you will need to include the following scopes in your sign-in request: `"wl.offline_access"`, `"ccs.ReadWrite"`, `"dds.read"`, `"dds.register"`, `"wns.connect"`, `"asimovrome.telemetry"`, and `"https://activity.windows.com/UserActivity.ReadWrite.CreatedByApp"`.</span></span> 

<span data-ttu-id="c1002-109">Si usas una cuenta de AAD, deberás solicitar los siguientes destinatarios: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"` y `"https://activity.microsoft.com"`.</span><span class="sxs-lookup"><span data-stu-id="c1002-109">If you're using an AAD account, you'll need to request the following audiences: `"https://cdpcs.access.microsoft.com"`, `"https://cs.dds.microsoft.com"`, `"https://wns.windows.com/"`, and `"https://activity.microsoft.com"`.</span></span>

> [!NOTE]
> <span data-ttu-id="c1002-110">No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c1002-110">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="c1002-111">Tanto si usas la implementación de **ConnectedDevicesAccountManager** proporcionada como si no, si utilizas AAD tendrás que especificar los siguientes permisos en el registro de la aplicación en Azure Portal (portal.azure.com > Azure Active Directory > Registros de aplicaciones):</span><span class="sxs-lookup"><span data-stu-id="c1002-111">Whether you use the provided **ConnectedDevicesAccountManager** implementation or not, if you are using AAD you'll need to specify the following permissions in your app's registration on the Azure portal (portal.azure.com > Azure Active Directory > App registrations):</span></span> 
* <span data-ttu-id="c1002-112">Microsoft Activity Feed Service (Servicio de fuentes de actividad de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="c1002-112">Microsoft Activity Feed Service</span></span> 
  * <span data-ttu-id="c1002-113">Entregar y modificar notificaciones del usuario para esta aplicación</span><span class="sxs-lookup"><span data-stu-id="c1002-113">Deliver and modify user notifications for this app</span></span>
  * <span data-ttu-id="c1002-114">Leer y escribir la actividad de la aplicación en la fuente de actividades de los usuarios</span><span class="sxs-lookup"><span data-stu-id="c1002-114">Read and write app activity to users' activity feed</span></span>
* <span data-ttu-id="c1002-115">Servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="c1002-115">Windows Notification Service</span></span>
  * <span data-ttu-id="c1002-116">Conectar su dispositivo al Servicio de notificaciones de Windows</span><span class="sxs-lookup"><span data-stu-id="c1002-116">Connect your device to Windows Notification Service</span></span> 
* <span data-ttu-id="c1002-117">Microsoft Device Directory Service (Servicio de directorios de dispositivo de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="c1002-117">Microsoft Device Directory Service</span></span>
  * <span data-ttu-id="c1002-118">Ver la lista de dispositivos</span><span class="sxs-lookup"><span data-stu-id="c1002-118">See your list of devices</span></span>
  * <span data-ttu-id="c1002-119">Se agregará a su lista de dispositivos y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="c1002-119">Be added to your list of devices and apps</span></span> 
* <span data-ttu-id="c1002-120">Microsoft Command Service (Servicio de comandos de Microsoft)</span><span class="sxs-lookup"><span data-stu-id="c1002-120">Microsoft Command Service</span></span>
  * <span data-ttu-id="c1002-121">Comunicarse con los dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="c1002-121">Communicate with user devices</span></span>
  * <span data-ttu-id="c1002-122">Leer dispositivos de usuario</span><span class="sxs-lookup"><span data-stu-id="c1002-122">Read user devices</span></span>