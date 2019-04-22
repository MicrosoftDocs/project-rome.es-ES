### <a name="add-the-sdk"></a><span data-ttu-id="7e9ba-101">Agregue el SDK</span><span class="sxs-lookup"><span data-stu-id="7e9ba-101">Add the SDK</span></span>

<span data-ttu-id="7e9ba-102">Para Windows, SDK de notificación de Graph está disponible a los desarrolladores a través de un paquete de NuGet en lugar del SDK de Windows del sistema operativo integrado con el fin de ha mejor y bajo nivel compatibilidad con programación de lanzamiento más flexible.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-102">For Windows, Graph Notification SDK is made available to developers through a NuGet package instead of built-in OS Windows SDK in order to have better down-level support and more flexible release schedule.</span></span> <span data-ttu-id="7e9ba-103">El paquete NuGet publicado por msgraphsdkteam en nuget.org y puede encontrarse [aquí](https://www.nuget.org/profiles/msgraphsdkteam).</span><span class="sxs-lookup"><span data-stu-id="7e9ba-103">The NuGet package is published by msgraphsdkteam on nuget.org and can be found [here](https://www.nuget.org/profiles/msgraphsdkteam).</span></span> 

<span data-ttu-id="7e9ba-104">Para obtener más detalles sobre incluidos y consumir paquetes de NuGet desde su aplicación para UWP, consulte estos vínculos.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-104">For more details on including and consuming NuGet packages from your UWP app, please see these links.</span></span> 
* [<span data-ttu-id="7e9ba-105">Usar paquetes de nuget.org</span><span class="sxs-lookup"><span data-stu-id="7e9ba-105">Use packages from nuget.org</span></span>](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [<span data-ttu-id="7e9ba-106">Inicio rápido: Instalar y usar un paquete en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e9ba-106">Quickstart: Install and use a package in Visual Studio</span></span>](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




<span data-ttu-id="7e9ba-107">Dependiendo de qué escenarios implementan, quizá no tenga todos los espacios de nombres.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-107">Depending on which scenarios you implement, you many not need all of the namespaces.</span></span> <span data-ttu-id="7e9ba-108">Para las notificaciones de gráfico en concreto, será necesario el debajo de los espacios de nombres como se muestra.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-108">For Graph Notifications specifically, you will need the below namespaces as shown.</span></span>


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a><span data-ttu-id="7e9ba-109">Inicializar la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="7e9ba-109">Initialize the Connected Devices Platform</span></span>

<span data-ttu-id="7e9ba-110">Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-110">Before any Connected Devices features can be used, the platform must be initialized within your app.</span></span> <span data-ttu-id="7e9ba-111">Los pasos de inicialización deben producirse en la clase principal **OnLaunched** o **onActivated** método, porque son necesarios antes de pueden realizar otros escenarios de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-111">The initialization steps should occur in your main class' **OnLaunched** or **onActivated** method, because they are required before other Connected Devices scenarios can take place.</span></span> 

<span data-ttu-id="7e9ba-112">Debe crear una instancia del **ConnectedDevicesPlatform** clase.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-112">You must instantiate the **ConnectedDevicesPlatform** class.</span></span> <span data-ttu-id="7e9ba-113">El **ConnectedDevicesPlatform** constructor toma tres parámetros: el **contexto** para la aplicación, un **NotificationProvider**y un  **UserAccountProvider**.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-113">The **ConnectedDevicesPlatform** constructor takes three parameters: the **Context** for the app, a **NotificationProvider**, and a **UserAccountProvider**.</span></span>

<span data-ttu-id="7e9ba-114">El **NotificationProvider** parámetro sólo es necesario para determinados escenarios.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-114">The **NotificationProvider** parameter is only needed for certain scenarios.</span></span> <span data-ttu-id="7e9ba-115">En el caso de uso de notificaciones de Microsoft Graph, es necesario.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-115">In the case of using Microsoft Graph Notifications, it is required.</span></span> <span data-ttu-id="7e9ba-116">Déjela en blanco por ahora y descubra en la sección siguiente sobre cómo habilitar al cliente SDK para controlar las notificaciones de usuario-centric entrantes a través de canales de inserción nativa.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-116">Leave it empty for now and find out in next section on how to enable the client SDK to handle incoming user-centric notifications via native push channels.</span></span>

<span data-ttu-id="7e9ba-117">El **UserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-117">The **UserAccountProvider** is needed to deliver an OAuth 2.0 access token for the current user's access to the Connected Devices Platform.</span></span> <span data-ttu-id="7e9ba-118">Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-118">It will be called the first time the app is run and upon the expiration of a platform-managed refresh token.</span></span> 

<span data-ttu-id="7e9ba-119">Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado cuenta implementaciones del proveedor de Windows en el código de ejemplo, asegúrese de comprobar **MicrosoftAccountProvider.cs** para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-119">In order to help developers onboard with the platform more easily, we have provided account provider implementations for Windows in sample code, please make sure to check **MicrosoftAccountProvider.cs** for more details.</span></span> 

<span data-ttu-id="7e9ba-120">A continuación, puede construir un **plataforma** instancia.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-120">Then you can construct a **Platform** instance.</span></span> 

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

<span data-ttu-id="7e9ba-121">Debe apagar la plataforma cuando la aplicación cierra el primer plano.</span><span class="sxs-lookup"><span data-stu-id="7e9ba-121">You should shut down the platform when your app exits the foreground.</span></span>

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
