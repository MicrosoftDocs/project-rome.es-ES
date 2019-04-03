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
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="8de88-103">Instalación preliminar para la plataforma de dispositivos conectados y notificaciones</span><span class="sxs-lookup"><span data-stu-id="8de88-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="8de88-104">Antes de implementar conectividad remota, hay unos pasos que deberá tomar para dar la capacidad para conectarse a dispositivos remotos, así como enviar y recibir notificaciones de la aplicación Android.</span><span class="sxs-lookup"><span data-stu-id="8de88-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="8de88-105">Registrar la aplicación</span><span class="sxs-lookup"><span data-stu-id="8de88-105">Register your app</span></span>

<span data-ttu-id="8de88-106">Cuenta de Microsoft (MSA) o Azure Active Directory (AAD) se requiere autenticación para casi todas las características del SDK de Roma proyecto (la excepción que se va a las API de uso compartidas cercanas).</span><span class="sxs-lookup"><span data-stu-id="8de88-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="8de88-107">Si aún no tiene una MSA y desea usar uno, registrar en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="8de88-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

<span data-ttu-id="8de88-108">Mediante el método de autenticación seleccionado, debe registrar la aplicación con Microsoft, siga las instrucciones de la [Portal de registro de aplicación](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="8de88-108">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="8de88-109">Si no tiene una cuenta de desarrollador de Microsoft, deberá crear uno.</span><span class="sxs-lookup"><span data-stu-id="8de88-109">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="8de88-110">Al registrar una aplicación con una MSA, debería recibir una cadena de identificador de cliente.</span><span class="sxs-lookup"><span data-stu-id="8de88-110">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="8de88-111">Guardar esto para su uso posterior.</span><span class="sxs-lookup"><span data-stu-id="8de88-111">Save this for later.</span></span> <span data-ttu-id="8de88-112">Esto permitirá que la aplicación tener acceso a los recursos de plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="8de88-112">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="8de88-113">Si usa AAD, consulte [bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) para obtener instrucciones sobre cómo obtener el cliente de cadena del identificador.</span><span class="sxs-lookup"><span data-stu-id="8de88-113">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="8de88-114">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="8de88-114">Add the SDK</span></span>

<span data-ttu-id="8de88-115">Inserte las siguientes referencias de repositorio en el *build.gradle* archivo en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="8de88-115">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="8de88-116">A continuación, inserte la siguiente dependencia en el _build.gradle_ archivo que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="8de88-116">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="8de88-117">En el proyecto *AndroidManifest.xml* , agregue los siguientes permisos dentro de la `<manifest>` elemento (si aún no están presentes).</span><span class="sxs-lookup"><span data-stu-id="8de88-117">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="8de88-118">Esto da permiso a la aplicación para conectarse a Internet y para habilitar la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8de88-118">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="8de88-119">Tenga en cuenta que los permisos relacionados con el Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="8de88-119">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="8de88-120">Además, `ACCESS_COARSE_LOCATION` sólo es necesario en 21 de Android SDK y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="8de88-120">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="8de88-121">23 de Android SDK y versiones posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="8de88-121">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="8de88-122">A continuación, vaya a la clase o clases de actividad donde desea que la funcionalidad de dispositivos conectados a live.</span><span class="sxs-lookup"><span data-stu-id="8de88-122">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="8de88-123">Importar los paquetes siguientes.</span><span class="sxs-lookup"><span data-stu-id="8de88-123">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
