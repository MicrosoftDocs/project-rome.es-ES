---
title: Publicar y leer las actividades del usuario (iOS)
description: Esta guía muestra cómo crear, publicar y leer las actividades de usuario basada en Windows en su aplicación iOS.
ms.topic: article
keywords: proyecto de Microsoft, windows, Roma, las actividades del usuario, ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 3cc19463a5e036ab76288760aa70d86f1861675b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801677"
---
# <a name="implementing-user-activities-for-ios"></a><span data-ttu-id="de56d-104">Implementación de las actividades del usuario para iOS</span><span class="sxs-lookup"><span data-stu-id="de56d-104">Implementing User Activities for iOS</span></span>

<span data-ttu-id="de56d-105">Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación.</span><span class="sxs-lookup"><span data-stu-id="de56d-105">User Activities are data constructs that represent a user's tasks within an application.</span></span> <span data-ttu-id="de56d-106">Hacen posible guardar una instantánea de una tarea actual que se puede continuar en un momento posterior.</span><span class="sxs-lookup"><span data-stu-id="de56d-106">They make it possible to save a snapshot of a current task to be continued at a later time.</span></span> <span data-ttu-id="de56d-107">El [escala de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) característica presenta a los usuarios de Windows con una lista desplazable de todas sus actividades recientes, representado como tarjetas con texto y gráficos.</span><span class="sxs-lookup"><span data-stu-id="de56d-107">The [Windows Timeline](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) feature presents Windows users with a scrollable list of all their recent activities, represented as cards with text and graphics.</span></span> <span data-ttu-id="de56d-108">Para obtener más información acerca de las actividades del usuario en general, vea [continuar con la actividad del usuario, incluso en dispositivos](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span><span class="sxs-lookup"><span data-stu-id="de56d-108">For more information about User Activities in general, see [Continue user activity, even across devices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities).</span></span> <span data-ttu-id="de56d-109">Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, vea el [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía.</span><span class="sxs-lookup"><span data-stu-id="de56d-109">For recommendations on when to create or update Activities, see the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide.</span></span>

<span data-ttu-id="de56d-110">Con el SDK de proyecto Roma, la aplicación de iOS no puede publicar solo las actividades del usuario para su uso en las características de Windows, como la escala de tiempo, pero también puede actuar como un punto de conexión y las actividades de lectura al usuario igual que lo hace la escala de tiempo.</span><span class="sxs-lookup"><span data-stu-id="de56d-110">With the Project Rome SDK, your iOS app can not only publish User Activities for use in Windows features such as Timeline, but it can also act as an endpoint and read Activities back to the user just as Timeline does.</span></span> <span data-ttu-id="de56d-111">Esto permite que las aplicaciones entre dispositivos trascender completamente sus plataformas y presentes experiencias que siguen los usuarios en lugar de los dispositivos.</span><span class="sxs-lookup"><span data-stu-id="de56d-111">This allows cross-device apps to completely transcend their platforms and present experiences that follow users rather than devices.</span></span>

<span data-ttu-id="de56d-112">Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="de56d-112">The features of Project Rome are supported by an underlying platform called the Connected Devices Platform.</span></span> <span data-ttu-id="de56d-113">Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, explica cómo usar la plataforma para implementar características relacionadas de las actividades de usuario.</span><span class="sxs-lookup"><span data-stu-id="de56d-113">This guide provides the necessary steps to get started using the Connected Devices Platform, and then explains how to use the platform to implement user activities related features.</span></span>

<span data-ttu-id="de56d-114">Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.</span><span class="sxs-lookup"><span data-stu-id="de56d-114">This steps below will reference code from the [Project Rome iOS sample app](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) that is available on GitHub.</span></span>  

<span data-ttu-id="de56d-115">Consulte la [referencia de API](api-reference-for-ios.md) página para obtener vínculos a los documentos de referencia pertinentes para estos escenarios.</span><span class="sxs-lookup"><span data-stu-id="de56d-115">See the [API reference](api-reference-for-ios.md) page for links to the reference docs relevant to these scenarios.</span></span>

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a><span data-ttu-id="de56d-116">Configurar la plataforma de dispositivos conectados y notificaciones</span><span class="sxs-lookup"><span data-stu-id="de56d-116">Setting up the Connected Devices Platform and Notifications</span></span>

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a><span data-ttu-id="de56d-117">Con la plataforma</span><span class="sxs-lookup"><span data-stu-id="de56d-117">Using the platform</span></span>

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a><span data-ttu-id="de56d-118">Inicializar un canal de la actividad del usuario</span><span class="sxs-lookup"><span data-stu-id="de56d-118">Initialize a User Activity channel</span></span>

