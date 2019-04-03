---
title: La integración de aplicaciones para UWP con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909527"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a>Guía de procedimientos: La integración con las notificaciones de MS Graph (Windows UWP)

Con el SDK de cliente de Graph notificaciones en Windows, la aplicación de UWP de Windows puede realizar los pasos de registro necesarias para convertirse en un extremo de recepción que recibe notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario. El SDK, a continuación, se usa para administrar las notificaciones en el lado cliente incluidos recibir una notificación nueva cargas ha llegado a este cliente, administrar el estado de las notificaciones y recuperar el historial de notificaciones. Para obtener más información acerca de las notificaciones de MS Graph y cómo permite la entrega de notificaciones humanos-centric, consulte [información general de las notificaciones de Microsoft Graph](index.md)

Consulte la [referencia de API](api-reference-for-windows/index.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a>Instalación preliminar para tener acceso a la plataforma de dispositivos conectados para poder usar las notificaciones de Graph 
Hay unos pocos pasos que debe seguir para integrarse con las notificaciones de Graph
* MSA o registro de aplicación AAD
* Incorporación del centro de desarrollo para proporcionar la identidad de aplicación multiplataforma y las credenciales de la notificación de inserción
* Agregar el SDK e inicializar la plataforma de dispositivos conectados
* Asociar el servicio de notificación de plataforma de dispositivos conectados

En primer lugar, debe completar la MSA y/o el registro de aplicación de AAD. Si lo ha hecho ya, vaya a la sección siguiente.
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
A continuación, debe incorporar con Microsoft Windows Dev Center para obtener acceso a la plataforma de dispositivos conectados con el fin de integrar con experiencias multidispositivo incluido el uso de notificaciones de gráfico. Si lo ha hecho ya, vaya a la sección siguiente.
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
A continuación, debe agregar el SDK de Roma del proyecto al proyecto e inicializar la plataforma de dispositivos conectados. Si lo ha hecho ya, vaya a la sección siguiente.
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
Por último, debe habilitar la aplicación para recibir notificaciones de inserción. Si lo ha hecho ya, vaya a la sección siguiente.
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a>Inicializar un canal de notificación de Graph
En un nivel alto, el SDK permite la aplicación para suscribirse a distintos canales para recibir y administrar distintos tipos de datos de usuario: incluida las notificaciones de gráfico, las actividades del usuario y mucho más. Estos son almacenados y sincronizados en **UserDataFeed**. **UserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico. Para integrar con notificación de Graph y comience a recibir UserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **UserNotificationChannel**. Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma). 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Crear un UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification
Una vez que tenga un **UserNotificationChannel** referencia, necesita un **UserNotificationReader** con el fin de permitir que el SDK capturar el contenido de la notificación real del servidor. Un UserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección UserNotification completa que se puede utilizar como modelo de vista del historial de notificaciones del usuario.  

El código siguiente muestra los pasos necesarios para crear una instancia de un canal de notificación de usuario, crear un lector de notificación de usuario y agregar un controlador de eventos en el lector de notificación de usuario que se desencadena cuando la plataforma de dispositivos conectados se completa cada sincronización y tiene nuevos cambios a notificará. 

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

En la sección anterior se ve que se agrega un agente de escucha de eventos para el lector de notificación de usuario. Debe implementar este agente de escucha de eventos para leer todas las nuevas notificaciones y las actualizaciones de notificación desde el lector e implementar su propia lógica de negocios para controlar cada uno de estos nuevos cambios. 

> [!TIP] 
> Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios. Si actualmente usa notificación sin procesar del WNS para construir una notificación local en el centro de actividades de nivel de sistema operativo, o si usa el contenido en la notificación para actualizar alguna IU en la aplicación, esto es el lugar para hacerlo. 

El código siguiente muestra cómo se elige la aplicación de ejemplo generar una notificación del sistema local para todos los UserNotification entrante que están activos y quitar de la interfaz de usuario de notificación correspondiente en la vista de la aplicación si se elimina una notificación. 

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
## <a name="update-the-state-of-an-existing-usernotification"></a>Actualizar el estado de un UserNotification existente
En la sección anterior, hemos mencionado que a veces un cambio UserNotification recibido a través el lector podría ser una actualización de estado en una existente UserNotification – si se está marcando como descartado o se marca como leído. En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto. Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio UserNotification para comenzar: desde un dispositivo diferente. Puede elegir el momento para actualizar el estado de su UserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación se controla aún más por el usuario en cierta experiencia en la aplicación que habilitar . Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente. El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la UserNotification correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario. Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center. Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario. 

> [!TIP] 
> Clase UserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el UserNotificationReadState o la UserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puede marcar UserActionState para ser activado o descartada y descartar la dinamización de ese valor para implementar universal. Como alternativa, o al mismo tiempo puede marcar ReadState como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación. Código siguiente fragmento de código muestra cómo marcar la UserNotificationUserActionState de una notificación como descartada.

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
