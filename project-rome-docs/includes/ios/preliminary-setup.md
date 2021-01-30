---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: d0a91c583bda39cdef57adfdcab185e26e08195e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901572"
---
### <a name="register-your-app"></a><span data-ttu-id="a07ac-103">Registro de la aplicación</span><span class="sxs-lookup"><span data-stu-id="a07ac-103">Register your app</span></span>

<span data-ttu-id="a07ac-104">La mayoría de las características del SDK de Project Rome (a excepción de las API de Uso compartido en proximidad) necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="a07ac-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="a07ac-105">Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="a07ac-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="a07ac-106">No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a07ac-106">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="a07ac-107">A partir del método de autenticación elegido, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="a07ac-107">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="a07ac-108">Si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla.</span><span class="sxs-lookup"><span data-stu-id="a07ac-108">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="a07ac-109">Al registrar una aplicación con MSA, deberías recibir una cadena de id. de cliente.</span><span class="sxs-lookup"><span data-stu-id="a07ac-109">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="a07ac-110">Guárdala para más adelante.</span><span class="sxs-lookup"><span data-stu-id="a07ac-110">Save this for later.</span></span> <span data-ttu-id="a07ac-111">Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a07ac-111">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="a07ac-112">Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.</span><span class="sxs-lookup"><span data-stu-id="a07ac-112">If you're using AAD, see [Azure Active Directory Authentication Libraries](/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="a07ac-113">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="a07ac-113">Add the SDK</span></span>

<span data-ttu-id="a07ac-114">La manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS es hacerlo a través del administrador de dependencias [CocoaPods](https://cocoapods.org/).</span><span class="sxs-lookup"><span data-stu-id="a07ac-114">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="a07ac-115">Ve al archivo *Podfile* del proyecto de iOS e inserta la siguiente entrada:</span><span class="sxs-lookup"><span data-stu-id="a07ac-115">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

```ObjectiveC
platform :ios, "10.0"
workspace 'iOSSample'

target 'iOSSample' do
  # Uncomment the next line if you're using Swift or would like to use dynamic frameworks
  # use_frameworks!

    pod 'ProjectRomeSdk'

  # Pods for iOSSample
```

> [!NOTE]
> <span data-ttu-id="a07ac-116">Para utilizar CocoaPod, debes usar el archivo _xcworkspace_ en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="a07ac-116">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>