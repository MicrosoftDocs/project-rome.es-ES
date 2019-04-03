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
## <a name="preliminary-setup-for-the-connected-devices-platform"></a><span data-ttu-id="70b2e-103">Instalación preliminar para la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="70b2e-103">Preliminary setup for the Connected Devices Platform</span></span>

<span data-ttu-id="70b2e-104">Antes de implementar conectividad remota, hay unos pasos que deberá tomar para proporcionar la funcionalidad para conectarse a los dispositivos remotos a la aplicación Android.</span><span class="sxs-lookup"><span data-stu-id="70b2e-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices.</span></span>

### <a name="sign-in"></a><span data-ttu-id="70b2e-105">Iniciar sesión</span><span class="sxs-lookup"><span data-stu-id="70b2e-105">Sign-in</span></span>

<span data-ttu-id="70b2e-106">Se requiere autenticación de cuenta de Microsoft (MSA) o Azure Active Directory (AAD) para todas las características del SDK, excepto para el uso compartido de Nearby API.</span><span class="sxs-lookup"><span data-stu-id="70b2e-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for all features of the SDK, except for the Nearby sharing APIs.</span></span> 

<span data-ttu-id="70b2e-107">Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="70b2e-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="70b2e-108">A continuación, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/) (si no tiene una cuenta de desarrollador de Microsoft, debe crear una primera).</span><span class="sxs-lookup"><span data-stu-id="70b2e-108">Next, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/) (if you do not have a Microsoft developer account, you must create one first).</span></span> <span data-ttu-id="70b2e-109">Debería recibir una cadena de identificador de cliente de la aplicación; guardar esto para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="70b2e-109">You should receive a client ID string for your app; save this for later.</span></span> <span data-ttu-id="70b2e-110">Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="70b2e-110">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="70b2e-111">Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.</span><span class="sxs-lookup"><span data-stu-id="70b2e-111">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="70b2e-112">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="70b2e-112">Add the SDK</span></span>

<span data-ttu-id="70b2e-113">Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="70b2e-113">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
        maven { url 'https://maven.google.com' }
        maven { url 'https://projectrome.bintray.com/maven/' }
    }
}
```
<span data-ttu-id="70b2e-114">A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="70b2e-114">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:0.11.0'
}
```

<span data-ttu-id="70b2e-115">Si desea usar ProGuard en la aplicación, agregue las reglas de ProGuard de estas nuevas API.</span><span class="sxs-lookup"><span data-stu-id="70b2e-115">If you wish to use ProGuard in your app, add the ProGuard Rules for these new APIs.</span></span> <span data-ttu-id="70b2e-116">Cree un archivo llamado *proguard rules.txt* en el *aplicación* carpeta del proyecto y pegue los contenidos de [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span><span class="sxs-lookup"><span data-stu-id="70b2e-116">Create a file called *proguard-rules.txt* in the *App* folder of your project, and paste in the contents of [ProGuard_Rules_for_Android_Rome_SDK.txt](https://github.com/Microsoft/project-rome/blob/master/Android/ProGuard_Rules_for_Android_Rome_SDK.txt).</span></span>

<span data-ttu-id="70b2e-117">En el proyecto *AndroidManifest.xml* , agregue los siguientes permisos dentro de la `<manifest>` elemento (si aún no están presentes).</span><span class="sxs-lookup"><span data-stu-id="70b2e-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="70b2e-118">Esto da permiso a la aplicación para conectarse a Internet y para habilitar la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="70b2e-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

> [!NOTE]
> <span data-ttu-id="70b2e-119">Los permisos relacionados con el Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="70b2e-119">The Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="70b2e-120">Además, `ACCESS_COARSE_LOCATION` sólo es necesario en 21 de Android SDK y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="70b2e-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="70b2e-121">23 de Android SDK y versiones posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="70b2e-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>

<span data-ttu-id="70b2e-122">A continuación, vaya a la clase o clases de actividad donde desea que la funcionalidad de dispositivos conectados a live.</span><span class="sxs-lookup"><span data-stu-id="70b2e-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="70b2e-123">Importar los espacios de nombres siguientes.</span><span class="sxs-lookup"><span data-stu-id="70b2e-123">Import the the following namespaces.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.useractivities;
import com.microsoft.connecteddevices.userdata;
```
