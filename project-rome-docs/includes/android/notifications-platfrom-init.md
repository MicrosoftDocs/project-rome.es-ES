---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 9f679e13-b1b3-40f8-bd44-679e4dffc0d4
ms.localizationpriority: medium
ms.openlocfilehash: eafd435f0cd9eabc5aa121cdb5288bd0b522df60
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801804"
---
### <a name="add-the-sdk"></a>Agregue el SDK

Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.

```java
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

A continuación, vaya a la clase o clases de actividad donde desea agregar la funcionalidad de dispositivos conectados. Importar el **connecteddevices** espacios de nombres.

```java
import com.microsoft.connecteddevices.*;
```

Dependiendo de qué escenarios implementan, quizá no tenga todos los espacios de nombres. También es posible que deba agregar otros espacios de nombres nativo de Android a medida que avanza.

### <a name="initialize-the-connected-devices-platform"></a>Inicializar la plataforma de dispositivos conectados

Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación. Los pasos de inicialización deben producirse en la clase principal **onCreate** o **onResume** método, porque son necesarios antes de pueden realizar otros escenarios de dispositivos conectados. 

Debe crear una instancia del **plataforma** clase. El **plataforma** constructor toma tres parámetros: el **contexto** para la aplicación, un **NotificationProvider**y un **UserAccountProvider**.

El **NotificationProvider** parámetro sólo es necesario para determinados escenarios. En el caso de uso de notificaciones de Microsoft Graph, es necesario. Déjelo como `null` por ahora y obtenga información sobre cómo habilitar el cliente SDK para controlar las notificaciones de usuario-centric entrantes a través de canales de inserción nativa en la sección siguiente.

El **UserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada. 

Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado una cuenta de las implementaciones del proveedor para iOS y Android. Estas implementaciones, se encuentra en la [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), puede usarse para obtener el token de acceso de OAuth 2.0 y actualizar el token para la aplicación.

[!INCLUDE [auth-scopes](../auth-scopes.md)]

En el código siguiente, `mSignInHelper` referencias una **MSAAccountProvider**también inicializar a continuación. Esto proporciona la clase implementa la **UserAccountProvider** interfaz.

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

Ahora puede construir un **plataforma** instancia. Puede que desee colocar el código siguiente en una clase auxiliar independiente. 

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
En la clase principal, donde `mSignInHelper` está inicializado, agregue el código siguiente.

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

Debe apagar la plataforma cuando la aplicación cierra el primer plano.

```Java
mPlatform.shutdownAsync();
```
