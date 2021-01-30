---
title: Publicación y lectura de actividades del usuario (Android)
description: En esta guía se muestra cómo crear, publicar y leer en la aplicación Android actividades del usuario basadas en Windows.
ms.topic: article
keywords: microsoft, windows, project rome, user activities, android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: ab9cd29451ca9af511b2bd5f94e423f1ba01b46e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901673"
---
# <a name="implementing-user-activities-for-android"></a>Implementación de Actividades del usuario para Android

Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación. Permiten guardar una instantánea de una tarea para continuarla más adelante. La característica [Línea de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) muestra a los usuarios de Windows una lista desplazable de todas sus actividades recientes, representadas como tarjetas con texto y gráficos. Para obtener más información sobre las actividades del usuario en general, consulta [Continuar la actividad del usuario, incluso en diferentes dispositivos](/windows/uwp/launch-resume/useractivities). Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, consulta la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).

Con el SDK de Project Rome, la aplicación de Android no solo puede publicar las actividades del usuario para su uso en las características de Windows como Línea de tiempo, sino que también puede actuar como punto de conexión y leer las actividades al usuario, al igual que hace la característica Línea de tiempo en dispositivos Windows. Esto permite que las aplicaciones multidispositivo trasciendan las plataformas y presenten experiencias que siguen a los usuarios y no a los dispositivos.  

Consulta en la página de [referencia de API](api-reference-for-android.md) los vínculos a los documentos de referencia pertinentes para estos escenarios.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Uso de la plataforma

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Inicialización de un canal de actividad del usuario

Para implementar características de actividad del usuario en la aplicación, primero debes inicializar la fuente de la actividad del usuario mediante la creación de una clase UserActivityChannel. Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).

También necesitarás el id. de la aplicación multiplataforma, recuperado a través del registro del Panel de desarrolladores de Microsoft.
Los siguientes métodos inicializan una clase UserActivityChannel.

```Java
private UserActivityChannel mActivityChannel;
private UserDataFeed mUserDataFeed;

// ...

/**
 * Initializes the UserActivityFeed.
 */
public void initializeUserActivityFeed() {

    // define what scope of data this app needs
    SyncScope[] scopes = { UserActivityChannel.getSyncScope(), UserNotificationChannel.getSyncScope() };

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
    mActivityChannel = getUserActivityChannel();
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
private UserActivityChannel getUserActivityChannel() {
    UserActivityChannel channel = null;
    try {
        // create a UserActivityChannel for the signed in account
        channel = new UserActivityChannel(mUserDataFeed);
    } catch (Exception e) {
        e.printStackTrace();
        // handle exception
    }
    return channel;
}
```

En este punto debes contar con una referencia a UserActivityChannel en el canal mActivityChannel.


### <a name="create-and-publish-a-user-activity"></a>Creación y publicación de una actividad del usuario

A continuación, establece los datos de ID, DisplayText y ActivationURI de la que será una nueva instancia de **UserActivity**. El valor de ID debe ser una cadena única. El valor de DisplayText se verá en otros dispositivos cuando vean la actividad (en la característica Línea de tiempo de Windows, por ejemplo), por lo que debe ser una descripción concisa de la actividad. El valor de ActivationUri determinará qué acción se realiza cuando se activa la **UserActivity** (por ejemplo, cuando se selecciona en la línea de tiempo). El código siguiente rellena datos de ejemplo para estos campos.


```Java
private UserActivity mActivity;
private String mActivityId;
private String mDisplayText;
private String mActivationUri;

// ...

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```

A continuación, indica un método que cree una nueva instancia de **UserActivity**.

