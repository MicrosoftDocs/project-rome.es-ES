---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: e2a3dcbff4594a7886a14f90058bb814e85ff39d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909377"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>Instalación preliminar para la plataforma de dispositivos conectados y notificaciones

Antes de implementar conectividad remota, hay unos pasos que deberá tomar para dar la capacidad para conectarse a dispositivos remotos, así como enviar y recibir notificaciones de la aplicación Android.

### <a name="register-your-app"></a>Registrar la aplicación

Cuenta de Microsoft (MSA) o Azure Active Directory (AAD) se requiere autenticación para casi todas las características del SDK de Roma proyecto (la excepción que se va a las API de uso compartidas cercanas). Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).

Mediante el método de autenticación seleccionado, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/). Si no tiene una cuenta de desarrollador de Microsoft, deberá crear uno.

Al registrar una aplicación con una MSA, debería recibir una cadena de identificador de cliente. Guardar esto para su uso posterior. Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft. Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.

### <a name="add-the-sdk"></a>Agregue el SDK

Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

En el proyecto *AndroidManifest.xml* , agregue los siguientes permisos dentro de la `<manifest>` elemento (si aún no están presentes). Esto da permiso a la aplicación para conectarse a Internet y para habilitar la detección de Bluetooth en el dispositivo.

Tenga en cuenta que los permisos relacionados con el Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados. Además, `ACCESS_COARSE_LOCATION` sólo es necesario en 21 de Android SDK y versiones posteriores. 23 de Android SDK y versiones posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

A continuación, vaya a la clase o clases de actividad donde desea que la funcionalidad de dispositivos conectados a live. Importar los paquetes siguientes.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
