---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801667"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>Configuración preliminar para la plataforma de dispositivos conectados

Antes de implementar la conectividad remota, debes seguir unos pasos para que la aplicación Android disponga de la funcionalidad para conectarse a dispositivos remotos.

### <a name="sign-in"></a>Iniciar sesión

Todas las características del SDK necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD), excepto las API de Uso compartido en proximidad. 

Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).

A continuación debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/) (si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla). Deberías recibir una cadena de id. de cliente para la aplicación; guárdala para más adelante. Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft. Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.

### <a name="add-the-sdk"></a>Incorporación del SDK

Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

Si quieres usar ProGuard en la aplicación, agrega las reglas de ProGuard para estas nuevas API. Crea un archivo llamado *proguard-rules.txt* en la carpeta *App* del proyecto y pega en él el contenido del archivo [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).

En el archivo *AndroidManifest.xml* del proyecto, agrega los siguientes permisos dentro del elemento `<manifest>` (si no están ya incluidos). Esto permite que la aplicación se conecte a Internet y habilite la detección de Bluetooth en el dispositivo.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Los permisos relacionados con Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados. Además, `ACCESS_COARSE_LOCATION` solo es necesario en los niveles de Android SDK 21 y posteriores. En los niveles de Android SDK 23 y posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.

A continuación, ve a las clases de actividad donde deseas incluir la funcionalidad de dispositivos conectados. Importa los siguientes espacios de nombres.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
