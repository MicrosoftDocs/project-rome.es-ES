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
### <a name="add-the-sdk"></a><span data-ttu-id="aa7c5-103">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="aa7c5-103">Add the SDK</span></span>

<span data-ttu-id="aa7c5-104">Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="aa7c5-105">A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="aa7c5-106">Si desea usar ProGuard en la aplicación, agregue las reglas de ProGuard de estas nuevas API.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="aa7c5-107">Cree un archivo llamado *proguard rules.txt* en el *aplicación* carpeta del proyecto y pegue los contenidos de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="aa7c5-108">En el proyecto *AndroidManifest.xml* , agregue los siguientes permisos dentro de la `<manifest>` elemento (si aún no están presentes).</span><span class="sxs-lookup"><span data-stu-id="aa7c5-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="aa7c5-109">Esto da permiso a la aplicación para conectarse a Internet y para habilitar la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="aa7c5-110">Los permisos relacionados con el Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="aa7c5-111">Además, `ACCESS_COARSE_LOCATION` sólo es necesario en 21 de Android SDK y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="aa7c5-112">23 de Android SDK y versiones posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="aa7c5-113">A continuación, vaya a la clase o clases de actividad donde desea agregar la funcionalidad de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="aa7c5-114">Importar el **connecteddevices** espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="aa7c5-115">Dependiendo de qué escenarios implementan, quizá no tenga todos los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="aa7c5-116">También es posible que deba agregar otros espacios de nombres nativo de Android a medida que avanza.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="aa7c5-117">Inicializar la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="aa7c5-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="aa7c5-118">Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="aa7c5-119">Los pasos de inicialización deben producirse en la clase principal **onCreate** o **onResume** método, porque son necesarios antes de pueden realizar otros escenarios de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="aa7c5-120">Debe crear una instancia del **plataforma** clase.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="aa7c5-121">El **plataforma** constructor toma tres parámetros: el **contexto** para la aplicación, un **NotificationProvider**y un **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="aa7c5-122">El **NotificationProvider** parámetro sólo es necesario para determinados escenarios.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="aa7c5-123">En el caso de uso de notificaciones de Microsoft Graph, es necesario.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="aa7c5-124">Déjelo como `null` por ahora y obtenga información sobre cómo habilitar el cliente SDK para controlar las notificaciones de usuario-centric entrantes a través de canales de inserción nativa en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="aa7c5-125">El **UserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="aa7c5-126">Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="aa7c5-127">Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado una cuenta de las implementaciones del proveedor para iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="aa7c5-128">Estas implementaciones, se encuentra en la [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), puede usarse para obtener el token de acceso de OAuth 2.0 y actualizar el token para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="aa7c5-129">En el código siguiente, `mSignInHelper` referencias una **MSAAccountProvider**también inicializar a continuación.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="aa7c5-130">Esto proporciona la clase implementa la **UserAccountProvider** interfaz.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-130">This provided class implements the **UserAccountProvider** interface.</span></span>

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

<span data-ttu-id="aa7c5-131">Ahora puede construir un **plataforma** instancia.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="aa7c5-132">Puede que desee colocar el código siguiente en una clase auxiliar independiente.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-132">You may wish to put the following code in a separate helper class.</span></span> 

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
<span data-ttu-id="aa7c5-133">En la clase principal, donde `mSignInHelper` está inicializado, agregue el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="aa7c5-134">Debe apagar la plataforma cuando la aplicación cierra el primer plano.</span><span class="sxs-lookup"><span data-stu-id="aa7c5-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
