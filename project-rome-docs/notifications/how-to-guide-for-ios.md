---
title: Integración de aplicaciones de IOs con las notificaciones de Graph
description: Procedimiento para realizar los pasos de registro necesarios para convertirte en un punto de conexión de recepción de notificaciones publicadas desde tu servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801317"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a><span data-ttu-id="5f56c-103">Guía de procedimientos: Integración con las notificaciones de Graph (iOS)</span><span class="sxs-lookup"><span data-stu-id="5f56c-103">How-To Guide: Integrating with Graph Notifications (iOS)</span></span>

<span data-ttu-id="5f56c-104">Las notificaciones de Graph permiten a la aplicación enviar y administrar notificaciones destinadas al usuario en múltiples dispositivos.</span><span class="sxs-lookup"><span data-stu-id="5f56c-104">Graph Notifications enable your app to send and manage user-targeting notifications across multiple devices.</span></span> 

<span data-ttu-id="5f56c-105">Con el SDK del lado cliente de Project Rome en iOS, tu aplicación de iOS puede registrarse para recibir notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario conectado.</span><span class="sxs-lookup"><span data-stu-id="5f56c-105">With the Project Rome client-side SDK on iOS, your iOS app can register to receive notifications published from your app server targeted at a logged in user.</span></span> <span data-ttu-id="5f56c-106">El SDK permite al cliente de la aplicación recibir nuevas cargas útiles de notificaciones entrantes, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones.</span><span class="sxs-lookup"><span data-stu-id="5f56c-106">The SDK enables the app client to receive new incoming notification payloads, manage the state of the existing notifications, and retreive notification history.</span></span> <span data-ttu-id="5f56c-107">Para obtener más información acerca de las notificaciones y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).</span><span class="sxs-lookup"><span data-stu-id="5f56c-107">For more information about Notifications and how it enables human-centric notification delivery, see [Microsoft Graph Notifications Overview](index.md)</span></span>

<span data-ttu-id="5f56c-108">Todas las características del SDK de Project Rome, incluidas las notificaciones de Graph y otras, están construidas sobre una plataforma subyacente llamada plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="5f56c-108">All features in the Project Rome SDK, includng Graph Notifications and more, are built on top of an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="5f56c-109">Esta guía está diseñada para guiarte por los pasos necesarios para empezar a utilizar la plataforma de dispositivos conectados y para explicar cómo consumir API en el SDK para implementar características específicas de las notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="5f56c-109">This guide is designed to guide you through the necessary steps to get started using the Connected Devices Platform, and to explain how to consume APIs in the SDK to implement Graph Notifications -specific features.</span></span>

<span data-ttu-id="5f56c-110">Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo para iOS de Project Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples), disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="5f56c-110">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="5f56c-111">Consulta en la página de [referencia de API](api-reference-for-ios/index.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.</span><span class="sxs-lookup"><span data-stu-id="5f56c-111">See the [API reference](api-reference-for-ios/index.md) page for links to the reference docs relevant to notification scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="5f56c-112">Configuración de la plataforma de dispositivos conectados y las notificaciones</span><span class="sxs-lookup"><span data-stu-id="5f56c-112">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="5f56c-113">Uso de la plataforma</span><span class="sxs-lookup"><span data-stu-id="5f56c-113">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a><span data-ttu-id="5f56c-114">Inicialización de un canal de notificaciones de Graph</span><span class="sxs-lookup"><span data-stu-id="5f56c-114">Initialize a Graph Notification channel</span></span>
<span data-ttu-id="5f56c-115">El SDK de Project Rome permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras.</span><span class="sxs-lookup"><span data-stu-id="5f56c-115">The Project Rome SDK allows your app to subscribe to different channels in order to receive and manage various types of user data – including Graph Notifications, User Activities, and more.</span></span> <span data-ttu-id="5f56c-116">Todos ellos se almacenan y sincronizan en **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="5f56c-116">These are all stored and synced in **MCDUserDataFeed**.</span></span> <span data-ttu-id="5f56c-117">**MCDUserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph.</span><span class="sxs-lookup"><span data-stu-id="5f56c-117">**MCDUserNotification** is the class and data type corresponding to a user-targeted notification sent via Graph Notifications.</span></span>
<span data-ttu-id="5f56c-118">Para la integración con las notificaciones de Graph y comenzar a recibir la MCDUserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="5f56c-118">To integrate with Graph Notification and start receiving MCDUserNotification published by your app server, you will first need to initialize the user data feed by creating a **MCDUserNotificationChannel**.</span></span> <span data-ttu-id="5f56c-119">Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).</span><span class="sxs-lookup"><span data-stu-id="5f56c-119">You should treat this like the platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before platform initialization).</span></span>

