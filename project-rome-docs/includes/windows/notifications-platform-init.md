---
ms.openlocfilehash: dfe29b92cbab51382f4440b4929c2082cfb9b062
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "58909697"
---
### <a name="add-the-sdk"></a>Incorporación del SDK

En Windows, el SDK de Notificaciones de Graph está disponible para los desarrolladores a través de un paquete NuGet y no a través del SDK del SO Windows integrado, con el fin de conseguir una mayor compatibilidad de bajo nivel y una programación de lanzamiento más flexible. El paquete NuGet se publica en nuget.org a nombre de msgraphsdkteam y puede encontrarse [aquí](https://www.nuget.org/profiles/msgraphsdkteam). 

Para obtener más información sobre la inclusión y el consumo de paquetes NuGet desde la aplicación para UWP, consulta estos vínculos. 
* [Use packages from nuget.org](https://docs.microsoft.com/en-us/azure/devops/artifacts/nuget/upstream-sources?view=vsts&tabs=new-nav) (Uso de paquetes de nuget.org)
* [Inicio rápido: Instalar y usar un paquete en Visual Studio](https://docs.microsoft.com/en-us/nuget/quickstart/install-and-use-a-package-in-visual-studio)




En función de los escenarios que implementes, quizá no necesites todos los espacios de nombres. Concretamente, para las notificaciones de Graph, necesitarás los siguientes espacios de nombres, tal como se muestra.


```C#
using Microsoft.ConnectedDevices.Core;
using Microsoft.ConnectedDevices.UserData;
using Microsoft.ConnectedDevices.UserNotifications;

```


### <a name="initialize-the-connected-devices-platform"></a>Inicialización de la plataforma de dispositivos conectados

Para usar las características de dispositivos conectados, debes inicializar la plataforma dentro de la aplicación. Los pasos de inicialización deben producirse en los métodos **onLaunched** u **onActivated** de la clase principal, porque son necesarios antes de que puedan tener lugar otros escenarios de dispositivos conectados. 

Debes crear una instancia de la clase **ConnectedDevicesPlatform**. El constructor **ConnectedDevicesPlatform** utiliza tres parámetros: **Context** para la aplicación, **NotificationProvider** y **UserAccountProvider**.

El parámetro **NotificationProvider** solo es necesario para determinados escenarios. Es necesario, por ejemplo, si se utilizan las notificaciones de Microsoft Graph. Déjalo vacío por ahora y averigua en la siguiente sección cómo conseguir que el SDK de cliente controle las notificaciones centradas en el usuario entrantes a través de canales de notificaciones push nativos.

El parámetro **UserAccountProvider** es necesario para entregar un token de acceso OAuth 2.0 para el acceso del usuario actual a la plataforma de dispositivos conectados. Se le llamará la primera vez que se ejecute la aplicación y tras la expiración de un token de actualización administrado por la plataforma. 

Para ayudar a que los desarrolladores se incorporen a la plataforma más fácilmente, hemos incluido implementaciones de proveedores de cuentas para Windows en el código de ejemplo; asegúrate de comprobar el archivo **MicrosoftAccountProvider.cs** para obtener más información. 

Ahora puedes construir una instancia de **Platform**. 

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

Debes apagar la plataforma cuando la aplicación sale del primer plano.

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
