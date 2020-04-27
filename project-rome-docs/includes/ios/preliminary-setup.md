---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b979c0b7891aaa6ce5c422d8349809b429a47201
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755764"
---
### <a name="register-your-app"></a>Registro de la aplicación

La mayoría de las características del SDK de Project Rome (a excepción de las API de Uso compartido en proximidad) necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD). Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.

A partir del método de autenticación elegido, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/). Si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla.

Al registrar una aplicación con MSA, deberías recibir una cadena de id. de cliente. Guárdala para más adelante. Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft. Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.

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