<span data-ttu-id="5f56c-120">Los siguientes métodos inicializan una clase **MCDUserNotificationChannel**.</span><span class="sxs-lookup"><span data-stu-id="5f56c-120">The following methods initialize a **MCDUserNotificationChannel**.</span></span>
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
<span data-ttu-id="5f56c-121">En este momento, deberías tener una referencia a la clase **MCDUserNotificationChannel** en `channel`.</span><span class="sxs-lookup"><span data-stu-id="5f56c-121">At this point, you should have a **MCDUserNotificationChannel** reference in `channel`.</span></span>

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a><span data-ttu-id="5f56c-122">Creación de una clase MCDUserNotificationReader para recibir MCDUserNotifications entrantes y acceder al historial de MCDUserNotification.</span><span class="sxs-lookup"><span data-stu-id="5f56c-122">Create a MCDUserNotificationReader to receive incoming MCDUserNotifications and access MCDUserNotification history</span></span>
<span data-ttu-id="5f56c-123">Como se mostró anteriormente, la notificación inicial de APNS que llega al cliente de la aplicación solo contiene un toque de atención, y es necesario pasar esa carga útil del toque de atención a la plataforma de dispositivos conectados para que el SDK realice una sincronización completa con el servidor de dispositivos conectados, que contiene todas las MCDUserNotifications publicadas por el servidor de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="5f56c-123">As we showed previously, the initial APNS silent message arriving on the app client only contains a shoulder tap, and you need to pass that shoulder tap payload to the Connected Devices Platform in order to trigger the SDK to perform a full sync with the Connected Device server, which contains all the MCDUserNotifications published by your app server.</span></span> <span data-ttu-id="5f56c-124">Esto reducirá la carga útil de la notificación completa publicada por tu servidor de aplicaciones correspondiente a ese toque de atención (y en caso de que se publicaran notificaciones previas pero no se recibieran en este cliente de la aplicación debido a la conectividad del dispositivo u otros problemas, también se reducirán).</span><span class="sxs-lookup"><span data-stu-id="5f56c-124">This will pull down the full notification payload published by your app server corresponding to this shoulder tap (and in case if any previous notifications were published but not received on this app client due to device connectivity or other issues, they will be pulled down as well).</span></span> <span data-ttu-id="5f56c-125">Con estas sincronizaciones en tiempo real realizadas constantemente por el SDK, el cliente de la aplicación puede tener acceso a una caché local de la fuente de datos de MCDUserNotification del usuario que ha iniciado sesión.</span><span class="sxs-lookup"><span data-stu-id="5f56c-125">With these real-time syncs constantly performed by the SDK, the app client is able to have access to a local cache of this logged-in user’s MCDUserNotification data feed.</span></span> <span data-ttu-id="5f56c-126">En este caso, una clase MCDUserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de MCDUserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.</span><span class="sxs-lookup"><span data-stu-id="5f56c-126">A MCDUserNotificationReader in this case enables the app client’s access to this data feed – to receive latest notification payload via event listener, or to access the full MCDUserNotification collection which can be used as view model of the user’s notification history.</span></span>  
### <a name="receiving-mcdusernotifications"></a><span data-ttu-id="5f56c-127">Recepción de MCDUserNotifications</span><span class="sxs-lookup"><span data-stu-id="5f56c-127">Receiving MCDUserNotifications</span></span>
<span data-ttu-id="5f56c-128">Primero es necesario crear una instancia de MCDUserNotificationReader y obtener todas las MCDUserNotifications existentes ya en la escucha si estás interesado en consumir esa información para la experiencia que estás intentando habilitar.</span><span class="sxs-lookup"><span data-stu-id="5f56c-128">First you need to instantiate a MCDUserNotificationReader, and get all the existing MCDUserNotifications already in the reader if you are interested in consuming that information for the experience you are trying to enable.</span></span> <span data-ttu-id="5f56c-129">Es seguro asumir siempre que el servidor de aplicaciones ya ha publicado notificaciones a este usuario conectado, ya que el punto de conexión de este dispositivo puede no ser el único o el primer punto de conexión en el que el usuario ha instalado su aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f56c-129">It’s safe to always assume that the app server has already published notifications to this logged in user, given that this particular device endpoint might not be the only or the first endpoint that the user has installed your app.</span></span> <span data-ttu-id="5f56c-130">A continuación, agrega una escucha de eventos que se activará cuando la plataforma de dispositivos conectados complete una sincronización y tenga nuevos cambios que notificarte.</span><span class="sxs-lookup"><span data-stu-id="5f56c-130">Then, add an event listener which gets triggered when the Connected Device Platform completes a sync and has new changes to notify you about.</span></span> <span data-ttu-id="5f56c-131">En el caso de las notificaciones de Graph, los nuevos cambios pueden ser nuevas MCDUserNotifications entrantes publicadas por tu servidor de aplicaciones; o bien actualizaciones, eliminaciones y expiraciones de MCDUserNotifcation que ocurrieron desde el servidor o desde otros puntos de conexión registrados en los que inició sesión el mismo usuario.</span><span class="sxs-lookup"><span data-stu-id="5f56c-131">In the case of Graph Notifications, new changes could be new incoming MCDUserNotifications published by your app server, or MCDUserNotifcation updates, deletions, and expirations that happened from the server or from other registered endpoints that the same user logged in.</span></span>

