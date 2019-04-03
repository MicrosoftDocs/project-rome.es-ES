---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: 45aa2364c2b1f7a30e94e2b720a0e4b14d4bff27
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907797"
---
## <a name="preliminary-setup-for-the-connected-devices-platform"></a>Instalación preliminar para la plataforma de dispositivos conectados

Antes de implementar conectividad remota, hay unos pasos que deberá tomar para proporcionar la funcionalidad para conectarse a los dispositivos remotos a la aplicación Android.

### <a name="sign-in"></a>Iniciar sesión

Se requiere autenticación de cuenta de Microsoft (MSA) o Azure Active Directory (AAD) para todas las características del SDK, excepto para el uso compartido de Nearby API. 

Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).

A continuación, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/) (si no tiene una cuenta de desarrollador de Microsoft, debe crear una primera). Debería recibir una cadena de identificador de cliente de la aplicación; guardar esto para su uso posterior. Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft. Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.

### <a name="add-the-sdk"></a>Agregue el SDK

Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

Si desea usar ProGuard en la aplicación, agregue las reglas de ProGuard de estas nuevas API. Cree un archivo llamado *proguard rules.txt* en el *aplicación* carpeta del proyecto y pegue los contenidos de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).

En el proyecto *AndroidManifest.xml* , agregue los siguientes permisos dentro de la `<manifest>` elemento (si aún no están presentes). Esto da permiso a la aplicación para conectarse a Internet y para habilitar la detección de Bluetooth en el dispositivo.

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> Los permisos relacionados con el Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados. Además, `ACCESS_COARSE_LOCATION` sólo es necesario en 21 de Android SDK y versiones posteriores. 23 de Android SDK y versiones posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.

A continuación, vaya a la clase o clases de actividad donde desea que la funcionalidad de dispositivos conectados a live. Importar los espacios de nombres siguientes.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
