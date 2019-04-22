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
### <a name="add-the-sdk"></a>Agregue el SDK

Es la manera más sencilla de agregar la plataforma de dispositivos conectados a la aplicación iOS mediante el [CocoaPods](https://cocoapods.org/) Administrador de dependencias. Vaya a su proyecto de iOS *Podfile* e inserte la siguiente entrada:

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
> Para consumir CocoaPod, debe usar el _xcworkspace_ archivo del proyecto.

## <a name="initialize-the-connected-devices-platform"></a>Inicializar la plataforma de dispositivos conectados

Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación. 

Debe crear una instancia del **MCDPlatform** clase. El **MCDPlatform**del `platformWithAccountProvider:` método toma dos parámetros: un **MCDUserAccountProvider** y un **MCDNotificationProvider**. El **MCDNotificationProvider** parámetro sólo es necesario para el hospedaje de aplicaciones remotas y las actividades del usuario, que no se tratan en esta guía. Puede dejarse `nil` por ahora.

El **MCDUserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada. 

Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado una cuenta de las implementaciones del proveedor para iOS y Android. Estas implementaciones, se encuentra en la [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/iOS/samples/account-provider-sample), puede usarse para obtener el token de acceso de OAuth 2.0 y actualizar el token para la aplicación.

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

Apagar la plataforma cuando la aplicación cierra el primer plano mediante una llamada a la `shutdownAsync:` método.
