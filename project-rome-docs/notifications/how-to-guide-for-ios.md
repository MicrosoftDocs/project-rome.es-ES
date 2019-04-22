---
title: Integración de aplicaciones de IOs con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801317"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="3c0e6-103">Guía de procedimientos: La integración con Graph notificaciones (iOS)</span><span class="sxs-lookup"><span data-stu-id="3c0e6-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="3c0e6-104">Las notificaciones de Graph habilite la aplicación enviar y administrar las notificaciones de destinatarios de usuario en varios dispositivos.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="3c0e6-105">Con el SDK de cliente de proyecto Roma en iOS, puede registrar su aplicación iOS para recibir notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario que inició sesión.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="3c0e6-106">El SDK permite al cliente de aplicación recibir nuevas cargas de notificación entrante, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="3c0e6-107">Para obtener más información acerca de las notificaciones y cómo habilita la entrega de notificación centrado en humanos, consulte [información general de las notificaciones de Microsoft Graph](index.md)</span><span class="sxs-lookup"><span data-stu-id="3c0e6-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="3c0e6-108">Todas las características en el SDK de Roma proyecto, las notificaciones de includng gráfico y mucho más, se basan en una plataforma subyacente que se llama a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="3c0e6-109">Esta guía está diseñada para guiarle por los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y explicar cómo usar las API del SDK para implementar notificaciones de Graph-características específicas.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="3c0e6-110">Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="3c0e6-111">Consulte la [referencia de API](api-reference-for-ios/index.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="3c0e6-112">Configurar la plataforma de dispositivos conectados y notificaciones</span><span class="sxs-lookup"><span data-stu-id="3c0e6-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="3c0e6-113">Con la plataforma</span><span class="sxs-lookup"><span data-stu-id="3c0e6-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="3c0e6-114">Inicializar un canal de notificación de Graph</span><span class="sxs-lookup"><span data-stu-id="3c0e6-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="3c0e6-115">El SDK de proyecto Roma permite la aplicación para suscribirse a distintos canales para recibir y administrar varios tipos de datos de usuario: incluidas las notificaciones de gráfico, las actividades del usuario y mucho más.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="3c0e6-116">Estos son almacenados y sincronizados en **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="3c0e6-117">**MCDUserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="3c0e6-118">Para integrar con notificación de Graph y comience a recibir MCDUserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="3c0e6-119">Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).</span><span class="sxs-lookup"><span data-stu-id="3c0e6-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="3c0e6-120">Los siguientes métodos de inicializan un **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
```ObjectiveC
// You must be logged in to use UserNotifications
NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
if (accounts.count > 0)
{
    // Get a UserNotification channel, getting the default channel
    NSLog(@"Creating UserNotificationChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserNotificationChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must log in to receive notifications for the logged in user!");
    self.createNotificationStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="3c0e6-121">En este momento, debe tener un **MCDUserNotificationChannel** hace referencia en `channel`.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="3c0e6-122">Crear un MCDUserNotificationReader para recibir MCDUserNotifications entrantes y acceder al historial de MCDUserNotification</span><span class="sxs-lookup"><span data-stu-id="3c0e6-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="3c0e6-123">Tal como se mostró anteriormente, el APNS inicial silenciosa mensajes que llegan en el cliente de aplicación solo contiene una derivación de hombros y necesita pasar esa carga de tap hombro a la plataforma de dispositivos conectados para desencadenar el SDK para llevar a cabo una sincronización completa con el dispositivo conectado servidor, que contiene todas las MCDUserNotifications publicados por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="3c0e6-124">Extraerá la carga de notificación completa publicada por el servidor de aplicaciones correspondiente a este tap hombro (y en el caso si las notificaciones anteriores se han publicado, pero no se recibe en este cliente de aplicación debido a la conectividad de dispositivos u otros problemas, estará extraje también).</span><span class="sxs-lookup"><span data-stu-id="3c0e6-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="3c0e6-125">Con estas sincronizaciones en tiempo real constantemente realizadas por el SDK, el cliente de la aplicación es capaz de tener acceso a una caché local de la fuente de datos de MCDUserNotification ha iniciado la sesión de este usuario.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="3c0e6-126">Un MCDUserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección MCDUserNotification completa que se puede utilizar como modelo de vista de notificación del usuario historial.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="3c0e6-127">Recibir MCDUserNotifications</span><span class="sxs-lookup"><span data-stu-id="3c0e6-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="3c0e6-128">Primero deberá crear una instancia de un MCDUserNotificationReader y obtener todas las MCDUserNotifications existentes ya en el lector si está interesado en el consumo de esa información para la experiencia que está intentando habilitar.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="3c0e6-129">Es seguro suponer siempre que el servidor de aplicaciones ya publicado las notificaciones se registran en el usuario, dado que este punto de conexión de dispositivo en particular podría no ser la única o el primer punto de conexión que el usuario ha instalado la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="3c0e6-130">A continuación, agregue un agente de escucha de evento que se desencadena cuando la plataforma de dispositivos conectados se completa una sincronización y tiene nuevos cambios para notificarle acerca de.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="3c0e6-131">En el caso de las notificaciones de Graph, podrían ser nuevo nuevos cambios entrantes MCDUserNotifications publicados por las eliminaciones de aplicación de servidor o MCDUserNotifcation actualizaciones, y caducidad de las que se produjeron desde el servidor o de otros puntos de conexión registrados que el mismo usuario iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="3c0e6-132">Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="3c0e6-133">Si actualmente utiliza la notificación silenciosa de APNS para construir una notificación visual en el centro de notificaciones de nivel de sistema operativo, o si usa el contenido en la notificación silenciosa actualizar alguna IU en la aplicación, esto es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

```ObjectiveC
// Instantiate the reader from a MCDUserNotificationChannel
// Add a data change listener to subscribe to new changes when new notifications or notification updates are received
- (void)setupWithAccount:(MCDUserAccount*)account {
    dispatch_async(dispatch_get_global_queue(QOS_CLASS_DEFAULT, 0), ^{
        @synchronized (self) {
            MCDUserDataFeed* dataFeed = [MCDUserDataFeed userDataFeedForAccount:account platform:_platform activitySourceHost:@"graphnotifications.sample.windows.com"];
            [dataFeed addSyncScopes:@[[MCDUserNotificationChannel syncScope]]];
            self.channel = [MCDUserNotificationChannel userNotificationChannelWithUserDataFeed:dataFeed];
            self.reader = [self.channel createReader];
            
            __weak typeof(self) weakSelf = self;
            _readerRegistrationToken = [self.reader addDataChangedListener:^(__unused MCDUserNotificationReader* source) {
                NSLog(@"ME123 Got a change!");
                if (weakSelf) {
                    [weakSelf forceRead];
                } else {
                    NSLog(@"ME123 WEAKSELF FOR CHANGES IS NULL!!!");
                }
            }];
            
            [self forceRead];
        }
    });
}

