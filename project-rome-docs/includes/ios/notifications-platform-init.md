---
title: include file
description: include file
ms.topic: include
ms.assetid: cf4bc236-1a9c-4192-b3fe-2d78331316c0
ms.localizationpriority: medium
ms.openlocfilehash: 6de00cdfd4595f67a655a672dc46fea75806a51f
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801607"
---
### <a name="add-the-sdk"></a><span data-ttu-id="8118b-103">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="8118b-103">Add the SDK</span></span>

<span data-ttu-id="8118b-104">La manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS es hacerlo a través del administrador de dependencias [CocoaPods](https://cocoapods.org/).</span><span class="sxs-lookup"><span data-stu-id="8118b-104">The simplest way to add the Connected Devices Platform to your iOS app is by using the [CocoaPods](https://cocoapods.org/) dependency manager.</span></span> <span data-ttu-id="8118b-105">Ve al archivo *Podfile* del proyecto de iOS e inserta la siguiente entrada:</span><span class="sxs-lookup"><span data-stu-id="8118b-105">Go to your iOS project's *Podfile* and insert the following entry:</span></span>

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
> <span data-ttu-id="8118b-106">Para utilizar CocoaPod, debes usar el archivo _xcworkspace_ en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="8118b-106">In order to consume CocoaPod, you must use the _.xcworkspace_ file in your project.</span></span>

## <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="8118b-107">Inicialización de la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="8118b-107">Initialize the Connected Devices platform</span></span>

<span data-ttu-id="8118b-108">Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8118b-108">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> 

<span data-ttu-id="8118b-109">Debes crear una instancia de la clase **MCDPlatform**.</span><span class="sxs-lookup"><span data-stu-id="8118b-109">You must instantiate the **MCDPlatform** class.</span></span> <span data-ttu-id="8118b-110">El método `platformWithAccountProvider:` de **MCDPlatform** incluye dos parámetros: **MCDUserAccountProvider** y **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="8118b-110">The **MCDPlatform**'s `platformWithAccountProvider:` method takes two parameters: a **MCDUserAccountProvider** and a **MCDNotificationProvider**.</span></span> <span data-ttu-id="8118b-111">El parámetro **MCDNotificationProvider** solo es necesario para el hospedaje de aplicaciones remotas y las actividades del usuario, que no se tratan en esta guía.</span><span class="sxs-lookup"><span data-stu-id="8118b-111">The **MCDNotificationProvider** parameter is only needed for remote app hosting and User Activities, which are not covered in this guide.</span></span> <span data-ttu-id="8118b-112">Puede dejarse como `nil` por ahora.</span><span class="sxs-lookup"><span data-stu-id="8118b-112">It can be left `nil` for now.</span></span>

<span data-ttu-id="8118b-113">El parámetro **MCDUserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="8118b-113">The **MCDUserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="8118b-114">Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="8118b-114">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="8118b-115">Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="8118b-115">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="8118b-116">Estas implementaciones, que se encuentran en el [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), pueden usarse para obtener los token de acceso y actualización OAuth 2.0 para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="8118b-116">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="8118b-117">El siguiente código de la aplicación de ejemplo muestra la inicialización de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="8118b-117">The following code from the sample app shows the initialization of the platform.</span></span>

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

<span data-ttu-id="8118b-118">Apaga la plataforma con una llamada al método `shutdownAsync:` cuando la aplicación salga del primer plano.</span><span class="sxs-lookup"><span data-stu-id="8118b-118">Shut down the platform when your app exits the foreground by calling the `shutdownAsync:` method.</span></span>