```Java
// Create the UserActivity (with unique ID) using a custom method. 
mActivity = createUserActivity(mActivityChannel, mActivityId);

// ...

// Custom method for creating a new UserActivity
@Nullable
private UserActivity createUserActivity(UserActivityChannel channel, String activityId)
{
    UserActivity activity = null;
    AsyncOperation<UserActivity> activityOperation = channel.getOrCreateUserActivityAsync(activityId);
    try {
        activity = activityOperation.get();
        Log.d("UserActivityFragment","Created user activity successfully");
    } catch (Exception e) {
        e.printStackTrace();
        Log.d("UserActivityFragment","Created user activity successfully");
    }
    return activity;
}
```
Cuando tengas la instancia de **UserActivity**, rellénala con los datos definidos antes.

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

Por último, publica la actividad en la nube. 

```Java
// This code saves and publishes the activity
AsyncOperation<Void> operation = mActivity.saveAsync();
operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<Void, Throwable>() {
    @Override
    public void accept(Void aVoid, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to save");
        } else {
            Log.d("UserActivityFragment", "User activity saved");
        }
    }
});
```

> [!TIP] 
> Además de las propiedades anteriores, hay muchas otras características que se pueden configurar. Para ver todos los modos en los que se puede personalizar la construcción UserActivity, consulta las clases **[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)** y **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)**. Consulta recomendaciones detalladas sobre cómo diseñar actividades del usuario en la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).

### <a name="update-an-existing-user-activity"></a>Actualización de una actividad del usuario existente

Si ya tienes una actividad y deseas actualizar su información (en el caso de una nueva involucración, un cambio de página, etc.), puedes hacerlo con **UserActivitySession**.

```Java
private UserActivitySession mActivitySession;

// ...

if (mActivity != null)
{
    // create a session from a previous UserActivity instance.
    mActivitySession = mActivity.createSession();
    Log.d("UserActivityFragment", "Starting");
}
```

Una vez que has creado una sesión, la aplicación puede realizar los cambios deseados en las propiedades de la construcción **UserActivity**. Cuando hayas terminado de realizar los cambios, cierra la sesión. 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

**UserActivitySession** se puede considerar como una manera de crear una clase **UserActivitySessionHistoryItem** (se explica en la sección siguiente). En lugar de crear una nueva clase **UserActivity** cada vez que un usuario se mueve a una página nueva, puedes crear una nueva sesión para cada página. Así se conseguirá que la experiencia de lectura de la actividad sea más intuitiva y organizada.

### <a name="read-user-activities"></a>Lectura de actividades del usuario

La aplicación puede leer actividades del usuario y presentarlas al usuario, del mismo modo que lo hace la característica Línea de tiempo de Windows. Para configurar la lectura de la actividad del usuario, usa la misma instancia de **UserActivityChannel** que antes. Esta instancia puede exponer instancias de **UserActivitySessionHistoryItem**, que representan la involucración de un usuario en una actividad determinada durante un período de tiempo específico.

```Java
private ArrayList<UserActivitySessionHistoryItem> mHistoryItems; 

// ...

mHistoryItems.clear();

Log.d("UserActivityFragment", "Read");
//Async method to read activities. Last (most recent) 5 activities will be returned
AsyncOperation<UserActivitySessionHistoryItem[]> operation = mActivityChannel.getRecentUserActivitiesAsync(5);

operation.whenCompleteAsync(new AsyncOperation.ResultBiConsumer<UserActivitySessionHistoryItem[], Throwable>() {
    @Override
    public void accept(UserActivitySessionHistoryItem[] result, Throwable throwable) throws Throwable {
        if (throwable != null)
        {
            Log.d("UserActivityFragment", "Failed to read user activity!" + throwable.getMessage() + " " + throwable.getStackTrace());
        } else {
            // get the returned UserActivitySessionHistoryItems
            for (UserActivitySessionHistoryItem item : result)
            {
                mHistoryItems.add(item);
            }
        }
    }
});
```

Ahora la aplicación debe tener una lista rellenada de instancias de **UserActivitySessionHistoryItem**. Cada una de ellas puede ofrecer la actividad **UserActivity** subyacente (consulta **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)**, para obtener más información), que puedes mostrar al usuario.