// this is your own business logic when the event listener is fired
// In this case, the app reads the existing batch of notifications in the store and handle any new incoming notifications or notification updates after that
- (void)forceRead {
    NSLog(@"ME123 Forced to read!");
    [self.reader readBatchAsyncWithMaxSize:NSUIntegerMax completion:^(NSArray<MCDUserNotification *> * _Nullable notifications, NSError * _Nullable error) {
        if (error) {
            NSLog(@"ME123 Failed to read batch with error %@", error);
        } else {
            [self _handleNotifications:notifications];
            NSLog(@"ME123 Have %ld listeners", self.listenerMap.count);
            for (void (^listener)(void) in self.listenerMap.allValues) {
                NSLog(@"ME123 Calling a listener about an update!");
                listener();
            }
        }
    }];
}

```

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="3c0e6-134">Actualizar el estado de un MCDUserNotification existente</span><span class="sxs-lookup"><span data-stu-id="3c0e6-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="3c0e6-135">En la sección anterior, hemos mencionado que a veces un cambio MCDUserNotification recibido a través el lector podría ser una actualización de estado en una existente MCDUserNotification – si se está marcando como descartado o se marca como leído.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="3c0e6-136">En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="3c0e6-137">Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio MCDUserNotification para comenzar: desde un dispositivo diferente.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="3c0e6-138">Puede elegir el momento para actualizar el estado de su MCDUserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación es aún más controlada por el usuario en algo de experiencia en la aplicación habilitar.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="3c0e6-139">Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="3c0e6-140">El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="3c0e6-141">El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la notificación de usuario correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="3c0e6-142">Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="3c0e6-143">Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="3c0e6-144">Clase MCDUserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el MCDUserNotificationReadState o la MCDUserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="3c0e6-145">Por ejemplo, puede marcar el estado de acción para ser activado o descartada y descartar la dinamización de ese valor para implementar universal.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="3c0e6-146">Como alternativa, o al mismo tiempo, se puede marcar leer el estado como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación.</span><span class="sxs-lookup"><span data-stu-id="3c0e6-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

```ObjectiveC
- (void)dismissNotification:(MCDUserNotification*)notification {
    @synchronized (self) {
        notification.userActionState = MCDUserNotificationUserActionStateDismissed;
        [notification saveAsync:^(__unused MCDUserNotificationUpdateResult * _Nullable result, __unused NSError * _Nullable err) {
            NSLog(@"ME123 Dismiss notification with result %d error %@", result.succeeded, err);
        }];
    }
}

```
