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
# <a name="implementing-user-activities-for-android"></a><span data-ttu-id="c60af-104">Implementación de las actividades del usuario para Android</span><span class="sxs-lookup"><span data-stu-id="c60af-104">Implementing User Activities for Android</span></span>

<span data-ttu-id="c60af-105">Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="c60af-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="c60af-106">Hacen posible guardar una instantánea de una tarea que se puede continuar en un momento posterior.</span><span class="sxs-lookup"><span data-stu-id="c60af-106">They make it possible to save a snapshot of a task to be continued at a later time.</span></span> <span data-ttu-id="c60af-107">El [escala de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) característica presenta a los usuarios de Windows con una lista desplazable de todas sus actividades recientes, representado como tarjetas con texto y gráficos.</span><span class="sxs-lookup"><span data-stu-id="c60af-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="c60af-108">Para obtener más información acerca de las actividades del usuario en general, vea [continuar con la actividad del usuario, incluso en dispositivos](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="c60af-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="c60af-109">Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, vea el [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía.</span><span class="sxs-lookup"><span data-stu-id="c60af-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="c60af-110">Con el SDK de proyecto Roma, la aplicación Android puede no sólo publicar las actividades del usuario para su uso en las características de Windows, como la escala de tiempo, pero puede también actúan como un punto de conexión y leer las actividades al usuario igual escala de tiempo en los dispositivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="c60af-110">With the Project Rome SDK, your Android app can not only publish User Activities for use in Windows features such as Timeline, but can also act as an endpoint and read Activities back to the user just as Timeline does on Windows devices.</span></span> <span data-ttu-id="c60af-111">Esto permite que las aplicaciones entre dispositivos trascender sus plataformas y proporcionan experiencias que siguen los usuarios en lugar de los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="c60af-111">This allows cross-device apps to transcend their platforms and provide experiences that follow users rather than devices.</span></span>  

<span data-ttu-id="c60af-112">Consulte la [referencia de API](api-reference-for-android.md) página para obtener vínculos a los documentos de referencia pertinentes para estos escenarios.</span><span class="sxs-lookup"><span data-stu-id="c60af-112">See the [API reference](api-reference-for-android.md) page for links to the reference docs relevant to these scenarios.</span></span>

<span data-ttu-id="c60af-113">Este pasos hará referencia a código desde el [Roma Android de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span><span class="sxs-lookup"><span data-stu-id="c60af-113">This steps below will reference code from the [Project Rome Android sample app](https://github.com/Microsoft/project-rome/tree/master/Android/samples).</span></span>

[!INCLUDE [android/dev-reqs](../includes/android/dev-reqs.md)]

[!INCLUDE [android/preliminary-setup](../includes/android/preliminary-setup.md)]

[!INCLUDE [android/auth-scopes](../includes/auth-scopes.md)]

[!INCLUDE [android/dev-center-onboarding](../includes/android/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="c60af-114">Con la plataforma</span><span class="sxs-lookup"><span data-stu-id="c60af-114">Using the platform</span></span>

[!INCLUDE [android/create-setup-events-start-platform](../includes/android/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="c60af-115">Inicializar un canal de la actividad del usuario</span><span class="sxs-lookup"><span data-stu-id="c60af-115">Initialize a User Activity channel</span></span>

<span data-ttu-id="c60af-116">Para implementar características de la actividad del usuario en la aplicación, primero deberá inicializar la actividad del usuario mediante la creación de un UserActivityChannel de fuente.</span><span class="sxs-lookup"><span data-stu-id="c60af-116">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a UserActivityChannel.</span></span> <span data-ttu-id="c60af-117">Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).</span><span class="sxs-lookup"><span data-stu-id="c60af-117">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="c60af-118">También necesitará el identificador de aplicación multiplataforma, que se ha recuperado mediante el registro del panel para desarrolladores de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c60af-118">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="c60af-119">Los siguientes métodos de inicializan un UserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="c60af-119">The following methods initialize a UserActivityChannel.</span></span>

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

<span data-ttu-id="c60af-120">En este momento, debe tener una referencia UserActivityChannel en mActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="c60af-120">At this point, you should have a UserActivityChannel reference in mActivityChannel.</span></span>


### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="c60af-121">Creación y publicación de una actividad de usuario</span><span class="sxs-lookup"><span data-stu-id="c60af-121">Create and publish a User Activity</span></span>

<span data-ttu-id="c60af-122">A continuación, establezca los datos del identificador, DisplayText y ActivationURI de cuál será un nuevo **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="c60af-122">Next, set the ID, DisplayText and ActivationURI data of what will be a new **UserActivity**.</span></span> <span data-ttu-id="c60af-123">El identificador debe ser una cadena única.</span><span class="sxs-lookup"><span data-stu-id="c60af-123">The ID should be a unique String.</span></span> <span data-ttu-id="c60af-124">Se mostrará el texto para mostrar en otros dispositivos cuando los vean la actividad (en Windows escala de tiempo, por ejemplo), por lo que debe ser una descripción breve de la actividad.</span><span class="sxs-lookup"><span data-stu-id="c60af-124">The DisplayText will be shown on other devices when they view the Activity (in Windows Timeline, for example), so it should be a concise description of the activity.</span></span> <span data-ttu-id="c60af-125">El ActivationUri determinará qué acción se realiza cuando el **UserActivity** está activado (cuando está seleccionado en la escala de tiempo, por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="c60af-125">The ActivationUri will determine what action is taken when the **UserActivity** is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="c60af-126">El código siguiente rellena de datos de ejemplo para estos campos.</span><span class="sxs-lookup"><span data-stu-id="c60af-126">The following code fills in sample data for these fields.</span></span>


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

<span data-ttu-id="c60af-127">A continuación, proporcionar un método que crea un nuevo **UserActivity** instancia.</span><span class="sxs-lookup"><span data-stu-id="c60af-127">Next, provide a method that creates a new **UserActivity** instance.</span></span>

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
<span data-ttu-id="c60af-128">Una vez que tenga el **UserActivity** de la instancia, rellenarla con los datos definidos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c60af-128">Once you have the **UserActivity** instance, populate it with the data defined above.</span></span>

```Java
//set the properties of the UserActivity:
// Display Text will be shown when the UserActivity is viewed on other devices
mActivity.getVisualElements().setDisplayText(mDisplayText);
// ActivationURI will determine what is launched when your UserActivity is activated from other devices
mActivity.setActivationUri(mActivationUri);
```

<span data-ttu-id="c60af-129">Por último, puede publicar la actividad en la nube.</span><span class="sxs-lookup"><span data-stu-id="c60af-129">Finally, publish the Activity to the cloud.</span></span> 

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
> <span data-ttu-id="c60af-130">Además de las propiedades anteriores, hay muchas otras características que se pueden configurar.</span><span class="sxs-lookup"><span data-stu-id="c60af-130">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="c60af-131">Para completar las distintas maneras en que se puede personalizar un UserActivity, consulte el  **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, y **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** clases.</span><span class="sxs-lookup"><span data-stu-id="c60af-131">For a complete look at the different ways that a UserActivity can be customized, see the **[UserActivity](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity)**, **[UserActivityVisualElements](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_visual_elements)**, and **[UserActivityAttribution](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_attribution)** classes.</span></span> <span data-ttu-id="c60af-132">Consulte la [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía para recomendaciones detalladas sobre cómo al diseño de las actividades del usuario.</span><span class="sxs-lookup"><span data-stu-id="c60af-132">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

### <a name="update-an-existing-user-activity"></a><span data-ttu-id="c60af-133">Actualización de una actividad de usuario existente</span><span class="sxs-lookup"><span data-stu-id="c60af-133">Update an existing User Activity</span></span>

<span data-ttu-id="c60af-134">Si tiene una actividad existente y desea actualizar su información (en el caso de una nueva contratación, página cambiada etc.), puede hacerlo mediante el uso de un **UserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="c60af-134">If you have an existing Activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **UserActivitySession**.</span></span>

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

<span data-ttu-id="c60af-135">Una vez que ha creado una sesión, la aplicación puede realizar los cambios deseados a las propiedades de la **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="c60af-135">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="c60af-136">Cuando haya terminado de realizar los cambios, cierre la sesión.</span><span class="sxs-lookup"><span data-stu-id="c60af-136">When you're done making changes, close the session.</span></span> 

```Java
mActivitySession.close();
mActivitySession = null;
Log.d("UserActivityFragment", "Stopping");
```

<span data-ttu-id="c60af-137">Un **UserActivitySession** puede considerarse como una manera de crear un **UserActivitySessionHistoryItem** (que se describe en la sección siguiente).</span><span class="sxs-lookup"><span data-stu-id="c60af-137">A **UserActivitySession** can be thought of as a way to create a **UserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="c60af-138">En lugar de crear un nuevo **UserActivity** cada vez que un usuario se mueve a una página nueva, simplemente puede crear una nueva sesión para cada página.</span><span class="sxs-lookup"><span data-stu-id="c60af-138">Rather than create a new **UserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="c60af-139">Esto hará que para una actividad más intuitiva y organizada de experiencia de lectura.</span><span class="sxs-lookup"><span data-stu-id="c60af-139">This will make for a more intuitive and organized activity reading experience.</span></span>

### <a name="read-user-activities"></a><span data-ttu-id="c60af-140">Leer las actividades del usuario</span><span class="sxs-lookup"><span data-stu-id="c60af-140">Read User Activities</span></span>

<span data-ttu-id="c60af-141">La aplicación puede leer las actividades del usuario y presentarlos al usuario, igual que lo hace la característica de escala de tiempo de Windows.</span><span class="sxs-lookup"><span data-stu-id="c60af-141">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="c60af-142">Para configurar la lectura de la actividad del usuario, use el mismo **UserActivityChannel** anteriormente.</span><span class="sxs-lookup"><span data-stu-id="c60af-142">To set up User Activity reading, use the same **UserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="c60af-143">Esta instancia puede exponer **UserActivitySessionHistoryItem** las instancias que representan la contratación de un usuario en una actividad determinada durante un período de tiempo específico.</span><span class="sxs-lookup"><span data-stu-id="c60af-143">This instance can expose **UserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

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

<span data-ttu-id="c60af-144">Ahora la aplicación debe tener una lista rellenada de **UserActivitySessionHistoryItem**s.</span><span class="sxs-lookup"><span data-stu-id="c60af-144">Now your app should have a populated list of **UserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="c60af-145">Cada una de ellas puede entregar subyacente **UserActivity** (consulte **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** para obtener más información), que, a continuación, se puede mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="c60af-145">Each of these can deliver the underlying **UserActivity** (see **[UserActivitySessionHistoryItem](https://docs.microsoft.com/java/api/com.microsoft.connecteddevices.useractivities._user_activity_session_history_item)** for details), which you can then display to the user.</span></span>
