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
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="5bdf8-103">Guía de procedimientos: Integración con las notificaciones de MS Graph (Windows UWP)</span><span class="sxs-lookup"><span data-stu-id="5bdf8-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="5bdf8-104">Con el SDK del cliente de notificaciones de Graph en Windows, tu aplicación para Windows UWP puede realizar los pasos de registro necesarios para convertirse en un punto de conexión receptor que reciba notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="5bdf8-105">A continuación, el SDK se utiliza para administrar las notificaciones en el lado cliente, incluidas la recepción de nuevas cargas útiles de la notificación llegadas a este cliente, la administración del estado de las notificaciones y la recuperación del historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="5bdf8-106">Para obtener más información acerca de las notificaciones de MS Graph y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="5bdf8-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="5bdf8-107">Consulta en la página de [referencia de API](api-reference-for-windows/index.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="5bdf8-108">Configuración preliminar para acceder a la plataforma de dispositivos conectados con el fin de utilizar las notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="5bdf8-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="5bdf8-109">Hay unos pocos pasos que debes seguir para la integración con las notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="5bdf8-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="5bdf8-110">Registro de la aplicación con MSA o AAD</span><span class="sxs-lookup"><span data-stu-id="5bdf8-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="5bdf8-111">Incorporación del Centro de desarrollo para proporcionar la identidad de aplicación multiplataforma y las credenciales para las notificaciones push</span><span class="sxs-lookup"><span data-stu-id="5bdf8-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="5bdf8-112">Incorporación del SDK e inicialización de la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="5bdf8-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="5bdf8-113">Asociación del servicio de notificación a la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="5bdf8-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="5bdf8-114">En primer lugar, debes completar el registro de la aplicación con MSA o AAD.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="5bdf8-115">Si lo has hecho ya, ve a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="5bdf8-116">A continuación, debes incorporar el Centro de desarrollo de Microsoft Windows para obtener acceso a la plataforma de dispositivos conectados con el fin de integrar experiencias multidispositivo, incluido el uso de notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="5bdf8-117">Si lo has hecho ya, ve a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="5bdf8-118">A continuación, debes agregar el SDK de Project Rome al proyecto e inicializar la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="5bdf8-119">Si lo has hecho ya, ve a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="5bdf8-120">Por último, debes habilitar la aplicación para que reciba notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="5bdf8-121">Si lo has hecho ya, ve a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="5bdf8-122">Inicialización de un canal de notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="5bdf8-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="5bdf8-123">En un nivel alto, el SDK permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="5bdf8-124">Todos ellos se almacenan y sincronizan en **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="5bdf8-125">**UserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="5bdf8-126">Para la integración con las notificaciones de Graph y comenzar a recibir la UserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="5bdf8-127">Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).</span><span class="sxs-lookup"><span data-stu-id="5bdf8-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="5bdf8-128">Creación de una clase UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="5bdf8-129">Una vez que tengas una referencia a **UserNotificationChannel**, necesitarás una clase **UserNotificationReader** para que el SDK pueda obtener del servidor el contenido real de la notificación.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="5bdf8-130">En este caso, una clase UserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de UserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="5bdf8-131">El siguiente código muestra los pasos para crear una instancia de un canal de notificaciones de usuario, crear un lector de notificaciones de usuario y agregar un controlador de eventos en el lector de notificaciones de usuario que se activa cuando la plataforma de dispositivos conectados completa cada sincronización y tiene nuevos cambios que notificarte.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

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

### <a name="receiving-usernotifications"></a><span data-ttu-id="5bdf8-132">Recepción de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="5bdf8-132">Receiving UserNotifications</span></span>

<span data-ttu-id="5bdf8-133">En la sección anterior se ve que se agrega una escucha de eventos al lector de notificaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="5bdf8-134">Debes implementar esta escucha de eventos para leer todas las notificaciones nuevas y las actualizaciones de notificaciones del lector, e implementar tu propia lógica de negocio para controlar cada uno de estos nuevos cambios.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="5bdf8-135">En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="5bdf8-136">Si utilizas la notificación sin procesar de WNS para crear una notificación del sistema local en el centro de actividades a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="5bdf8-137">El código siguiente muestra cómo la aplicación de ejemplo elige generar una notificación del sistema local para todas las notificaciones de usuario (UserNotification) entrantes que están activas y quitar la interfaz de usuario de notificaciones correspondiente en la vista de la aplicación si se elimina una notificación.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="5bdf8-138">Actualización del estado de una clase UserNotification existente</span><span class="sxs-lookup"><span data-stu-id="5bdf8-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="5bdf8-139">En la sección anterior se mencionó que a veces un cambio en UserNotification recibido a través de la escucha puede ser una actualización de estado de una UserNotification existente, independientemente de si está marcada como descartada o como leída.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="5bdf8-140">En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="5bdf8-141">Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de UserNotification desde otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="5bdf8-142">Puedes elegir la hora para actualizar el estado de tus UserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="5bdf8-143">Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="5bdf8-144">El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="5bdf8-145">El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la UserNotification correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="5bdf8-146">Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="5bdf8-147">Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="5bdf8-148">Actualmente, la clase UserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar UserNotificationReadState o UserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="5bdf8-149">Por ejemplo, puedes marcar UserActionState para que esté activada o descartada y basarte en ese valor para implementar el descarte universal.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="5bdf8-150">Si lo prefieres, o al mismo tiempo, puedes marcar ReadState como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="5bdf8-151">El fragmento de código siguiente muestra cómo marcar el elemento UserNotificationUserActionState de una notificación como desestimado.</span><span class="sxs-lookup"><span data-stu-id="5bdf8-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

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