> [!TIP] 
> <span data-ttu-id="5f56c-132">En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios.</span><span class="sxs-lookup"><span data-stu-id="5f56c-132">This event listener is where you handle the main business logic and “consume” the content of your notification payload based on your scenarios.</span></span> <span data-ttu-id="5f56c-133">Si utilizas la notificación sin procesar de APNS para crear una notificación visual en el centro de notificaciones a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="5f56c-133">If you currently use APNS silent notification to construct a visual notification in the OS-level notification center, or if you use the content in the silent notification to update some in-app UI, this is the place to do that.</span></span> 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a><span data-ttu-id="5f56c-134">Actualización del estado de una clase MCDUserNotification existente</span><span class="sxs-lookup"><span data-stu-id="5f56c-134">Update the state of an existing MCDUserNotification</span></span>
<span data-ttu-id="5f56c-135">En la sección anterior se mencionó que a veces un cambio en MCDUserNotification recibido a través de la escucha puede ser una actualización de estado de una MCDUserNotification existente, independientemente de si está marcada como descartada o como leída.</span><span class="sxs-lookup"><span data-stu-id="5f56c-135">In the previous section, we mentioned that sometimes a MCDUserNotification change received through the reader could be a state update on an existing MCDUserNotification – whether that’s being marked as dismissed or marked as read.</span></span> <span data-ttu-id="5f56c-136">En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto.</span><span class="sxs-lookup"><span data-stu-id="5f56c-136">In this case, the app client can choose what to do, such as enabling universal dismiss by removing the corresponding visual notification on this particular device.</span></span> <span data-ttu-id="5f56c-137">Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de MCDUserNotification desde otro dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5f56c-137">Taking a step back, your app client is often the one that initiated this MCDUserNotification change update to begin with – from a different device.</span></span> <span data-ttu-id="5f56c-138">Puedes elegir la hora para actualizar el estado de tus MCDUserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites.</span><span class="sxs-lookup"><span data-stu-id="5f56c-138">You can choose the time to update the state of your MCDUserNotifications, but usually they get updated when the corresponding visual notification is handled by the user on that device, or the notification is further handled by the user in some in-app experience you enable.</span></span> <span data-ttu-id="5f56c-139">Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f56c-139">Here is an example of what the flow would look like: Your app server publishes a notification targeted at User A. User A receives this notification on both his PC and his phone where the app clients are installed.</span></span> <span data-ttu-id="5f56c-140">El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente.</span><span class="sxs-lookup"><span data-stu-id="5f56c-140">The user clicks on the notification on PC, and chases into the app to handles the corresponding task.</span></span> <span data-ttu-id="5f56c-141">El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la notificación de usuario correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario.</span><span class="sxs-lookup"><span data-stu-id="5f56c-141">The app client on this PC will then call into Connected Devices Platform SDK to update the state of the corresponding User Notification in order to have this update synced across all this user’s devices.</span></span> <span data-ttu-id="5f56c-142">Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5f56c-142">The other app clients, upon receiving this state update in real-time, will then remove the corresponding visual alert / message / toast notification from the device’s notification center / notification tray / Action Center.</span></span> <span data-ttu-id="5f56c-143">Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario.</span><span class="sxs-lookup"><span data-stu-id="5f56c-143">This is how notifications get universally dismissed across a user’s devices.</span></span> 

> [!TIP]
> <span data-ttu-id="5f56c-144">Actualmente, la clase MCDUserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar MCDUserNotificationReadState o MCDUserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="5f56c-144">MCDUserNotification class currently provides 2 types of state updates – you can modify the MCDUserNotificationReadState or the MCDUserNotificationUserActionState and define your own logic on what should happen when notifications are updated.</span></span> <span data-ttu-id="5f56c-145">Por ejemplo, puedes marcar la acción para que esté activada o descartada y basarte en ese valor para implementar el descarte universal.</span><span class="sxs-lookup"><span data-stu-id="5f56c-145">For example, you can mark the action state to be Activated or Dismissed, and pivot on that value to implement universal dismiss.</span></span> <span data-ttu-id="5f56c-146">Si lo prefieres, o al mismo tiempo, puedes marcar el estado de lectura como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="5f56c-146">Alternatively, or at the same time, you can mark read state as Read or Unread and based on that determine which notifications should show up in the in-app notification history view.</span></span> 

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
