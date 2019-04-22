---
title: La integración de aplicaciones para UWP con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 09f32a9869343778712449db04f74e9341fbc5a6
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801307"
---
# <a name="how-to-guide-integrating-with-ms-graph-notifications-windows-uwp"></a><span data-ttu-id="e4938-103">Guía de procedimientos: La integración con las notificaciones de MS Graph (Windows UWP)</span><span class="sxs-lookup"><span data-stu-id="e4938-103">How-To Guide: Integrating with MS Graph Notifications (Windows UWP)</span></span>

<span data-ttu-id="e4938-104">Con el SDK de cliente de Graph notificaciones en Windows, la aplicación de UWP de Windows puede realizar los pasos de registro necesarias para convertirse en un extremo de recepción que recibe notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario.</span><span class="sxs-lookup"><span data-stu-id="e4938-104">With the Graph Notifications client-side SDK on Windows, your Windows UWP app can perform the necessary registration steps to become a receiving endpoint that receives notifications published from your app server targeted at a user.</span></span> <span data-ttu-id="e4938-105">El SDK, a continuación, se usa para administrar las notificaciones en el lado cliente incluidos recibir una notificación nueva cargas ha llegado a este cliente, administrar el estado de las notificaciones y recuperar el historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="e4938-105">The SDK is then used to manage the notifications on the client side including receiving new notification payloads arrived on this client, managing the state of notifications, and retrieving notification history.</span></span> <span data-ttu-id="e4938-106">Para obtener más información acerca de las notificaciones de MS Graph y cómo permite la entrega de notificaciones humanos-centric, consulte [información general de las notificaciones de Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="e4938-106">For more information about MS Graph Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="e4938-107">Consulte la [referencia de API](api-reference-for-windows/index.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="e4938-107">See the [API reference](api-reference-for-windows/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="preliminary-setup-for-accessing-the-connected-devices-platform-in-order-to-use-graph-notifications"></a><span data-ttu-id="e4938-108">Instalación preliminar para tener acceso a la plataforma de dispositivos conectados para poder usar las notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="e4938-108">Preliminary setup for accessing the Connected Devices Platform in order to use Graph Notifications</span></span> 
<span data-ttu-id="e4938-109">Hay unos pocos pasos que debe seguir para integrarse con las notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="e4938-109">There are a few steps you must take to integrate with Graph Notifications</span></span>
* <span data-ttu-id="e4938-110">MSA o registro de aplicación AAD</span><span class="sxs-lookup"><span data-stu-id="e4938-110">MSA or AAD App Registration</span></span>
* <span data-ttu-id="e4938-111">Incorporación del centro de desarrollo para proporcionar la identidad de aplicación multiplataforma y las credenciales de la notificación de inserción</span><span class="sxs-lookup"><span data-stu-id="e4938-111">Dev Center Onboarding to Provide Cross-Platform App Identity and Push Notification Credentials</span></span>
* <span data-ttu-id="e4938-112">Agregar el SDK e inicializar la plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="e4938-112">Adding the SDK and Initializing the Connected Devices Platform</span></span>
* <span data-ttu-id="e4938-113">Asociar el servicio de notificación de plataforma de dispositivos conectados</span><span class="sxs-lookup"><span data-stu-id="e4938-113">Associate the Notification Service with Connected Devices Platform</span></span>

<span data-ttu-id="e4938-114">En primer lugar, debe completar la MSA y/o el registro de aplicación de AAD.</span><span class="sxs-lookup"><span data-stu-id="e4938-114">First, you must complete the MSA and/or AAD App Registration.</span></span> <span data-ttu-id="e4938-115">Si lo ha hecho ya, vaya a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="e4938-115">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/platform-init](../includes/windows/notifications-app-registration-onboarding.md)]
<span data-ttu-id="e4938-116">A continuación, debe incorporar con Microsoft Windows Dev Center para obtener acceso a la plataforma de dispositivos conectados con el fin de integrar con experiencias multidispositivo incluido el uso de notificaciones de gráfico.</span><span class="sxs-lookup"><span data-stu-id="e4938-116">Next, you must onboard with Microsoft Windows Dev Center to get access to the Connected Device Platform in order to integrate with cross-device experiences including use of Graph Notifications.</span></span> <span data-ttu-id="e4938-117">Si lo ha hecho ya, vaya a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="e4938-117">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [windows/notification-init](../includes/windows/notifications-dev-center-onboarding.md)]
<span data-ttu-id="e4938-118">A continuación, debe agregar el SDK de Roma del proyecto al proyecto e inicializar la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="e4938-118">Next, you must add the Project Rome SDK to your project and initialize the Connected Devices Platform.</span></span> <span data-ttu-id="e4938-119">Si lo ha hecho ya, vaya a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="e4938-119">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-platfrom-init.md)]
<span data-ttu-id="e4938-120">Por último, debe habilitar la aplicación para recibir notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="e4938-120">Lastly, you must enable your app to receive push notifications.</span></span> <span data-ttu-id="e4938-121">Si lo ha hecho ya, vaya a la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="e4938-121">If you've done this already, skip to the next section.</span></span>
[!INCLUDE [android/notification-init](../includes/android/notifications-notification-init.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="e4938-122">Inicializar un canal de notificación de Graph</span><span class="sxs-lookup"><span data-stu-id="e4938-122">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="e4938-123">En un nivel alto, el SDK permite la aplicación para suscribirse a distintos canales para recibir y administrar distintos tipos de datos de usuario: incluida las notificaciones de gráfico, las actividades del usuario y mucho más.</span><span class="sxs-lookup"><span data-stu-id="e4938-123">At a high level, the SDK allows your app to subscribe to different channels in order to receive and manage different types of User Data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="e4938-124">Estos son almacenados y sincronizados en **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="e4938-124">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="e4938-125">**UserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico.</span><span class="sxs-lookup"><span data-stu-id="e4938-125">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="e4938-126">Para integrar con notificación de Graph y comience a recibir UserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="e4938-126">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="e4938-127">Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).</span><span class="sxs-lookup"><span data-stu-id="e4938-127">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="e4938-128">Crear un UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification</span><span class="sxs-lookup"><span data-stu-id="e4938-128">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="e4938-129">Una vez que tenga un **UserNotificationChannel** referencia, necesita un **UserNotificationReader** con el fin de permitir que el SDK capturar el contenido de la notificación real del servidor.</span><span class="sxs-lookup"><span data-stu-id="e4938-129">Once you have a **UserNotificationChannel** reference, you need a **UserNotificationReader** in order to allow the SDK to fetch the actual notification content from the server.</span></span> <span data-ttu-id="e4938-130">Un UserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección UserNotification completa que se puede utilizar como modelo de vista del historial de notificaciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4938-130">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  

<span data-ttu-id="e4938-131">El código siguiente muestra los pasos necesarios para crear una instancia de un canal de notificación de usuario, crear un lector de notificación de usuario y agregar un controlador de eventos en el lector de notificación de usuario que se desencadena cuando la plataforma de dispositivos conectados se completa cada sincronización y tiene nuevos cambios a notificará.</span><span class="sxs-lookup"><span data-stu-id="e4938-131">The code below shows the steps to instantiate a user notification channel, create a user notification reader, and add an event handler on the user notification reader which gets triggered when the COnnected Device Platform completes each sync and has new changes to notify you about.</span></span> 

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

### <a name="receiving-usernotifications"></a><span data-ttu-id="e4938-132">Recepción de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="e4938-132">Receiving UserNotifications</span></span>

<span data-ttu-id="e4938-133">En la sección anterior se ve que se agrega un agente de escucha de eventos para el lector de notificación de usuario.</span><span class="sxs-lookup"><span data-stu-id="e4938-133">In the above section we see that an event listner is added to the user notification reader.</span></span> <span data-ttu-id="e4938-134">Debe implementar este agente de escucha de eventos para leer todas las nuevas notificaciones y las actualizaciones de notificación desde el lector e implementar su propia lógica de negocios para controlar cada uno de estos nuevos cambios.</span><span class="sxs-lookup"><span data-stu-id="e4938-134">You should implement this event listener to read all the new notifications and notification updates from the reader, and implement your own business logic to handle each of these new changes.</span></span> 

> [!TIP] 
> <span data-ttu-id="e4938-135">Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios.</span><span class="sxs-lookup"><span data-stu-id="e4938-135">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="e4938-136">Si actualmente usa notificación sin procesar del WNS para construir una notificación local en el centro de actividades de nivel de sistema operativo, o si usa el contenido en la notificación para actualizar alguna IU en la aplicación, esto es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="e4938-136">If you currently use WNS’s raw notification to construct a local toast notification in the OS-level Action Center, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 

<span data-ttu-id="e4938-137">El código siguiente muestra cómo se elige la aplicación de ejemplo generar una notificación del sistema local para todos los UserNotification entrante que están activos y quitar de la interfaz de usuario de notificación correspondiente en la vista de la aplicación si se elimina una notificación.</span><span class="sxs-lookup"><span data-stu-id="e4938-137">The code below shows you how the sample app chooses to raise a local toast notification for all the incoming UserNotification that are Active, and remove the corresponding notification UI in the in-app view if a notification is deleted.</span></span> 

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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="e4938-138">Actualizar el estado de un UserNotification existente</span><span class="sxs-lookup"><span data-stu-id="e4938-138">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="e4938-139">En la sección anterior, hemos mencionado que a veces un cambio UserNotification recibido a través el lector podría ser una actualización de estado en una existente UserNotification – si se está marcando como descartado o se marca como leído.</span><span class="sxs-lookup"><span data-stu-id="e4938-139">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="e4938-140">En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="e4938-140">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="e4938-141">Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio UserNotification para comenzar: desde un dispositivo diferente.</span><span class="sxs-lookup"><span data-stu-id="e4938-141">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="e4938-142">Puede elegir el momento para actualizar el estado de su UserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación se controla aún más por el usuario en cierta experiencia en la aplicación que habilitar .</span><span class="sxs-lookup"><span data-stu-id="e4938-142">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="e4938-143">Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4938-143">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="e4938-144">El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="e4938-144">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="e4938-145">El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la UserNotification correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="e4938-145">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="e4938-146">Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center.</span><span class="sxs-lookup"><span data-stu-id="e4938-146">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="e4938-147">Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario.</span><span class="sxs-lookup"><span data-stu-id="e4938-147">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="e4938-148">Clase UserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el UserNotificationReadState o la UserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="e4938-148">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="e4938-149">Por ejemplo, puede marcar UserActionState para ser activado o descartada y descartar la dinamización de ese valor para implementar universal.</span><span class="sxs-lookup"><span data-stu-id="e4938-149">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="e4938-150">Como alternativa, o al mismo tiempo puede marcar ReadState como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación.</span><span class="sxs-lookup"><span data-stu-id="e4938-150">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="e4938-151">Código siguiente fragmento de código muestra cómo marcar la UserNotificationUserActionState de una notificación como descartada.</span><span class="sxs-lookup"><span data-stu-id="e4938-151">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

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
