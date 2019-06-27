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
### <a name="add-the-sdk"></a><span data-ttu-id="1f522-103">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="1f522-103">Add the SDK</span></span>

<span data-ttu-id="1f522-104">Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="1f522-104">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="1f522-105">A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="1f522-105">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="1f522-106">Si quieres usar ProGuard en la aplicación, agrega las reglas de ProGuard para estas nuevas API.</span><span class="sxs-lookup"><span data-stu-id="1f522-106">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="1f522-107">Crea un archivo llamado *proguard-rules.txt* en la carpeta *App* del proyecto y pega en él el contenido del archivo [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="1f522-107">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="1f522-108">En el archivo *AndroidManifest.xml* del proyecto, agrega los siguientes permisos dentro del elemento `<manifest>` (si no están ya incluidos).</span><span class="sxs-lookup"><span data-stu-id="1f522-108">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="1f522-109">Esto permite que la aplicación se conecte a Internet y habilite la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1f522-109">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="1f522-110">Los permisos relacionados con Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="1f522-110">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="1f522-111">Además, `ACCESS_COARSE_LOCATION` solo es necesario en los niveles de Android SDK 21 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="1f522-111">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="1f522-112">En los niveles de Android SDK 23 y posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="1f522-112">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="1f522-113">A continuación, ve a las clases de actividad donde deseas agregar la funcionalidad de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="1f522-113">Next, go to the activity class(es) where you would like to add the Connected Devices functionality.</span></span> <span data-ttu-id="1f522-114">Importa los espacios de nombres de **connecteddevices**.</span><span class="sxs-lookup"><span data-stu-id="1f522-114">Import the **connecteddevices** namespaces.</span></span>

```java
import com.microsoft.connecteddevices.*;
```

<span data-ttu-id="1f522-115">En función de los escenarios que implementes, quizá no necesites todos los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="1f522-115">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="1f522-116">También es posible que debas agregar otros espacios de nombres nativos de Android a medida que avanzas.</span><span class="sxs-lookup"><span data-stu-id="1f522-116">You may also need to add other Android-native namespaces as you progress.</span></span>

### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="1f522-117">Inicialización de la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="1f522-117">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="1f522-118">Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1f522-118">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="1f522-119">Los pasos de inicialización deben producirse en los métodos **onCreate** u **onResume** de la clase principal, porque son necesarios antes de que puedan tener lugar otros escenarios de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="1f522-119">The initialization steps should occur in your main class' **onCreate** or **onResume** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="1f522-120">Debes crear una instancia de la clase **Platform**.</span><span class="sxs-lookup"><span data-stu-id="1f522-120">You must instantiate the **Platform** class.</span></span> <span data-ttu-id="1f522-121">El constructor **Platform** utiliza tres parámetros: **Context** para la aplicación, **NotificationProvider** y **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="1f522-121">The **Platform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="1f522-122">El parámetro **NotificationProvider** solo es necesario para determinados escenarios.</span><span class="sxs-lookup"><span data-stu-id="1f522-122">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="1f522-123">Es necesario, por ejemplo, si se utilizan las notificaciones de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="1f522-123">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="1f522-124">Déjalo como `null` por ahora y averigua cómo conseguir que el SDK de cliente controle las notificaciones centradas en el usuario entrantes a través de canales de notificaciones push nativos en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="1f522-124">Leave it as `null` for now and find out how to enable the client SDK to handle incoming user-centric notifications via native push channels in next section.</span></span>

<span data-ttu-id="1f522-125">El parámetro **UserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="1f522-125">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="1f522-126">Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="1f522-126">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="1f522-127">Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para iOS y Android.</span><span class="sxs-lookup"><span data-stu-id="1f522-127">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Android and iOS.</span></span> <span data-ttu-id="1f522-128">Estas implementaciones, que se encuentran en el [ejemplo de proveedor de autenticación](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), pueden usarse para obtener los token de acceso y actualización OAuth 2.0 para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="1f522-128">These implementations, found in the [authentication provider sample](https://github.com/Microsoft/project-rome/tree/master/Android/samples/account-provider-sample), can be used to obtain the OAuth 2.0 access token and refresh token for your app.</span></span>

[!INCLUDE [auth-scopes](../auth-scopes.md)]

<span data-ttu-id="1f522-129">En el código siguiente, `mSignInHelper` hace referencia a **MSAAccountProvider**, que también se inicializa a continuación.</span><span class="sxs-lookup"><span data-stu-id="1f522-129">In the code below, `mSignInHelper` references an **MSAAccountProvider**, also initialized below.</span></span> <span data-ttu-id="1f522-130">La clase proporcionada implementa la interfaz de **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="1f522-130">This provided class implements the **UserAccountProvider** interface.</span></span>

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

<span data-ttu-id="1f522-131">Ahora puedes construir una instancia de **Platform**.</span><span class="sxs-lookup"><span data-stu-id="1f522-131">Now you can construct a **Platform** instance.</span></span> <span data-ttu-id="1f522-132">Puede que quieras incluir el código siguiente en una clase auxiliar independiente.</span><span class="sxs-lookup"><span data-stu-id="1f522-132">You may wish to put the following code in a separate helper class.</span></span> 

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
<span data-ttu-id="1f522-133">En la clase principal, donde se inicializa `mSignInHelper`, agrega el código siguiente.</span><span class="sxs-lookup"><span data-stu-id="1f522-133">In your main class, where `mSignInHelper` is initialized, add the following code.</span></span>

```java
private Platform mPlatform;

//...

mPlatform = PlatformHelperClass.getOrCreatePlatform(this, mSignInHelper, null);
```

<span data-ttu-id="1f522-134">Debes apagar la plataforma cuando la aplicación sale del primer plano.</span><span class="sxs-lookup"><span data-stu-id="1f522-134">You should shut down the platform when your app exits the foreground.</span></span>

```Java
mPlatform.shutdownAsync();
```
