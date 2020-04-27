---
title: Integración de aplicaciones de Android con las notificaciones de Graph
description: Procedimiento para realizar los pasos de registro necesarios para convertirte en un punto de conexión de recepción de notificaciones publicadas desde tu servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801207"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a><span data-ttu-id="42790-103">Guía de procedimientos: Integración con las notificaciones de Graph (Android)</span><span class="sxs-lookup"><span data-stu-id="42790-103">How-To Guide: Integrating with Graph Notifications (Android)</span></span>

<span data-ttu-id="42790-104">Las notificaciones de Graph permiten a la aplicación enviar y administrar notificaciones destinadas al usuario en múltiples dispositivos.</span><span class="sxs-lookup"><span data-stu-id="42790-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="42790-105">Con el SDK del lado cliente de Project Rome en Android, tu aplicación de Android puede registrarse para recibir notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="42790-105">With the Project Rome client-side SDK on Android, your Android app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="42790-106">El SDK permite al cliente de la aplicación recibir nuevas cargas útiles de notificaciones entrantes, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="42790-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="42790-107">Para obtener más información acerca de las notificaciones y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="42790-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="42790-108">Todas las características del SDK de Project Rome, incluidas las notificaciones de Graph y otras, están construidas sobre una plataforma subyacente llamada plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="42790-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="42790-109">Esta guía está diseñada para guiarte por los pasos necesarios para empezar a utilizar la plataforma de dispositivos conectados y para explicar cómo consumir API en el SDK para implementar características específicas de las notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="42790-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="42790-110">Consulta en la página de [referencia de API](api-reference-for-android.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="42790-110">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to notification scenarios.</span></span>

<span data-ttu-id="42790-111">Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="42790-111">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="42790-112">Inicialización de un canal de notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="42790-112">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="42790-113">El SDK de Project Rome permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras.</span><span class="sxs-lookup"><span data-stu-id="42790-113">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="42790-114">Todos ellos se almacenan y sincronizan en **UserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="42790-114">These are all stored and synced in **UserDataFeed**.</span></span> <span data-ttu-id="42790-115">**UserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="42790-115">**UserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span> <span data-ttu-id="42790-116">Para la integración con las notificaciones de Graph y comenzar a recibir la UserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="42790-116">To integrate with Graph Notification and start receiving UserNotification published by your app server, you will first need to initialize the user data feed by creating a **UserNotificationChannel**.</span></span> <span data-ttu-id="42790-117">Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).</span><span class="sxs-lookup"><span data-stu-id="42790-117">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span> 

