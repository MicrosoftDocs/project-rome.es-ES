### <a name="add-the-sdk"></a>Agregue el SDK

Para Windows, SDK de notificación de Graph está disponible a los desarrolladores a través de un paquete de NuGet en lugar del SDK de Windows del sistema operativo integrado con el fin de ha mejor y bajo nivel compatibilidad con programación de lanzamiento más flexible. El paquete NuGet publicado por msgraphsdkteam en nuget.org y puede encontrarse [aquí](https://www.nuget.org/profiles/msgraphsdkteam). 

Para obtener más detalles sobre incluidos y consumir paquetes de NuGet desde su aplicación para UWP, consulte estos vínculos. 
* [Usar paquetes de nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav)
* [Inicio rápido: Instalar y usar un paquete en Visual Studio](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




Dependiendo de qué escenarios implementan, quizá no tenga todos los espacios de nombres. Para las notificaciones de gráfico en concreto, será necesario el debajo de los espacios de nombres como se muestra.


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>Inicializar la plataforma de dispositivos conectados

Antes de que se pueden usar las características de dispositivos conectados, la plataforma debe inicializarse dentro de la aplicación. Los pasos de inicialización deben producirse en la clase principal **OnLaunched** o **onActivated** método, porque son necesarios antes de pueden realizar otros escenarios de dispositivos conectados. 

Debe crear una instancia del **ConnectedDevicesPlatform** clase. El **ConnectedDevicesPlatform** constructor toma tres parámetros: el **contexto** para la aplicación, un **NotificationProvider**y un  **UserAccountProvider**.

El **NotificationProvider** parámetro sólo es necesario para determinados escenarios. En el caso de uso de notificaciones de Microsoft Graph, es necesario. Déjela en blanco por ahora y descubra en la sección siguiente sobre cómo habilitar al cliente SDK para controlar las notificaciones de usuario-centric entrantes a través de canales de inserción nativa.

El **UserAccountProvider** es necesario para entregar un token de acceso de OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que la aplicación se ejecuta y token de actualización tras la expiración de una plataforma administrada. 

Con el fin de ayudar a los desarrolladores incorporar con la plataforma más fácilmente, hemos proporcionado cuenta implementaciones del proveedor de Windows en el código de ejemplo, asegúrese de comprobar **MicrosoftAccountProvider.cs** para obtener más detalles. 

A continuación, puede construir un **plataforma** instancia. 

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

Debe apagar la plataforma cuando la aplicación cierra el primer plano.

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
