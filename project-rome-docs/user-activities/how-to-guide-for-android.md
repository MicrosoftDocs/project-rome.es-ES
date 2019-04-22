---
title: Publicar y leer las actividades del usuario (Android)
description: Esta guía muestra cómo crear, publicar y leer las actividades de usuario basada en Windows en su aplicación Android.
ms.topic: article
keywords: proyecto de Microsoft, windows, Roma, las actividades del usuario, android
ms.assetid: 8cfb7544-913c-48c0-8528-52b93ba8b0c6
ms.localizationpriority: medium
ms.openlocfilehash: 67f793341a108853d5b36e062fd04f441efff473
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801537"
---
# <a name="implementing-user-activities-for-android"></a>Implementación de las actividades del usuario para Android

Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación. Hacen posible guardar una instantánea de una tarea que se puede continuar en un momento posterior. El [escala de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) característica presenta a los usuarios de Windows con una lista desplazable de todas sus actividades recientes, representado como tarjetas con texto y gráficos. Para obtener más información acerca de las actividades del usuario en general, vea [continuar con la actividad del usuario, incluso en dispositivos](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, vea el [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía.

Con el SDK de proyecto Roma, la aplicación Android puede no sólo publicar las actividades del usuario para su uso en las características de Windows, como la escala de tiempo, pero puede también actúan como un punto de conexión y leer las actividades al usuario igual escala de tiempo en los dispositivos de Windows. Esto permite que las aplicaciones entre dispositivos trascender sus plataformas y proporcionan experiencias que siguen los usuarios en lugar de los dispositivos.  

Consulte la [referencia de API](api-reference-for-android.md) página para obtener vínculos a los documentos de referencia pertinentes para estos escenarios.

Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Con la plataforma

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Inicializar un canal de la actividad del usuario

Para implementar características de la actividad del usuario en la aplicación, primero deberá inicializar la actividad del usuario mediante la creación de un UserActivityChannel de fuente. Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).

También necesitará el identificador de aplicación multiplataforma, que se ha recuperado mediante el registro del panel para desarrolladores de Microsoft.
Los siguientes métodos de inicializan un UserActivityChannel.

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

En este momento, debe tener una referencia UserActivityChannel en mActivityChannel.


### <a name="create-and-publish-a-user-activity"></a>Creación y publicación de una actividad de usuario

A continuación, establezca los datos del identificador, DisplayText y ActivationURI de cuál será un nuevo **UserActivity**. El identificador debe ser una cadena única. Se mostrará el texto para mostrar en otros dispositivos cuando los vean la actividad (en Windows escala de tiempo, por ejemplo), por lo que debe ser una descripción breve de la actividad. El ActivationUri determinará qué acción se realiza cuando el **UserActivity** está activado (cuando está seleccionado en la escala de tiempo, por ejemplo). El código siguiente rellena de datos de ejemplo para estos campos.


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

A continuación, proporcionar un método que crea un nuevo **UserActivity** instancia.

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
Una vez que tenga el **UserActivity** de la instancia, rellenarla con los datos definidos anteriormente.

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

Por último, puede publicar la actividad en la nube. 

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
> Además de las propiedades anteriores, hay muchas otras características que se pueden configurar. Para completar las distintas maneras en que se puede personalizar un UserActivity, consulte el  **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, y **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** clases. Consulte la [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía para recomendaciones detalladas sobre cómo al diseño de las actividades del usuario.

### <a name="update-an-existing-user-activity"></a>Actualización de una actividad de usuario existente

Si tiene una actividad existente y desea actualizar su información (en el caso de una nueva contratación, página cambiada etc.), puede hacerlo mediante el uso de un **UserActivitySession**.

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

Una vez que ha creado una sesión, la aplicación puede realizar los cambios deseados a las propiedades de la **UserActivity**. Cuando haya terminado de realizar los cambios, cierre la sesión. 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

Un **UserActivitySession** puede considerarse como una manera de crear un **UserActivitySessionHistoryItem** (que se describe en la sección siguiente). En lugar de crear un nuevo **UserActivity** cada vez que un usuario se mueve a una página nueva, simplemente puede crear una nueva sesión para cada página. Esto hará que para una actividad más intuitiva y organizada de experiencia de lectura.

### <a name="read-user-activities"></a>Leer las actividades del usuario

La aplicación puede leer las actividades del usuario y presentarlos al usuario, igual que lo hace la característica de escala de tiempo de Windows. Para configurar la lectura de la actividad del usuario, use el mismo **UserActivityChannel** anteriormente. Esta instancia puede exponer **UserActivitySessionHistoryItem** las instancias que representan la contratación de un usuario en una actividad determinada durante un período de tiempo específico.

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

Ahora la aplicación debe tener una lista rellenada de **UserActivitySessionHistoryItem**s. Cada una de ellas puede entregar subyacente **UserActivity** (consulte **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** para obtener más información), que, a continuación, se puede mostrar al usuario.
