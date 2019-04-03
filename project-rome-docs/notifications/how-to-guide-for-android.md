---
title: La integración de aplicaciones Android con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 69084d2a3ac99445c8c1919b7dc4748de865153e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907917"
---
# <a name="how-to-guide-integrating-with-graph-notifications-android"></a>Guía de procedimientos: La integración con Graph notificaciones (Android)

Las notificaciones de Graph habilite la aplicación enviar y administrar las notificaciones de destinatarios de usuario en varios dispositivos. 

Con el SDK de cliente de Roma del proyecto en Android, puede registrar la aplicación Android para recibir notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario que inició sesión. El SDK permite al cliente de aplicación recibir nuevas cargas de notificación entrante, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones. Para obtener más información acerca de las notificaciones y cómo habilita la entrega de notificación centrado en humanos, consulte [información general de las notificaciones de Microsoft Graph](index.md)

Todas las características en el SDK de Roma proyecto, las notificaciones de includng gráfico y mucho más, se basan en una plataforma subyacente que se llama a la plataforma de dispositivos conectados. Esta guía está diseñada para guiarle por los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y explicar cómo usar las API del SDK para implementar notificaciones de Graph-características específicas.

Consulte la [referencia de API](api-reference-for-android.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.

Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]


## <a name="initialize-a-graph-notification-channel"></a>Inicializar un canal de notificación de Graph
El SDK de proyecto Roma permite la aplicación para suscribirse a distintos canales para recibir y administrar varios tipos de datos de usuario: incluidas las notificaciones de gráfico, las actividades del usuario y mucho más. Estos son almacenados y sincronizados en **UserDataFeed**. **UserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico. Para integrar con notificación de Graph y comience a recibir UserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **UserNotificationChannel**. Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma). 

Los siguientes métodos de inicializan un **UserNotificationChannel**.

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
En este momento, debe tener un **UserNotificationChannel** hace referencia en `mNotificationChannel`.

## <a name="create-a-usernotificationreader-to-receive-incoming-usernotifications-and-access-usernotification-history"></a>Crear un UserNotificationReader para recibir UserNotifications entrantes y acceder al historial de UserNotification
Como se mostró anteriormente, la notificación de Google Cloud Messaging inicial que llegan en la aplicación cliente solo contiene una derivación de hombros y necesita pasar esa carga de tap hombro a la plataforma de dispositivos conectados para desencadenar el SDK para llevar a cabo una sincronización completa con el Dispositivo servidor conectado, que contiene todas las UserNotifications publicados por el servidor de aplicaciones. Extraerá la carga de notificación completa publicada por el servidor de aplicaciones correspondiente a este tap hombro (y en el caso si las notificaciones anteriores se han publicado, pero no se recibe en este cliente de aplicación debido a la conectividad de dispositivos u otros problemas, estará extraje también). Con estas sincronizaciones en tiempo real constantemente realizadas por el SDK, el cliente de la aplicación es capaz de tener acceso a una caché local de la fuente de datos de UserNotification ha iniciado la sesión de este usuario. Un UserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección UserNotification completa que se puede utilizar como modelo de vista del historial de notificaciones del usuario.  
### <a name="receiving-usernotifications"></a>Recepción de UserNotifications
Primero deberá crear una instancia de un UserNotificationReader y obtener todas las UserNotifications existentes ya en el lector si está interesado en el consumo de esa información para la experiencia que está intentando habilitar. Es seguro suponer siempre que el servidor de aplicaciones ya publicado las notificaciones se registran en el usuario, dado que este punto de conexión de dispositivo en particular podría no ser la única o el primer punto de conexión que el usuario ha instalado la aplicación. 
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
Ahora, agregue un agente de escucha de evento que se desencadena cuando la plataforma de dispositivos conectados se completa una sincronización y tiene nuevos cambios para notificarle acerca de. En el caso de las notificaciones de Graph, podrían ser nuevo nuevos cambios entrantes UserNotifications publicados por las eliminaciones de aplicación de servidor o UserNotifcation actualizaciones, y registrado de caducidad de las que se produjeron desde el servidor o de otros puntos de conexión que ha iniciado el mismo usuario en. 
> [!TIP] 
> Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios. Si actualmente utiliza mensaje de datos del Google Cloud Messaging para construir una notificación visual en la Bandeja de notificación de nivel de sistema operativo, o si usa el contenido en la notificación para actualizar alguna IU en la aplicación, esto es el lugar para hacerlo. 
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
## <a name="update-the-state-of-an-existing-usernotification"></a>Actualizar el estado de un UserNotification existente
En la sección anterior, hemos mencionado que a veces un cambio UserNotification recibido a través el lector podría ser una actualización de estado en una existente UserNotification – si se está marcando como descartado o se marca como leído. En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto. Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio UserNotification para comenzar: desde un dispositivo diferente. Puede elegir el momento para actualizar el estado de su UserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación se controla aún más por el usuario en cierta experiencia en la aplicación que habilitar . Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente. El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la UserNotification correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario. Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center. Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario. 

> [!TIP] 
> Clase UserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el UserNotificationReadState o la UserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puede marcar UserActionState para ser activado o descartada y descartar la dinamización de ese valor para implementar universal. Como alternativa, o al mismo tiempo puede marcar ReadState como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación. Código siguiente fragmento de código muestra cómo marcar la UserNotificationUserActionState de una notificación como descartada.

```Java
public void dismissNotification(int position) {
    final UserNotification notification = mNewNotifications.get(position);
          
    notification.setUserActionState(UserNotificationUserActionState.DISMISSED);
    notification.saveAsync();
}

```
