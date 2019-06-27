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
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="21584-103">Configuración preliminar para la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="21584-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="21584-104">Antes de implementar la conectividad remota, debes seguir unos pasos para que la aplicación Android disponga de la funcionalidad para conectarse a dispositivos remotos.</span><span class="sxs-lookup"><span data-stu-id="21584-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="21584-105">Iniciar sesión</span><span class="sxs-lookup"><span data-stu-id="21584-105">Sign-in</span></span>

<span data-ttu-id="21584-106">Todas las características del SDK necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD), excepto las API de Uso compartido en proximidad.</span><span class="sxs-lookup"><span data-stu-id="21584-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="21584-107">Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="21584-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="21584-108">A continuación debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/) (si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla).</span><span class="sxs-lookup"><span data-stu-id="21584-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="21584-109">Deberías recibir una cadena de id. de cliente para la aplicación; guárdala para más adelante.</span><span class="sxs-lookup"><span data-stu-id="21584-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="21584-110">Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="21584-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="21584-111">Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.</span><span class="sxs-lookup"><span data-stu-id="21584-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="21584-112">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="21584-112">Add the SDK</span></span>

<span data-ttu-id="21584-113">Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="21584-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="21584-114">A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="21584-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="21584-115">Si quieres usar ProGuard en la aplicación, agrega las reglas de ProGuard para estas nuevas API.</span><span class="sxs-lookup"><span data-stu-id="21584-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="21584-116">Crea un archivo llamado *proguard-rules.txt* en la carpeta *App* del proyecto y pega en él el contenido del archivo [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="21584-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="21584-117">En el archivo *AndroidManifest.xml* del proyecto, agrega los siguientes permisos dentro del elemento `<manifest>` (si no están ya incluidos).</span><span class="sxs-lookup"><span data-stu-id="21584-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="21584-118">Esto permite que la aplicación se conecte a Internet y habilite la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="21584-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="21584-119">Los permisos relacionados con Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="21584-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="21584-120">Además, `ACCESS_COARSE_LOCATION` solo es necesario en los niveles de Android SDK 21 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="21584-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="21584-121">En los niveles de Android SDK 23 y posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="21584-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="21584-122">A continuación, ve a las clases de actividad donde deseas incluir la funcionalidad de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="21584-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="21584-123">Importa los siguientes espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="21584-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
