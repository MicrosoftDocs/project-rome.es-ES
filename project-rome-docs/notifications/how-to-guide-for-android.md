---
title: La integración de aplicaciones Android con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801207"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="a6f58-103">Guía de procedimientos: La integración con Graph notificaciones (Android)</span><span class="sxs-lookup"><span data-stu-id="a6f58-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="a6f58-104">Las notificaciones de Graph habilite la aplicación enviar y administrar las notificaciones de destinatarios de usuario en varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="a6f58-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="a6f58-105">Con el SDK de cliente de Roma del proyecto en Android, puede registrar la aplicación Android para recibir notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario que inició sesión.</span><span class="sxs-lookup"><span data-stu-id="a6f58-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="a6f58-106">El SDK permite al cliente de aplicación recibir nuevas cargas de notificación entrante, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="a6f58-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="a6f58-107">Para obtener más información acerca de las notificaciones y cómo habilita la entrega de notificación centrado en humanos, consulte [información general de las notificaciones de Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="a6f58-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="a6f58-108">Todas las características en el SDK de Roma proyecto, las notificaciones de includng gráfico y mucho más, se basan en una plataforma subyacente que se llama a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="a6f58-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="a6f58-109">Esta guía está diseñada para guiarle por los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y explicar cómo usar las API del SDK para implementar notificaciones de Graph-características específicas.</span><span class="sxs-lookup"><span data-stu-id="a6f58-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="a6f58-110">Consulte la [referencia de API](api-reference-for-android.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="a6f58-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="a6f58-111">Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="a6f58-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="a6f58-112">Inicializar un canal de notificación de Graph</span><span class="sxs-lookup"><span data-stu-id="a6f58-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="a6f58-113">El SDK de proyecto Roma permite la aplicación para suscribirse a distintos canales para recibir y administrar varios tipos de datos de usuario: incluidas las notificaciones de gráfico, las actividades del usuario y mucho más.</span><span class="sxs-lookup"><span data-stu-id="a6f58-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="a6f58-114">Estos son almacenados y sincronizados en **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="a6f58-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="a6f58-115">**UserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico.</span><span class="sxs-lookup"><span data-stu-id="a6f58-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="a6f58-116">Para integrar con notificación de Graph y comience a recibir UserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="a6f58-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="a6f58-117">Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).</span><span class="sxs-lookup"><span data-stu-id="a6f58-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="a6f58-118">Los siguientes métodos de inicializan un **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="a6f58-118">The following methods initialize a **UserNotificationChannel**.</span></span>

```Java
private UserNotificationChannel mNotificationChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserNotificationFeed.
 */
public void initializeUserNotificationFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserNotificationChannel.getSyncScope() };

    // Get a reference to the UserDataFeed. This method is defined below
    mUserDataFeed = getUserDataFeed(scopes, new EventListener<UserDataFeed, Void>() {
        @Override
        public void onEvent(UserDataFeed userDataFeed, Void aVoid) {
            if (userDataFeed.getSyncStatus() == UserDataSyncStatus.SYNCHRONIZED) {
                // log synchronized.
            } else {
                // log synchronization not completed.
            }
        }
    });

    // this method is defined below
    mNotificationChannel = getUserNotificationChannel();
}

// instantiate the UserDataFeed
private UserDataFeed getUserDataFeed(SyncScope[] scopes, EventListener<UserDataFeed, Void> listener) {
    UserAccount[] accounts = AccountProviderBroker.getSignInHelper().getUserAccounts();
    if (accounts.length <= 0) {
        // notify the user that sign-in is required
        return null;
    }

    // use the initialized Platform instance, along with the cross-device app ID.
    UserDataFeed feed = UserDataFeed.getForAccount(accounts[0], PlatformBroker.getPlatform(), Secrets.APP_HOST_NAME);
    feed.addSyncStatusChangedListener(listener);
    feed.addSyncScopes(scopes);
    // sync data with the server
    feed.startSync();
    return feed;
}

// use the UserDataFeed reference to create a UserActivityChannel
@Nullable
private UserNotificationChannel getUserNotificationChannel() {
    UserNotificationChannel channel = null;
    try {
        // create a UserNotificationChannel for the signed in account
        channel = new UserNotificationChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```
<span data-ttu-id="a6f58-119">En este momento, debe tener un **UserNotificationChannel** hace referencia en `mNotificationChannel`.</span><span class="sxs-lookup"><span data-stu-id="a6f58-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="a6f58-120">Crear un UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification</span><span class="sxs-lookup"><span data-stu-id="a6f58-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="a6f58-121">Como se mostró anteriormente, la notificación de Google Cloud Messaging inicial que llegan en la aplicación cliente solo contiene una derivación de hombros y necesita pasar esa carga de tap hombro a la plataforma de dispositivos conectados para desencadenar el SDK para llevar a cabo una sincronización completa con el Dispositivo servidor conectado, que contiene todas las UserNotifications publicados por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="a6f58-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="a6f58-122">Extraerá la carga de notificación completa publicada por el servidor de aplicaciones correspondiente a este tap hombro (y en el caso si las notificaciones anteriores se han publicado, pero no se recibe en este cliente de aplicación debido a la conectividad de dispositivos u otros problemas, estará extraje también).</span><span class="sxs-lookup"><span data-stu-id="a6f58-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="a6f58-123">Con estas sincronizaciones en tiempo real constantemente realizadas por el SDK, el cliente de la aplicación es capaz de tener acceso a una caché local de la fuente de datos de UserNotification ha iniciado la sesión de este usuario.</span><span class="sxs-lookup"><span data-stu-id="a6f58-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="a6f58-124">Un UserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección UserNotification completa que se puede utilizar como modelo de vista del historial de notificaciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="a6f58-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="a6f58-125">Recepción de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="a6f58-125">Receiving UserNotifications</span></span>
<span data-ttu-id="a6f58-126">Primero deberá crear una instancia de un UserNotificationReader y obtener todas las UserNotifications existentes ya en el lector si está interesado en el consumo de esa información para la experiencia que está intentando habilitar.</span><span class="sxs-lookup"><span data-stu-id="a6f58-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="a6f58-127">Es seguro suponer siempre que el servidor de aplicaciones ya publicado las notificaciones se registran en el usuario, dado que este punto de conexión de dispositivo en particular podría no ser la única o el primer punto de conexión que el usuario ha instalado la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6f58-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
```Java
private static UserNotificationReader mReader;
private static final ArrayList<UserNotification> mHistoricalNotifications = new ArrayList<>();
// Instantiate UserNotificationReader
UserNotificationReaderOptions options = new UserNotificationReaderOptions();
mReader = mNotificationChannel.createReaderWithOptions(options);
// Read any previously published UserNotifications that have not expired yet
mReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
    @Override
    public void accept(UserNotification[] userNotifications) throws Throwable {
        synchronized (mHistoricalNotifications) {
            for (UserNotification notification : userNotifications) {
                if (notification.getReadState() == UserNotificationReadState.UNREAD) {
                    mHistoricalNotifications.add(notification);
                }
            }
        }
 
        if (RunnableManager.getHistoryUpdated() != null) {
            activity.runOnUiThread(RunnableManager.getHistoryUpdated());
        }
    }
});

```
<span data-ttu-id="a6f58-128">Ahora, agregue un agente de escucha de evento que se desencadena cuando la plataforma de dispositivos conectados se completa una sincronización y tiene nuevos cambios para notificarle acerca de.</span><span class="sxs-lookup"><span data-stu-id="a6f58-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="a6f58-129">En el caso de las notificaciones de Graph, podrían ser nuevo nuevos cambios entrantes UserNotifications publicados por las eliminaciones de aplicación de servidor o UserNotifcation actualizaciones, y registrado de caducidad de las que se produjeron desde el servidor o de otros puntos de conexión que ha iniciado el mismo usuario en.</span><span class="sxs-lookup"><span data-stu-id="a6f58-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="a6f58-130">Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios.</span><span class="sxs-lookup"><span data-stu-id="a6f58-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="a6f58-131">Si actualmente utiliza mensaje de datos del Google Cloud Messaging para construir una notificación visual en la Bandeja de notificación de nivel de sistema operativo, o si usa el contenido en la notificación para actualizar alguna IU en la aplicación, esto es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="a6f58-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
```Java
mReader.addDataChangedListener(new EventListener<UserNotificationReader, Void>() {
    @Override
    public void onEvent(UserNotificationReader userNotificationReader, Void aVoid) {
        userNotificationReader.readBatchAsync(Long.MAX_VALUE).thenAccept(new AsyncOperation.ResultConsumer<UserNotification[]>() {
        @Override
        public void accept(UserNotification[] userNotifications) throws Throwable {
            boolean updatedNew = false;
            boolean updatedHistorical = false;
            synchronized (sHistoricalNotifications) {
                for (final UserNotification notification : userNotifications) {
                    if (notification.getStatus() == UserNotificationStatus.ACTIVE && notification.getReadState() == UserNotificationReadState.UNREAD) {
                        switch (notification.getUserActionState()) {
                            case NO_INTERACTION:
                                // Brand new notification
                                // Insert business logic to construct a new visual notification in Android notification tray for the user to see
                                // ...
                            case DISMISSED:
                                // Existing notification that is marked as dismissed
                                // An app client receive this type of changes because another app client logged in by the same user has marked the notification as dismissed and the change is fanned-out to everywhere
                                // This state sync across app clients on different devices enable universal dismiss of notifications and other scenarios across multiple devices owned by the same user
                                // Insert business logic to dismiss the corresponding visual notification inside Android system notification tray, to make sure users don’t have to deal with redundant information across devices, and potentially insert this notification in your app’s notification history view
                                // ...
                            default:
                                // Unexpected
                        }
                    } else {
                        // ...
                    }
                }
            }
        }
    });
}
});

```
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="a6f58-132">Actualizar el estado de un UserNotification existente</span><span class="sxs-lookup"><span data-stu-id="a6f58-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="a6f58-133">En la sección anterior, hemos mencionado que a veces un cambio UserNotification recibido a través el lector podría ser una actualización de estado en una existente UserNotification – si se está marcando como descartado o se marca como leído.</span><span class="sxs-lookup"><span data-stu-id="a6f58-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="a6f58-134">En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="a6f58-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="a6f58-135">Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio UserNotification para comenzar: desde un dispositivo diferente.</span><span class="sxs-lookup"><span data-stu-id="a6f58-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="a6f58-136">Puede elegir el momento para actualizar el estado de su UserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación se controla aún más por el usuario en cierta experiencia en la aplicación que habilitar .</span><span class="sxs-lookup"><span data-stu-id="a6f58-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="a6f58-137">Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6f58-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="a6f58-138">El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="a6f58-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="a6f58-139">El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la UserNotification correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="a6f58-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="a6f58-140">Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center.</span><span class="sxs-lookup"><span data-stu-id="a6f58-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="a6f58-141">Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario.</span><span class="sxs-lookup"><span data-stu-id="a6f58-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="a6f58-142">Clase UserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el UserNotificationReadState o la UserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="a6f58-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="a6f58-143">Por ejemplo, puede marcar UserActionState para ser activado o descartada y descartar la dinamización de ese valor para implementar universal.</span><span class="sxs-lookup"><span data-stu-id="a6f58-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="a6f58-144">Como alternativa, o al mismo tiempo puede marcar ReadState como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación.</span><span class="sxs-lookup"><span data-stu-id="a6f58-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="a6f58-145">Código siguiente fragmento de código muestra cómo marcar la UserNotificationUserActionState de una notificación como descartada.</span><span class="sxs-lookup"><span data-stu-id="a6f58-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
