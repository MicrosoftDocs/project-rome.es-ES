---
title: include file
description: include file
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801804"
---
### <a name="add-the-sdk"></a>Incorporación del SDK

Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.

```java
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

A continuación, ve a las clases de actividad donde deseas agregar la funcionalidad de dispositivos conectados. Importa los espacios de nombres de **connecteddevices**.

```java
import com.microsoft.connecteddevices.*;
```

En función de los escenarios que implementes, quizá no necesites todos los espacios de nombres. También es posible que debas agregar otros espacios de nombres nativos de Android a medida que avanzas.

### <a name="initialize-the-connected-devices-platform"></a>Inicialización de la plataforma de dispositivos conectados

Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación. Los pasos de inicialización deben producirse en los métodos **onCreate** u **onResume** de la clase principal, porque son necesarios antes de que puedan tener lugar otros escenarios de dispositivos conectados. 

Debes crear una instancia de la clase **Platform**. El constructor **Platform** utiliza tres parámetros: **Context** para la aplicación, **NotificationProvider** y **UserAccountProvider**.

El parámetro **NotificationProvider** solo es necesario para determinados escenarios. Es necesario, por ejemplo, si se utilizan las notificaciones de Microsoft Graph. Déjalo como `null` por ahora y averigua cómo conseguir que el SDK de cliente controle las notificaciones centradas en el usuario entrantes a través de canales de notificaciones push nativos en la sección siguiente.

El parámetro **UserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma. 

Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para iOS y Android. Estas implementaciones, que se encuentran en el [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), pueden usarse para obtener los token de acceso y actualización OAuth 2.0 para la aplicación.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

En el código siguiente, `mSignInHelper` hace referencia a **MSAAccountProvider**, que también se inicializa a continuación. La clase proporcionada implementa la interfaz de **UserAccountProvider**.

```java
private MSAAccountProvider mSignInHelper;

// ...

// Create sign-in helper from helper lib, which does user account and access token management for us
// Takes two parameters: a client id for msa, and the Context
mSignInHelper = new MSAAccountProvider(Secrets.MSA_CLIENT_ID, getContext());

// add an event listener, which changes the button text when account state changes
mSignInHelper.addUserAccountChangedListener(new EventListener<UserAccountProvider, Void>() {
    @Override
    public void onEvent(UserAccountProvider provider, Void aVoid){
        if (mSignInHelper.isSignedIn()) {
            // update the UI indicating a user is signed in.
        }
        else
        {
            // update the UI indicating a user is not signed in.
        }
    }
});
```

Ahora puedes construir una instancia de **Platform**. Puede que quieras incluir el código siguiente en una clase auxiliar independiente. 

```java
// Platform helper class:

private static Platform sPlatform;

//...

// This is the main Platform-generating method
public static synchronized Platform getOrCreatePlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    // check whether the local platform variable is already initialized.
    Platform platform = getPlatform();

    if (platform == null) {
        // if it is not initialized, do so:
        platform = createPlatform(context, accountProvider, notificationProvider);
    }
    return platform;
}

// gets the local platform variable
public static synchronized Platform getPlatform() {
        return sPlatform;
}

// creates and returns a new Platform instance
public static synchronized Platform createPlatform(Context context, UserAccountProvider accountProvider, NotificationProvider notificationProvider) {
    sPlatform = new Platform(context, accountProvider, notificationProvider);
    return sPlatform;
}
```
En la clase principal, donde se inicializa `mSignInHelper`, agrega el código siguiente.

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

Debes apagar la plataforma cuando la aplicación sale del primer plano.

```Java
mPlatform.shutdownAsync();
```