<span data-ttu-id="de56d-119">Para implementar características de la actividad del usuario en la aplicación, primero deberá inicializar la actividad del usuario mediante la creación de un MCDUserActivityChannel de fuente.</span><span class="sxs-lookup"><span data-stu-id="de56d-119">To implement User Activity features in your app, you will first need to initialize the user activity feed by creating a MCDUserActivityChannel.</span></span> <span data-ttu-id="de56d-120">Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).</span><span class="sxs-lookup"><span data-stu-id="de56d-120">You should treat this like the Platform initialization step above: it should be checked and possibly redone whenever the app comes to the foreground (but not before Platform initialization).</span></span>

<span data-ttu-id="de56d-121">Necesitará una cuenta de usuario que inició sesión para este paso.</span><span class="sxs-lookup"><span data-stu-id="de56d-121">You will need a signed-in user account for this step.</span></span> <span data-ttu-id="de56d-122">Como anteriormente, puede usar una clase en el ejemplo de proveedor de autenticación para adquirir fácilmente el MCDUserAccount(s).</span><span class="sxs-lookup"><span data-stu-id="de56d-122">As above, you may use a class from the authentication provider sample to easily acquire the MCDUserAccount(s).</span></span> <span data-ttu-id="de56d-123">También necesitará el identificador de aplicación multiplataforma, que se ha recuperado mediante el registro del panel para desarrolladores de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="de56d-123">You will also need your cross-platform app ID, which was retrieved through the Microsoft Developer Dashboard registration.</span></span>
<span data-ttu-id="de56d-124">El método de la aplicación de ejemplo siguiente inicializa un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="de56d-124">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

<span data-ttu-id="de56d-125">El método de la aplicación de ejemplo siguiente inicializa un MCDUserActivityChannel.</span><span class="sxs-lookup"><span data-stu-id="de56d-125">The following method from the sample app initializes an MCDUserActivityChannel.</span></span>

```ObjectiveC

    // Get a UserActivity channel, getting the default channel        
    NSLog(@"Creating UserActivityChannel");
    NSArray<MCDUserAccount*>* accounts = [[AppDataSource sharedInstance].accountProvider getUserAccounts];
    MCDUserDataFeed* userDataFeed = [MCDUserDataFeed userDataFeedForAccount:accounts[0]
        platform:[AppDataSource sharedInstance].platform
        activitySourceHost:CROSS_PLATFORM_APP_ID];
    NSArray<MCDSyncScope*>* syncScopes = @[ [MCDUserActivityChannel syncScope] ];
    [userDataFeed addSyncScopes:syncScopes];
    self.channel = [MCDUserActivityChannel userActivityChannelWithUserDataFeed:userDataFeed];
}
else
{
    NSLog(@"Must have an active account to publish activities!");
    self.createActivityStatusField.text = @"Need to be logged in!";
}
```
<span data-ttu-id="de56d-126">En este momento, debe tener una referencia MCDUserActivityChannel en el canal.</span><span class="sxs-lookup"><span data-stu-id="de56d-126">At this point, you should have an MCDUserActivityChannel reference in channel.</span></span>

### <a name="create-and-publish-a-user-activity"></a><span data-ttu-id="de56d-127">Creación y publicación de una actividad de usuario</span><span class="sxs-lookup"><span data-stu-id="de56d-127">Create and publish a User Activity</span></span>

<span data-ttu-id="de56d-128">El siguiente ejemplo de código se muestra cómo una nueva **MCDUserActivity** se crea la instancia.</span><span class="sxs-lookup"><span data-stu-id="de56d-128">The following sample code shows how a new **MCDUserActivity** instance is created.</span></span>

```ObjectiveC
- (IBAction)createActivityButton:(id)sender
{
    // Step #2: Create a UserActivity
    [self.channel getOrCreateUserActivityAsync:[[NSUUID UUID] UUIDString]
        completion:^(MCDUserActivity* activity, NSError* error) {
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error creating activity!";
            }
            else if (!activity)
            {
                NSLog(@"No activity created!");
            }
            else
            {
                dispatch_async(dispatch_get_main_queue(), ^{
                    self.activity = activity;

                    // Create an activityId so the app knows so you know how to get back
                    self.activityId.text = activity.activityId;
                    self.createActivityStatusField.text = @"Created by iOSSample";
                    // Create a deep link so the app can get right back to where it was
                    self.activationUri.text = @"roman-app:";
                    self.createActivityStatusField.text = @"Activity created";
                });
            }
        }];
}
```

