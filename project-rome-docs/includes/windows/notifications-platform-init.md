---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909697"
---
### <a name="add-the-sdk"></a><span data-ttu-id="3751f-101">Incorporación del SDK</span><span class="sxs-lookup"><span data-stu-id="3751f-101">Add the SDK</span></span>

<span data-ttu-id="3751f-102">En Windows, el SDK de Notificaciones de Graph está disponible para los desarrolladores a través de un paquete NuGet y no a través del SDK del SO Windows integrado, con el fin de conseguir una mayor compatibilidad de bajo nivel y una programación de lanzamiento más flexible.</span><span class="sxs-lookup"><span data-stu-id="3751f-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="3751f-103">El paquete NuGet se publica en nuget.org a nombre de msgraphsdkteam y puede encontrarse [aquí](https://www.nuget.org/profiles/msgraphsdkteam).</span><span class="sxs-lookup"><span data-stu-id="3751f-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="3751f-104">Para obtener más información sobre la inclusión y el consumo de paquetes NuGet desde la aplicación para UWP, consulta estos vínculos.</span><span class="sxs-lookup"><span data-stu-id="3751f-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* <span data-ttu-id="3751f-105">[Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav) (Uso de paquetes de nuget.org)</span><span class="sxs-lookup"><span data-stu-id="3751f-105">[Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)</span></span>
* [<span data-ttu-id="3751f-106">Inicio rápido: Instalar y usar un paquete en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3751f-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="3751f-107">En función de los escenarios que implementes, quizá no necesites todos los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="3751f-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="3751f-108">Concretamente, para las notificaciones de Graph, necesitarás los siguientes espacios de nombres, tal como se muestra.</span><span class="sxs-lookup"><span data-stu-id="3751f-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="3751f-109">Inicialización de la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="3751f-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="3751f-110">Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3751f-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="3751f-111">Los pasos de inicialización deben producirse en los métodos **onLaunched** u **onActivated** de la clase principal, porque son necesarios antes de que puedan tener lugar otros escenarios de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="3751f-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="3751f-112">Debes crear una instancia de la clase **ConnectedDevicesPlatform**.</span><span class="sxs-lookup"><span data-stu-id="3751f-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="3751f-113">El constructor **ConnectedDevicesPlatform** utiliza tres parámetros: **Context** para la aplicación, **NotificationProvider** y **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="3751f-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="3751f-114">El parámetro **NotificationProvider** solo es necesario para determinados escenarios.</span><span class="sxs-lookup"><span data-stu-id="3751f-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="3751f-115">Es necesario, por ejemplo, si se utilizan las notificaciones de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="3751f-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="3751f-116">Déjalo vacío por ahora y averigua en la siguiente sección cómo conseguir que el SDK de cliente controle las notificaciones centradas en el usuario entrantes a través de canales de notificaciones push nativos.</span><span class="sxs-lookup"><span data-stu-id="3751f-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="3751f-117">El parámetro **UserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="3751f-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="3751f-118">Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma.</span><span class="sxs-lookup"><span data-stu-id="3751f-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="3751f-119">Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para Windows en el código de ejemplo; asegúrate de comprobar el archivo **MicrosoftAccountProvider.cs** para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="3751f-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="3751f-120">Ahora puedes construir una instancia de **Platform**.</span><span class="sxs-lookup"><span data-stu-id="3751f-120">Then you can construct a **Platform** instance.</span></span> 

```C#

public async Task InstantiatePlatform()
{
    var account = m_accoutProvider.SignedInAccount;

    if (m_feed == null)
    {
        await Task.Run(() =>
        {
            lock (this)
            {
                if (m_feed == null)
                {
                    m_platform = new ConnectedDevicesPlatform(m_accoutProvider, this);


                }
            }
        });
    }
}

```

<span data-ttu-id="3751f-121">Debes apagar la plataforma cuando la aplicación sale del primer plano.</span><span class="sxs-lookup"><span data-stu-id="3751f-121">You should shut down the platform when your app exits the foreground.</span></span>

```C#

public async void Reset()
{
    if (m_platform != null)
    {
        await m_platform.ShutdownAsync();
        m_platform = null;
        m_feed = null;
        m_newNotifications.Clear();
        m_historicalNotifications.Clear();
    }
}

```
