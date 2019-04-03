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
### <a name="register-your-app"></a>Registrar la aplicación

Cuenta de Microsoft (MSA) o Azure Active Directory (AAD) se requiere autenticación para casi todas las características del SDK de Roma proyecto (la excepción que se va a las API de uso compartidas cercanas). Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).

Mediante el método de autenticación seleccionado, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/). Si no tiene una cuenta de desarrollador de Microsoft, deberá crear uno.

Al registrar una aplicación con una MSA, debería recibir una cadena de identificador de cliente. Guardar esto para su uso posterior. Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft. Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.

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