<span data-ttu-id="de56d-129">En el siguiente método, los datos visuales de la **MCDUserActivity** se establece antes de publica la actividad.</span><span class="sxs-lookup"><span data-stu-id="de56d-129">In the next method, the visual data of the **MCDUserActivity** is set before the Activity is published.</span></span> <span data-ttu-id="de56d-130">La activación URI determinará qué acción se realiza cuando se activa la actividad (cuando está seleccionado en la escala de tiempo, por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="de56d-130">The activation URI will determine what action is taken when the Activity is activated (when it is selected in Timeline, for example).</span></span> <span data-ttu-id="de56d-131">El texto se mostrará en otros dispositivos cuando los vean la actividad (en la escala de tiempo de Windows, por ejemplo).</span><span class="sxs-lookup"><span data-stu-id="de56d-131">The display text will be shown on other devices when they view the Activity (in Windows Timeline, for example).</span></span> <span data-ttu-id="de56d-132">El iconUri es un vínculo web a una imagen de icono.</span><span class="sxs-lookup"><span data-stu-id="de56d-132">The iconUri is a web link to an icon image.</span></span>


```ObjectiveC
- (IBAction)publishActivityButton:(id)sender
{
    self.createActivityStatusField.text = @"Saving";
    self.activity.activationUri = self.activationUri.text;
    // Set the display text for your activity.
    self.activity.visualElements.displayText = @"Visual Element, like an Adaptive Card";
    self.activity.visualElements.attribution.iconUri = @"https://www.microsoft.com/favicon.ico";

    // ...
```

<span data-ttu-id="de56d-133">Una vez el **MCDUserActivity** se rellena con estos datos, realiza la operación de publicación.</span><span class="sxs-lookup"><span data-stu-id="de56d-133">Once the **MCDUserActivity** is populated with this data, the publish operation takes place.</span></span>

```ObjectiveC
    // ...

    // Publish the Activity
    [self.activity saveAsync:^(NSError* error) {
        dispatch_async(dispatch_get_main_queue(), ^{
            if (error)
            {
                NSLog(@"%@", error);
                self.createActivityStatusField.text = @"Error saving activity";
            }
            else
            {
                self.createActivityStatusField.text = @"Saved successfully!";
                [self.sessionButton setTitle:@"Start Session" forState:normal];
            }
        });
    }];
}

mActivityId = UUID.randomUUID().toString();
mDisplayText = "Created by OneSDK Sample App";
mActivationUri = "http://contoso.com");
```
> [!TIP] 
> <span data-ttu-id="de56d-134">Además de las propiedades anteriores, hay muchas otras características que se pueden configurar.</span><span class="sxs-lookup"><span data-stu-id="de56d-134">In addition to the properties above, there are many other features that can be configured.</span></span> <span data-ttu-id="de56d-135">Para completar las distintas maneras en que se puede personalizar un UserActivity, consulte el  **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, y **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** clases.</span><span class="sxs-lookup"><span data-stu-id="de56d-135">For a complete look at the different ways that a UserActivity can be customized, see the **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, and **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** classes.</span></span> <span data-ttu-id="de56d-136">Consulte la [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía para recomendaciones detalladas sobre cómo al diseño de las actividades del usuario.</span><span class="sxs-lookup"><span data-stu-id="de56d-136">See the [User Activities best practices](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guide for detailed recommendations on how to design User Activities.</span></span>

## <a name="update-an-existing-user-activity"></a><span data-ttu-id="de56d-137">Actualización de una actividad de usuario existente</span><span class="sxs-lookup"><span data-stu-id="de56d-137">Update an existing User Activity</span></span>

<span data-ttu-id="de56d-138">Si tiene una actividad existente y desea actualizar su información (en el caso de una nueva contratación, página cambiada etc.), puede hacerlo mediante el uso de un **MCDUserActivitySession**.</span><span class="sxs-lookup"><span data-stu-id="de56d-138">If you have an existing activity and wish to update its information (in the event of a new engagement, changed page, and so on), you can do so by using a **MCDUserActivitySession**.</span></span> 

<span data-ttu-id="de56d-139">Una vez que ha creado una sesión, la aplicación puede realizar los cambios deseados a las propiedades de la **UserActivity**.</span><span class="sxs-lookup"><span data-stu-id="de56d-139">Once you've created a session, your app can make any desired changes to the properties of the **UserActivity**.</span></span> <span data-ttu-id="de56d-140">Cuando haya terminado de realizar los cambios, cierre la sesión.</span><span class="sxs-lookup"><span data-stu-id="de56d-140">When you're done making changes, close the session.</span></span> 

<span data-ttu-id="de56d-141">El método de la aplicación de ejemplo siguiente activa una sesión y se desactiva.</span><span class="sxs-lookup"><span data-stu-id="de56d-141">The following method from the sample app toggles a session on and off.</span></span>

```ObjectiveC
- (IBAction)manageSessionButton:(id)sender
{

    // Start a new a session for the UserActivity
    if (self.session == nil)
    {
       self.session = [self.activity createSession];
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has started %@", self.session);
            self.session = [self.activity createSession];
            dispatch_async(dispatch_get_main_queue(), ^{ [self.sessionButton setTitle:@"Stop Session" forState:normal]; });
        });
    }
    else
    {
        // Stop the UserActivitySession
        [self.session close];
        self.session = nil;
        dispatch_async(dispatch_get_main_queue(), ^{
            NSLog(@"UserActivitySession has stopped %@", self.session);
            [self.sessionButton setTitle:@"Start Session" forState:normal];
        });
    }
}
```


<span data-ttu-id="de56d-142">Un **MCDUserActivitySession** puede considerarse como una manera de crear un **MCDUserActivitySessionHistoryItem** (que se describe en la sección siguiente).</span><span class="sxs-lookup"><span data-stu-id="de56d-142">An **MCDUserActivitySession** can be thought of as a way to create a **MCDUserActivitySessionHistoryItem** (covered in the next section).</span></span> <span data-ttu-id="de56d-143">En lugar de crear un nuevo **MCDUserActivity** cada vez que un usuario se mueve a una página nueva, simplemente puede crear una nueva sesión para cada página.</span><span class="sxs-lookup"><span data-stu-id="de56d-143">Rather than create a new **MCDUserActivity** every time a user moves to a new page, you can simply create a new session for each page.</span></span> <span data-ttu-id="de56d-144">Esto hará que para una actividad más intuitiva y organizada de experiencia de lectura.</span><span class="sxs-lookup"><span data-stu-id="de56d-144">This will make for a more intuitive and organized activity reading experience.</span></span>

## <a name="read-user-activities"></a><span data-ttu-id="de56d-145">Leer las actividades del usuario</span><span class="sxs-lookup"><span data-stu-id="de56d-145">Read User Activities</span></span>

<span data-ttu-id="de56d-146">La aplicación puede leer las actividades del usuario y presentarlos al usuario, igual que lo hace la característica de escala de tiempo de Windows.</span><span class="sxs-lookup"><span data-stu-id="de56d-146">Your app can read User Activities and present them to the user just as the Windows Timeline feature does.</span></span> <span data-ttu-id="de56d-147">Para configurar la lectura de la actividad del usuario, use el mismo **MCDUserActivityChannel** anteriormente.</span><span class="sxs-lookup"><span data-stu-id="de56d-147">To set up User Activity reading, you use the same **MCDUserActivityChannel** instance from earlier.</span></span> <span data-ttu-id="de56d-148">Esta instancia puede exponer **MCDUserActivitySessionHistoryItem** las instancias que representan la contratación de un usuario en una actividad determinada durante un período de tiempo específico.</span><span class="sxs-lookup"><span data-stu-id="de56d-148">This instance can expose **MCDUserActivitySessionHistoryItem** instances, which represent a user's engagement in a particular Activity during a specific period of time.</span></span>

```ObjectiveC
- (IBAction)readActivityButton:(id)sender
{

    // Read/sync your UserActivities
    [self.channel getRecentUserActivitiesAsync:(NSInteger)5
        completion:^(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull result, NSError* _Nullable error) {
            dispatch_async(dispatch_get_main_queue(), ^{
                if (error)
                {
                    self.readActivityStatusField.text = @"Error reading activity!";
                }
                else if (result.count == 0)
                {
                    self.readActivityStatusField.text = @"Read completed, no activities returned";
                }
                else
                {
                    self.readActivityStatusField.text = @"Read completed!";
                    MCDUserActivitySessionHistoryItem* item = result.firstObject;
                    self.activityList.text = item.userActivity.activityId;
                    self.activityDisplay.text = item.userActivity.visualElements.displayText;
                }
            });
        }];
}
```

<span data-ttu-id="de56d-149">Ahora la aplicación debe tener una lista rellenada de **MCDUserActivitySessionHistoryItem**s.</span><span class="sxs-lookup"><span data-stu-id="de56d-149">Now your app should have a populated list of **MCDUserActivitySessionHistoryItem**s.</span></span> <span data-ttu-id="de56d-150">Cada una de ellas puede entregar subyacente **MCDUserActivity** (consulte **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** para obtener más información), que, a continuación, se puede mostrar al usuario.</span><span class="sxs-lookup"><span data-stu-id="de56d-150">Each of these can deliver the underlying **MCDUserActivity** (see **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** for details), which you can then display to the user.</span></span>
