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
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="72e29-104">Implementación de Actividades del usuario para Android</span><span class="sxs-lookup"><span data-stu-id="72e29-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="72e29-105">Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="72e29-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="72e29-106">Permiten guardar una instantánea de una tarea para continuarla más adelante.</span><span class="sxs-lookup"><span data-stu-id="72e29-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="72e29-107">La característica [Línea de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) muestra a los usuarios de Windows una lista desplazable de todas sus actividades recientes, representadas como tarjetas con texto y gráficos.</span><span class="sxs-lookup"><span data-stu-id="72e29-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="72e29-108">Para obtener más información sobre las actividades del usuario en general, consulta [Continuar la actividad del usuario, incluso en diferentes dispositivos](/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="72e29-108">For more information about User Activities in general, see [Continue user activity, even across devices](/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="72e29-109">Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, consulta la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).</span><span class="sxs-lookup"><span data-stu-id="72e29-109">For recommendations on when to create or update Activities, see the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="72e29-110">Con el SDK de Project Rome, la aplicación de Android no solo puede publicar las actividades del usuario para su uso en las características de Windows como Línea de tiempo, sino que también puede actuar como punto de conexión y leer las actividades al usuario, al igual que hace la característica Línea de tiempo en dispositivos Windows.</span><span class="sxs-lookup"><span data-stu-id="72e29-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="72e29-111">Esto permite que las aplicaciones multidispositivo trasciendan las plataformas y presenten experiencias que siguen a los usuarios y no a los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="72e29-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="72e29-112">Consulta en la página de [referencia de API](api-reference-for-android.md) los vínculos a los documentos de referencia pertinentes para estos escenarios.</span><span class="sxs-lookup"><span data-stu-id="72e29-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="72e29-113">Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo de Android para Project Rome](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="72e29-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="72e29-114">Uso de la plataforma</span><span class="sxs-lookup"><span data-stu-id="72e29-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="72e29-115">Inicialización de un canal de actividad del usuario</span><span class="sxs-lookup"><span data-stu-id="72e29-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="72e29-116">Para implementar características de actividad del usuario en la aplicación, primero debes inicializar la fuente de la actividad del usuario mediante la creación de una clase UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="72e29-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="72e29-117">Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).</span><span class="sxs-lookup"><span data-stu-id="72e29-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="72e29-118">También necesitarás el id. de la aplicación multiplataforma, recuperado a través del registro del Panel de desarrolladores de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="72e29-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="72e29-119">Los siguientes métodos inicializan una clase UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="72e29-119">The following methods initialize a UserActivityChannel.</span></span>

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

<span data-ttu-id="72e29-120">En este punto debes contar con una referencia a UserActivityChannel en el canal mActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="72e29-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="72e29-121">Creación y publicación de una actividad del usuario</span><span class="sxs-lookup"><span data-stu-id="72e29-121">Create and publish a User Activity</span></span>

<span data-ttu-id="72e29-122">A continuación, establece los datos de ID, DisplayText y ActivationURI de la que será una nueva instancia de **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="72e29-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="72e29-123">El valor de ID debe ser una cadena única.</span><span class="sxs-lookup"><span data-stu-id="72e29-123">The ID should be a unique String.</span></span> <span data-ttu-id="72e29-124">El valor de DisplayText se verá en otros dispositivos cuando vean la actividad (en la característica Línea de tiempo de Windows, por ejemplo), por lo que debe ser una descripción concisa de la actividad.</span><span class="sxs-lookup"><span data-stu-id="72e29-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="72e29-125">El valor de ActivationUri determinará qué acción se realiza cuando se activa la **UserActivity** (por ejemplo, cuando se selecciona en la línea de tiempo).</span><span class="sxs-lookup"><span data-stu-id="72e29-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="72e29-126">El código siguiente rellena datos de ejemplo para estos campos.</span><span class="sxs-lookup"><span data-stu-id="72e29-126">The following code fills in sample data for these fields.</span></span>


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

<span data-ttu-id="72e29-127">A continuación, indica un método que cree una nueva instancia de **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="72e29-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

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
<span data-ttu-id="72e29-128">Cuando tengas la instancia de **UserActivity**, rellénala con los datos definidos antes.</span><span class="sxs-lookup"><span data-stu-id="72e29-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="72e29-129">Por último, publica la actividad en la nube.</span><span class="sxs-lookup"><span data-stu-id="72e29-129">Finally, publish the Activity to the cloud.</span></span> 

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
> <span data-ttu-id="72e29-130">Además de las propiedades anteriores, hay muchas otras características que se pueden configurar.</span><span class="sxs-lookup"><span data-stu-id="72e29-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="72e29-131">Para ver todos los modos en los que se puede personalizar la construcción UserActivity, consulta las clases **[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)** y **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)**.</span><span class="sxs-lookup"><span data-stu-id="72e29-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="72e29-132">Consulta recomendaciones detalladas sobre cómo diseñar actividades del usuario en la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).</span><span class="sxs-lookup"><span data-stu-id="72e29-132">See the [User Activities best practices](/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="72e29-133">Actualización de una actividad del usuario existente</span><span class="sxs-lookup"><span data-stu-id="72e29-133">Update an existing User Activity</span></span>

<span data-ttu-id="72e29-134">Si ya tienes una actividad y deseas actualizar su información (en el caso de una nueva involucración, un cambio de página, etc.), puedes hacerlo con **UserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="72e29-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

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

<span data-ttu-id="72e29-135">Una vez que has creado una sesión, la aplicación puede realizar los cambios deseados en las propiedades de la construcción **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="72e29-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="72e29-136">Cuando hayas terminado de realizar los cambios, cierra la sesión.</span><span class="sxs-lookup"><span data-stu-id="72e29-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="72e29-137">**UserActivitySession** se puede considerar como una manera de crear una clase **UserActivitySessionHistoryItem** (se explica en la sección siguiente).</span><span class="sxs-lookup"><span data-stu-id="72e29-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="72e29-138">En lugar de crear una nueva clase **UserActivity** cada vez que un usuario se mueve a una página nueva, puedes crear una nueva sesión para cada página.</span><span class="sxs-lookup"><span data-stu-id="72e29-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="72e29-139">Así se conseguirá que la experiencia de lectura de la actividad sea más intuitiva y organizada.</span><span class="sxs-lookup"><span data-stu-id="72e29-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="72e29-140">Lectura de actividades del usuario</span><span class="sxs-lookup"><span data-stu-id="72e29-140">Read User Activities</span></span>

<span data-ttu-id="72e29-141">La aplicación puede leer actividades del usuario y presentarlas al usuario, del mismo modo que lo hace la característica Línea de tiempo de Windows.</span><span class="sxs-lookup"><span data-stu-id="72e29-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="72e29-142">Para configurar la lectura de la actividad del usuario, usa la misma instancia de **UserActivityChannel** que antes.</span><span class="sxs-lookup"><span data-stu-id="72e29-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="72e29-143">Esta instancia puede exponer instancias de **UserActivitySessionHistoryItem**, que representan la involucración de un usuario en una actividad determinada durante un período de tiempo específico.</span><span class="sxs-lookup"><span data-stu-id="72e29-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="72e29-144">Ahora la aplicación debe tener una lista rellenada de instancias de **UserActivitySessionHistoryItem**.</span><span class="sxs-lookup"><span data-stu-id="72e29-144">Now your app should have a populated list of **UserActivitySessionHistoryItem** s.</span></span> <span data-ttu-id="72e29-145">Cada una de ellas puede ofrecer la actividad **UserActivity** subyacente (consulta **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)**, para obtener más información), que puedes mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="72e29-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>