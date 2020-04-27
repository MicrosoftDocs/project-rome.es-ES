---
title: include file
description: include file
ms.topic: include
ms.assetid: ''
ms.localizationpriority: medium
ms.openlocfilehash: b2d1d764c4aae562a1fcafdb490db5a14522cda6
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "66755805"
---
## <a name="preliminary-setup-for-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="2e774-103">Configuración preliminar para la plataforma de dispositivos conectados y las notificaciones</span><span class="sxs-lookup"><span data-stu-id="2e774-103">Preliminary setup for the Connected Devices Platform and Notifications</span></span>

<span data-ttu-id="2e774-104">Antes de implementar la conectividad remota, debes seguir unos pasos para que la aplicación Android disponga de la funcionalidad para conectarse a dispositivos remotos, así como para enviar y recibir notificaciones.</span><span class="sxs-lookup"><span data-stu-id="2e774-104">Before implementing remote connectivity, there are a few steps you'll need to take to give your Android app the capability to connect to remote devices as well as send and receive notifications.</span></span>

### <a name="register-your-app"></a><span data-ttu-id="2e774-105">Registro de la aplicación</span><span class="sxs-lookup"><span data-stu-id="2e774-105">Register your app</span></span>

<span data-ttu-id="2e774-106">La mayoría de las características del SDK de Project Rome (a excepción de las API de Uso compartido en proximidad) necesitan la autenticación de la cuenta de Microsoft (MSA) o Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="2e774-106">Microsoft Account (MSA) or Azure Active Directory (AAD) authentication is required for almost all features of the Project Rome SDK (the exception being the nearby sharing APIs).</span></span> <span data-ttu-id="2e774-107">Si aún no tienes una cuenta MSA y deseas usarla, regístrate en [account.microsoft.com](https://account.microsoft.com/account).</span><span class="sxs-lookup"><span data-stu-id="2e774-107">If you do not already have an MSA and wish to use one, register on [account.microsoft.com](https://account.microsoft.com/account).</span></span>

> [!NOTE]
> <span data-ttu-id="2e774-108">No se admiten cuentas de Azure Active Directory (AAD) con las API de Retransmisión de dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e774-108">Azure Active Directory (AAD) accounts are not supported with the Device Relay APIs.</span></span>

<span data-ttu-id="2e774-109">A partir del método de autenticación elegido, debes registrar la aplicación con Microsoft; para ello, sigue las instrucciones del [Portal de registro de aplicaciones](https://apps.dev.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="2e774-109">Using your chosen authentication method, you must register your app with Microsoft by following the instructions on the [Application Registration Portal](https://apps.dev.microsoft.com/).</span></span> <span data-ttu-id="2e774-110">Si no tienes una cuenta de desarrollador de Microsoft, antes debes crearla.</span><span class="sxs-lookup"><span data-stu-id="2e774-110">If you do not have a Microsoft developer account, you will need to create one.</span></span>

<span data-ttu-id="2e774-111">Al registrar una aplicación con MSA, deberías recibir una cadena de id. de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e774-111">When you register an app using an MSA, you should receive a client ID string.</span></span> <span data-ttu-id="2e774-112">Guárdala para más adelante.</span><span class="sxs-lookup"><span data-stu-id="2e774-112">Save this for later.</span></span> <span data-ttu-id="2e774-113">Este dato permitirá que la aplicación acceda a los recursos de la plataforma de dispositivos conectados de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2e774-113">This will allow your app to access Microsoft's Connected Devices Platform resources.</span></span> <span data-ttu-id="2e774-114">Si usas AAD, consulta en [Bibliotecas de autenticación de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) las instrucciones sobre cómo obtener la cadena de id. de cliente.</span><span class="sxs-lookup"><span data-stu-id="2e774-114">If you're using AAD, see [Azure Active Directory Authentication Libraries](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-libraries) for instructions on getting the client ID string.</span></span>

### <a name="add-the-sdk"></a><span data-ttu-id="2e774-115">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="2e774-115">Add the SDK</span></span>

<span data-ttu-id="2e774-116">Inserta las siguientes referencias de repositorio en el archivo *build.gradle* situado en la raíz del proyecto.</span><span class="sxs-lookup"><span data-stu-id="2e774-116">Insert the following repository references into the *build.gradle* file at the root of your project.</span></span>

```Java
allprojects {
    repositories {
        jcenter()
    }
}
```
<span data-ttu-id="2e774-117">A continuación, inserta la siguiente dependencia en el archivo _build.gradle_ que se encuentra en la carpeta del proyecto.</span><span class="sxs-lookup"><span data-stu-id="2e774-117">Then, insert the following dependency into the _build.gradle_ file that is in your project folder.</span></span>

```Java
dependencies { 
    ...
    implementation 'com.microsoft.connecteddevices:connecteddevices-sdk:+'
}
```

<span data-ttu-id="2e774-118">En el archivo *AndroidManifest.xml* del proyecto, agrega los siguientes permisos dentro del elemento `<manifest>` (si no están ya incluidos).</span><span class="sxs-lookup"><span data-stu-id="2e774-118">In your project's *AndroidManifest.xml* file, add the following permissions inside the `<manifest>` element (if they are not already present).</span></span> <span data-ttu-id="2e774-119">Esto permite que la aplicación se conecte a Internet y habilite la detección de Bluetooth en el dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e774-119">This gives your app permission to connect to the Internet and to enable Bluetooth discovery on your device.</span></span>

<span data-ttu-id="2e774-120">Ten en cuenta que los permisos relacionados con Bluetooth solo son necesarios para usar la detección de Bluetooth; no se necesitan para las demás características de la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="2e774-120">Note that the Bluetooth-related permissions are only necessary for using Bluetooth discovery; they are not needed for the other features in the Connected Devices Platform.</span></span> <span data-ttu-id="2e774-121">Además, `ACCESS_COARSE_LOCATION` solo es necesario en los niveles de Android SDK 21 y posteriores.</span><span class="sxs-lookup"><span data-stu-id="2e774-121">Additionally, `ACCESS_COARSE_LOCATION` is only required on Android SDKs 21 and later.</span></span> <span data-ttu-id="2e774-122">En los niveles de Android SDK 23 y posteriores, el desarrollador también debe pedir al usuario que conceda acceso a la ubicación en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="2e774-122">On Android SDKs 23 and later, the developer must also prompt the user to grant location access at runtime.</span></span>


```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.BLUETOOTH" />
<uses-permission android:name="android.permission.BLUETOOTH_ADMIN" />
<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

<span data-ttu-id="2e774-123">A continuación, ve a las clases de actividad donde deseas incluir la funcionalidad de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="2e774-123">Next, go to the activity class(es) where you would like the Connected Devices functionality to live.</span></span> <span data-ttu-id="2e774-124">Importa los siguientes paquetes.</span><span class="sxs-lookup"><span data-stu-id="2e774-124">Import the the following packages.</span></span>

```java
import com.microsoft.connecteddevices;
import com.microsoft.connecteddevices.remotesystems;
import com.microsoft.connecteddevices.remotesystems.commanding;
```
