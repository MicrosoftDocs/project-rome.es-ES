---
title: Integración de aplicaciones de Android con las notificaciones de Graph
description: Procedimiento para realizar los pasos de registro necesarios para convertirte en un punto de conexión de recepción de notificaciones publicadas desde tu servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59801207"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>Guía de procedimientos: Integración con las notificaciones de Graph (Android)

Las notificaciones de Graph permiten a la aplicación enviar y administrar notificaciones destinadas al usuario en múltiples dispositivos. 

Con el SDK del lado cliente de Project Rome en Android, tu aplicación de Android puede registrarse para recibir notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario conectado. El SDK permite al cliente de la aplicación recibir nuevas cargas útiles de notificaciones entrantes, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones. Para obtener más información acerca de las notificaciones y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).

Todas las características del SDK de Project Rome, incluidas las notificaciones de Graph y otras, están construidas sobre una plataforma subyacente llamada plataforma de dispositivos conectados. Esta guía está diseñada para guiarte por los pasos necesarios para empezar a utilizar la plataforma de dispositivos conectados y para explicar cómo consumir API en el SDK para implementar características específicas de las notificaciones de Graph.

Consulta en la página de [referencia de API](api-reference-for-android.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>Inicialización de un canal de notificaciones de Graph
El SDK de Project Rome permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras. Todos ellos se almacenan y sincronizan en **UserDataFeed**. **UserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph. Para la integración con las notificaciones de Graph y comenzar a recibir la UserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **UserNotificationChannel**. Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma). 

Los siguientes métodos inicializan una clase **UserNotificationChannel**.

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
En este momento, deberías tener una referencia a la clase **UserNotificationChannel** en `mNotificationChannel`.

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Creación de una clase UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification.
Como se mostró anteriormente, la notificación inicial de Google Cloud Messaging que llega al cliente de la aplicación solo contiene un toque de atención, y es necesario pasar esa carga útil del toque de atención a la plataforma de dispositivos conectados para que el SDK realice una sincronización completa con el servidor de dispositivos conectados, que contiene todas las UserNotifications publicadas por el servidor de aplicaciones. Esto reducirá la carga útil de la notificación completa publicada por tu servidor de aplicaciones correspondiente a ese toque de atención (y en caso de que se publicaran notificaciones previas pero no se recibieran en este cliente de la aplicación debido a la conectividad del dispositivo u otros problemas, también se reducirán). Con estas sincronizaciones en tiempo real realizadas constantemente por el SDK, el cliente de la aplicación puede tener acceso a una caché local de la fuente de datos de UserNotification del usuario que ha iniciado sesión. En este caso, una clase UserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de UserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.  
### <a name="receiving-usernotifications"></a>Recepción de UserNotifications
Primero es necesario crear una instancia de UserNotificationReader y obtener todas las UserNotifications existentes ya en la escucha si estás interesado en consumir esa información para la experiencia que estás intentando habilitar. Es seguro asumir siempre que el servidor de aplicaciones ya ha publicado notificaciones a este usuario conectado, ya que el punto de conexión de este dispositivo puede no ser el único o el primer punto de conexión en el que el usuario ha instalado su aplicación. 
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
Ahora, agrega una escucha de eventos que se activará cuando la plataforma de dispositivos conectados complete una sincronización y tenga nuevos cambios que notificarte. En el caso de las notificaciones de Graph, los nuevos cambios pueden ser nuevas UserNotifications entrantes publicadas por tu servidor de aplicaciones; o bien actualizaciones, eliminaciones y expiraciones de UserNotifcation que ocurrieron desde el servidor o desde otros puntos de conexión registrados en los que inició sesión el mismo usuario. 
> [!TIP] 
> En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios. Si utilizas el mensaje de datos de Google Cloud Messaging para crear una notificación visual en la bandeja de notificaciones a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo. 
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
## <a name="update-the-state-of-an-existing-usernotification"></a>Actualización del estado de una clase UserNotification existente
En la sección anterior se mencionó que a veces un cambio en UserNotification recibido a través de la escucha puede ser una actualización de estado de una UserNotification existente, independientemente de si está marcada como descartada o como leída. En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto. Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de UserNotification desde otro dispositivo. Puedes elegir la hora para actualizar el estado de tus UserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites. Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente. El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la UserNotification correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario. Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo. Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario. 

> [!TIP] 
> Actualmente, la clase UserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar UserNotificationReadState o UserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puedes marcar UserActionState para que esté activada o descartada y basarte en ese valor para implementar el descarte universal. Si lo prefieres, o al mismo tiempo, puedes marcar ReadState como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación. El fragmento de código siguiente muestra cómo marcar el elemento UserNotificationUserActionState de una notificación como desestimado.

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
