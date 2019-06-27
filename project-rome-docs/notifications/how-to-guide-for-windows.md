---
title: Integración de aplicaciones para UWP con las notificaciones de Graph
description: Procedimiento para realizar los pasos de registro necesarios para convertirte en un punto de conexión de recepción de notificaciones publicadas desde tu servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801307"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>Guía de procedimientos: Integración con las notificaciones de MS Graph (Windows UWP)

Con el SDK del cliente de notificaciones de Graph en Windows, tu aplicación para Windows UWP puede realizar los pasos de registro necesarios para convertirse en un punto de conexión receptor que reciba notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario. A continuación, el SDK se utiliza para administrar las notificaciones en el lado cliente, incluidas la recepción de nuevas cargas útiles de la notificación llegadas a este cliente, la administración del estado de las notificaciones y la recuperación del historial de notificaciones. Para obtener más información acerca de las notificaciones de MS Graph y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).

Consulta en la página de [referencia de API](api-reference-for-windows/index.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>Configuración preliminar para acceder a la plataforma de dispositivos conectados con el fin de utilizar las notificaciones de Graph 
Hay unos pocos pasos que debes seguir para la integración con las notificaciones de Graph
* Registro de la aplicación con MSA o AAD
* Incorporación del Centro de desarrollo para proporcionar la identidad de aplicación multiplataforma y las credenciales para las notificaciones push
* Incorporación del SDK e inicialización de la plataforma de dispositivos conectados
* Asociación del servicio de notificación a la plataforma de dispositivos conectados

En primer lugar, debes completar el registro de la aplicación con MSA o AAD. Si lo has hecho ya, ve a la sección siguiente.
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
A continuación, debes incorporar el Centro de desarrollo de Microsoft Windows para obtener acceso a la plataforma de dispositivos conectados con el fin de integrar experiencias multidispositivo, incluido el uso de notificaciones de Graph. Si lo has hecho ya, ve a la sección siguiente.
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
A continuación, debes agregar el SDK de Project Rome al proyecto e inicializar la plataforma de dispositivos conectados. Si lo has hecho ya, ve a la sección siguiente.
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
Por último, debes habilitar la aplicación para que reciba notificaciones push. Si lo has hecho ya, ve a la sección siguiente.
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>Inicialización de un canal de notificaciones de Graph
En un nivel alto, el SDK permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras. Todos ellos se almacenan y sincronizan en **UserDataFeed**. **UserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph. Para la integración con las notificaciones de Graph y comenzar a recibir la UserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **UserNotificationChannel**. Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma). 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Creación de una clase UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification.
Una vez que tengas una referencia a **UserNotificationChannel**, necesitarás una clase **UserNotificationReader** para que el SDK pueda obtener del servidor el contenido real de la notificación. En este caso, una clase UserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de UserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.  

El siguiente código muestra los pasos para crear una instancia de un canal de notificaciones de usuario, crear un lector de notificaciones de usuario y agregar un controlador de eventos en el lector de notificaciones de usuario que se activa cuando la plataforma de dispositivos conectados completa cada sincronización y tiene nuevos cambios que notificarte. 

```C#

public async Task SetupChannel()
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

                    Logger.Instance.LogMessage($"Create feed for {account.Id} {account.Type}");
                    m_feed = new UserDataFeed(account, m_platform, "graphnotifications.sample.windows.com");
                    m_feed.SyncStatusChanged += Feed_SyncStatusChanged;
                    m_feed.AddSyncScopes(new List<IUserDataFeedSyncScope>
                    {
                        UserNotificationChannel.SyncScope
                    });

                    m_channel = new UserNotificationChannel(m_feed);
                    m_reader = m_channel.CreateReader();
                    m_reader.DataChanged += Reader_DataChanged;
                }
            }
        });
    }
}

```

### <a name="receiving-usernotifications"></a>Recepción de UserNotifications

En la sección anterior se ve que se agrega una escucha de eventos al lector de notificaciones de usuario. Debes implementar esta escucha de eventos para leer todas las notificaciones nuevas y las actualizaciones de notificaciones del lector, e implementar tu propia lógica de negocio para controlar cada uno de estos nuevos cambios. 

> [!TIP] 
> En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios. Si utilizas la notificación sin procesar de WNS para crear una notificación del sistema local en el centro de actividades a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo. 

El código siguiente muestra cómo la aplicación de ejemplo elige generar una notificación del sistema local para todas las notificaciones de usuario (UserNotification) entrantes que están activas y quitar la interfaz de usuario de notificaciones correspondiente en la vista de la aplicación si se elimina una notificación. 

```C#

private void Reader_DataChanged(UserNotificationReader sender, object args)
{
    ReadNotifications(sender, true);
}

private async void ReadNotifications(UserNotificationReader reader, bool showToast)
{
    var notifications = await reader.ReadBatchAsync(UInt32.MaxValue);

    foreach (var notification in notifications)
    {

        if (notification.Status == UserNotificationStatus.Active)
        {
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            if (notification.UserActionState == UserNotificationUserActionState.NoInteraction)
            {
                // new notification, show this to user using the Windows local toast notification APIs
                m_newNotifications.Add(notification);
                if (!string.IsNullOrEmpty(notification.Content) && showToast)
                {
                    ShowToastNotification(BuildToastNotification(notification.Id, notification.Content));
                }
            }

            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.Insert(0, notification);
        }
        else
        {
            // Existing notification is marked as deleted, remove from display
            m_newNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            m_historicalNotifications.RemoveAll((n) => { return (n.Id == notification.Id); });
            RemoveToastNotification(notification.Id);
        }
    }
}

```
## <a name="update-the-state-of-an-existing-usernotification"></a>Actualización del estado de una clase UserNotification existente
En la sección anterior se mencionó que a veces un cambio en UserNotification recibido a través de la escucha puede ser una actualización de estado de una UserNotification existente, independientemente de si está marcada como descartada o como leída. En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto. Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de UserNotification desde otro dispositivo. Puedes elegir la hora para actualizar el estado de tus UserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites. Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente. El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la UserNotification correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario. Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo. Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario. 

> [!TIP] 
> Actualmente, la clase UserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar UserNotificationReadState o UserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puedes marcar UserActionState para que esté activada o descartada y basarte en ese valor para implementar el descarte universal. Si lo prefieres, o al mismo tiempo, puedes marcar ReadState como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación. El fragmento de código siguiente muestra cómo marcar el elemento UserNotificationUserActionState de una notificación como desestimado.

```C#
public async void Dismiss(string id)
{
    var notification = m_newNotifications.Find((n) => { return (n.Id == id); });
    if (notification != null)
    {
        notification.UserActionState = UserNotificationUserActionState.Dismissed;
        await notification.SaveAsync();
    }
}

```
