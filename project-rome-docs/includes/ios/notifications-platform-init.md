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
### <a name="add-the-sdk"></a>Incorporación del SDK

La manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS es hacerlo a través del administrador de dependencias [CocoaPods](https://cocoapods.org/). Ve al archivo *Podfile* del proyecto de iOS e inserta la siguiente entrada:

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
> Para utilizar CocoaPod, debes usar el archivo _xcworkspace_ en el proyecto.

## <a name="initialize-the-connected-devices-platform"></a>Inicialización de la plataforma de dispositivos conectados

Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación. 

Debes crear una instancia de la clase **MCDPlatform**. El método `platformWithAccountProvider:` de **MCDPlatform** incluye dos parámetros: **MCDUserAccountProvider** y **MCDNotificationProvider**. El parámetro **MCDNotificationProvider** solo es necesario para el hospedaje de aplicaciones remotas y las actividades del usuario, que no se tratan en esta guía. Puede dejarse como `nil` por ahora.

El parámetro **MCDUserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma. 

Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para iOS y Android. Estas implementaciones, que se encuentran en el [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), pueden usarse para obtener los token de acceso y actualización OAuth 2.0 para la aplicación.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

El siguiente código de la aplicación de ejemplo muestra la inicialización de la plataforma.

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

Apaga la plataforma con una llamada al método `shutdownAsync:` cuando la aplicación salga del primer plano.
