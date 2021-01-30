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
### <a name="register-your-app"></a>Registro de la aplicación

La mayoría de las características del SDK de Project Rome (a excepción de las API de Uso compartido en proximidad) necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD). Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.

A partir del método de autenticación elegido, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/). Si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla.

Al registrar una aplicación con MSA, deberías recibir una cadena de id. de cliente. Guárdala para más adelante. Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft. Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.

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