<span data-ttu-id="42790-118">Los siguientes métodos inicializan una clase **UserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="42790-118">The following methods initialize a **UserNotificationChannel**.</span></span>

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
<span data-ttu-id="42790-119">En este momento, deberías tener una referencia a la clase **UserNotificationChannel** en `mNotificationChannel`.</span><span class="sxs-lookup"><span data-stu-id="42790-119">At this point, you should have a **UserNotificationChannel** reference in `mNotificationChannel`.</span></span>

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a><span data-ttu-id="42790-120">Creación de una clase UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification.</span><span class="sxs-lookup"><span data-stu-id="42790-120">Create a UserNotificationReader to receive incoming UserNotifications and access UserNotification history</span></span>
<span data-ttu-id="42790-121">Como se mostró anteriormente, la notificación inicial de Google Cloud Messaging que llega al cliente de la aplicación solo contiene un toque de atención, y es necesario pasar esa carga útil del toque de atención a la plataforma de dispositivos conectados para que el SDK realice una sincronización completa con el servidor de dispositivos conectados, que contiene todas las UserNotifications publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="42790-121">As we showed previously, the initial Google Cloud Messaging notification arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the UserNotifications published by your app server.</span></span> <span data-ttu-id="42790-122">Esto reducirá la carga útil de la notificación completa publicada por tu servidor de aplicaciones correspondiente a ese toque de atención (y en caso de que se publicaran notificaciones previas pero no se recibieran en este cliente de la aplicación debido a la conectividad del dispositivo u otros problemas, también se reducirán).</span><span class="sxs-lookup"><span data-stu-id="42790-122">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="42790-123">Con estas sincronizaciones en tiempo real realizadas constantemente por el SDK, el cliente de la aplicación puede tener acceso a una caché local de la fuente de datos de UserNotification del usuario que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="42790-123">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s UserNotification data feed.</span></span> <span data-ttu-id="42790-124">En este caso, una clase UserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de UserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="42790-124">A UserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full UserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-usernotifications"></a><span data-ttu-id="42790-125">Recepción de UserNotifications</span><span class="sxs-lookup"><span data-stu-id="42790-125">Receiving UserNotifications</span></span>
<span data-ttu-id="42790-126">Primero es necesario crear una instancia de UserNotificationReader y obtener todas las UserNotifications existentes ya en la escucha si estás interesado en consumir esa información para la experiencia que estás intentando habilitar.</span><span class="sxs-lookup"><span data-stu-id="42790-126">First you need to instantiate a UserNotificationReader, and get all the existing UserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="42790-127">Es seguro asumir siempre que el servidor de aplicaciones ya ha publicado notificaciones a este usuario conectado, ya que el punto de conexión de este dispositivo puede no ser el único o el primer punto de conexión en el que el usuario ha instalado su aplicación.</span><span class="sxs-lookup"><span data-stu-id="42790-127">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> 
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
<span data-ttu-id="42790-128">Ahora, agrega una escucha de eventos que se activará cuando la plataforma de dispositivos conectados complete una sincronización y tenga nuevos cambios que notificarte.</span><span class="sxs-lookup"><span data-stu-id="42790-128">Now, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="42790-129">En el caso de las notificaciones de Graph, los nuevos cambios pueden ser nuevas UserNotifications entrantes publicadas por tu servidor de aplicaciones; o bien actualizaciones, eliminaciones y expiraciones de UserNotifcation que ocurrieron desde el servidor o desde otros puntos de conexión registrados en los que inició sesión el mismo usuario.</span><span class="sxs-lookup"><span data-stu-id="42790-129">In the case of Graph Notifications, new changes could be new incoming UserNotifications published by your app server, or UserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span> 
> [!TIP] 
> <span data-ttu-id="42790-130">En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios.</span><span class="sxs-lookup"><span data-stu-id="42790-130">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="42790-131">Si utilizas el mensaje de datos de Google Cloud Messaging para crear una notificación visual en la bandeja de notificaciones a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="42790-131">If you currently use Google Cloud Messaging’s data message to construct a visual notification in the OS-level notification tray, or if you use the content in the notification to update some in-app UI, this is the place to do that.</span></span> 
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
## <a name="update-the-state-of-an-existing-usernotification"></a><span data-ttu-id="42790-132">Actualización del estado de una clase UserNotification existente</span><span class="sxs-lookup"><span data-stu-id="42790-132">Update the state of an existing UserNotification</span></span>
<span data-ttu-id="42790-133">En la sección anterior se mencionó que a veces un cambio en UserNotification recibido a través de la escucha puede ser una actualización de estado de una UserNotification existente, independientemente de si está marcada como descartada o como leída.</span><span class="sxs-lookup"><span data-stu-id="42790-133">In the previous section, we mentioned that sometimes a UserNotification change received through the reader could be a state update on an existing UserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="42790-134">En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="42790-134">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="42790-135">Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de UserNotification desde otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="42790-135">Taking a step back, your app client is often the one that initiated this UserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="42790-136">Puedes elegir la hora para actualizar el estado de tus UserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites.</span><span class="sxs-lookup"><span data-stu-id="42790-136">You can choose the time to update the state of your UserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="42790-137">Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="42790-137">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="42790-138">El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="42790-138">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="42790-139">El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la UserNotification correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="42790-139">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding UserNotification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="42790-140">Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="42790-140">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="42790-141">Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario.</span><span class="sxs-lookup"><span data-stu-id="42790-141">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP] 
> <span data-ttu-id="42790-142">Actualmente, la clase UserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar UserNotificationReadState o UserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="42790-142">UserNotification class currently provides 2 types of state updates – you can modify the UserNotificationReadState or the UserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="42790-143">Por ejemplo, puedes marcar UserActionState para que esté activada o descartada y basarte en ese valor para implementar el descarte universal.</span><span class="sxs-lookup"><span data-stu-id="42790-143">For example, you can mark UserActionState to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="42790-144">Si lo prefieres, o al mismo tiempo, puedes marcar ReadState como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="42790-144">Alternatively, or at the same time you can mark ReadState as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> <span data-ttu-id="42790-145">El fragmento de código siguiente muestra cómo marcar el elemento UserNotificationUserActionState de una notificación como desestimado.</span><span class="sxs-lookup"><span data-stu-id="42790-145">Below code snippet shows how to mark the UserNotificationUserActionState of a notification as Dismissed.</span></span>

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
