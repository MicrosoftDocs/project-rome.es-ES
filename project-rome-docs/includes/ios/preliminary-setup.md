---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 53cbe2ec68785c257341caf110439d535b8f83be
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907627"
---
### <a name="register-your-app"></a><span data-ttu-id="b7edb-103">Registrar la aplicación</span><span class="sxs-lookup"><span data-stu-id="b7edb-103">Register your app</span></span>

<span data-ttu-id="b7edb-104">Cuenta de Microsoft (MSA) o Azure Active Directory (AAD) se requiere autenticación para casi todas las características del SDK de Roma proyecto (la excepción que se va a las API de uso compartidas cercanas).</span><span class="sxs-lookup"><span data-stu-id="b7edb-104">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="b7edb-105">Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="b7edb-105">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="b7edb-106">Mediante el método de autenticación seleccionado, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b7edb-106">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="b7edb-107">Si no tiene una cuenta de desarrollador de Microsoft, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="b7edb-107">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="b7edb-108">Al registrar una aplicación con una MSA, debería recibir una cadena de identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="b7edb-108">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="b7edb-109">Guardar esto para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="b7edb-109">Save this for later.</span></span> <span data-ttu-id="b7edb-110">Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b7edb-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="b7edb-111">Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.</span><span class="sxs-lookup"><span data-stu-id="b7edb-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="b7edb-112">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="b7edb-112">Add the SDK</span></span>

<span data-ttu-id="b7edb-113">Es la manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS mediante el [CocoaPods](https://cocoapods.org/) Administrador de dependencias.</span><span class="sxs-lookup"><span data-stu-id="b7edb-113">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="b7edb-114">Vaya a su proyecto de iOS *Podfile* e inserte la siguiente entrada:</span><span class="sxs-lookup"><span data-stu-id="b7edb-114">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="b7edb-115">Para consumir CocoaPod, debe usar el _xcworkspace_ archivo del proyecto.</span><span class="sxs-lookup"><span data-stu-id="b7edb-115">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>
