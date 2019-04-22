---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801607"
---
### <a name="add-the-sdk"></a><span data-ttu-id="857dc-103">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="857dc-103">Add the SDK</span></span>

<span data-ttu-id="857dc-104">Es la manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS mediante el [CocoaPods](https://cocoapods.org/) Administrador de dependencias.</span><span class="sxs-lookup"><span data-stu-id="857dc-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="857dc-105">Vaya a su proyecto de iOS *Podfile* e inserte la siguiente entrada:</span><span class="sxs-lookup"><span data-stu-id="857dc-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="857dc-106">Para consumir CocoaPod, debe usar el _xcworkspace_ archivo del proyecto.</span><span class="sxs-lookup"><span data-stu-id="857dc-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="857dc-107">Inicializar la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="857dc-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="857dc-108">Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="857dc-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="857dc-109">Debe crear una instancia del **MCDPlatform** clase.</span><span class="sxs-lookup"><span data-stu-id="857dc-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="857dc-110">El **MCDPlatform**del `platformWithAccountProvider:` método toma dos parámetros: un **MCDUserAccountProvider** y un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="857dc-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="857dc-111">El **MCDNotificationProvider** parámetro sólo es necesario para el hospedaje de aplicaciones remotas y las actividades del usuario, que no se tratan en esta guía.</span><span class="sxs-lookup"><span data-stu-id="857dc-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="857dc-112">Puede dejarse `nil` por ahora.</span><span class="sxs-lookup"><span data-stu-id="857dc-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="857dc-113">El **MCDUserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="857dc-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="857dc-114">Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada.</span><span class="sxs-lookup"><span data-stu-id="857dc-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="857dc-115">Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado una cuenta de las implementaciones del proveedor para iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="857dc-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="857dc-116">Estas implementaciones, se encuentra en la [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), puede usarse para obtener el token de acceso de OAuth 2.0 y actualizar el token para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="857dc-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="857dc-117">El siguiente código de la aplicación de ejemplo muestra la inicialización de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="857dc-117">The following code from the sample app shows the initialization of the platform.</span></span>

```ObjectiveC
- (void)initializePlatform
{
    // Only register for APNs if this app is enabled for push notifications
    NotificationProvider* notificationProvider;
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        notificationProvider = [AppDataSource sharedInstance].notificationProvider;
    }
    else
    {
        NSLog(@"Initializing platform without a notification provider!");
        notificationProvider = nil;
    }

    // Initialize platform
    [AppDataSource sharedInstance].platform = [MCDPlatform platformWithAccountProvider:[AppDataSource sharedInstance].accountProvider notificationProvider:notificationProvider];

    // ...
}
```

<span data-ttu-id="857dc-118">Apagar la plataforma cuando la aplicación cierra el primer plano mediante una llamada a la `shutdownAsync:` método.</span><span class="sxs-lookup"><span data-stu-id="857dc-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
