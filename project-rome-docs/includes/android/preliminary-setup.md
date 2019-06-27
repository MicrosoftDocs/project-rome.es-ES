---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b2d1d764c4aae562a1fcafdb490db5a14522cda6
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "66755805"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a>Configuración preliminar para la plataforma de dispositivos conectados y las notificaciones

Antes de implementar la conectividad remota, debes seguir unos pasos para que la aplicación Android disponga de la funcionalidad para conectarse a dispositivos remotos, así como para enviar y recibir notificaciones.

### <a name="register-your-app"></a>Registro de la aplicación

La mayoría de las características del SDK de Project Rome (a excepción de las API de Uso compartido en proximidad) necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD). Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).

> [!NOTE]
> No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.

A partir del método de autenticación elegido, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/). Si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla.

Al registrar una aplicación con MSA, deberías recibir una cadena de id. de cliente. Guárdala para más adelante. Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft. Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.

### <a name="add-the-sdk"></a>Incorporación del SDK

Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

En el archivo *AndroidManifest.xml* del proyecto, agrega los siguientes permisos dentro del elemento `<manifest>` (si no están ya incluidos). Esto permite que la aplicación se conecte a Internet y habilite la detección de Bluetooth en el dispositivo.

Ten en cuenta que los permisos relacionados con Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados. Además, `ACCESS_COARSE_LOCATION` solo es necesario en los niveles de Android SDK 21 y posteriores. En los niveles de Android SDK 23 y posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

A continuación, ve a las clases de actividad donde deseas incluir la funcionalidad de dispositivos conectados. Importa los siguientes paquetes.

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
