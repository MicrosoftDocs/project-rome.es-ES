---
title: Publicación y lectura de actividades del usuario (iOS)
description: En esta guía se muestra cómo crear, publicar y leer en la aplicación iOS actividades del usuario basadas en Windows.
ms.topic: article
keywords: microsoft, windows, project rome, user activities, ios
ms.assetid: 445f1dd4-f3c7-46e4-a7cd-42a1fb411172
ms.localizationpriority: medium
ms.openlocfilehash: 95345d8fb4d8dd600ec0dc447ea38c29612402d1
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901683"
---
# <a name="implementing-user-activities-for-ios"></a>Implementación de Actividades del usuario para iOS

Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación. Permiten guardar una instantánea de una tarea actual para continuarla más adelante. La característica [Línea de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) muestra a los usuarios de Windows una lista desplazable de todas sus actividades recientes, representadas como tarjetas con texto y gráficos. Para obtener más información sobre las actividades del usuario en general, consulta [Continuar la actividad del usuario, incluso en diferentes dispositivos](/windows/uwp/launch-resume/useractivities). Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, consulta la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).

Con el SDK de Project Rome, la aplicación de iOS no solo puede publicar las actividades del usuario para su uso en las características de Windows como Línea de tiempo, sino que también puede actuar como punto de conexión y leer las actividades al usuario, al igual que hace la característica Línea de tiempo. Esto permite que las aplicaciones multidispositivo trasciendan por completo las plataformas y presenten experiencias que siguen a los usuarios y no a los dispositivos.

Las características de Project Rome son compatibles con una plataforma subyacente, la plataforma de dispositivos conectados. En esta guía se proporcionan los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, se explica cómo usar la plataforma para implementar características relacionadas con las actividades del usuario.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo para iOS de Project Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples), disponible en GitHub.  

Consulta en la página de [referencia de API](api-reference-for-ios.md) los vínculos a los documentos de referencia pertinentes para estos escenarios.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuración de la plataforma de dispositivos conectados y las notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Uso de la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Inicialización de un canal de actividad del usuario

Para implementar características de actividad del usuario en la aplicación, primero debes inicializar la fuente de la actividad del usuario mediante la creación de una clase MCDUserActivityChannel. Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).

Necesitarás una cuenta de usuario que haya iniciado sesión para este paso. Como en el paso anterior, puedes usar una clase del ejemplo del proveedor de autenticación para conseguir fácilmente cuentas MCDUserAccount. También necesitarás el id. de la aplicación multiplataforma, recuperado a través del registro del Panel de desarrolladores de Microsoft.
El siguiente método de la aplicación de ejemplo inicializa una clase MCDUserActivityChannel.

El siguiente método de la aplicación de ejemplo inicializa una clase MCDUserActivityChannel.

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
En este punto debes contar con una referencia a MCDUserActivityChannel en el canal.

### <a name="create-and-publish-a-user-activity"></a>Creación y publicación de una actividad del usuario

En el siguiente ejemplo de código se muestra cómo se crea una nueva instancia de **MCDUserActivity**.

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

En el siguiente método se establecen los datos visuales de **MCDUserActivity** antes de publicar la actividad. El URI de activación determinará qué acción se realiza cuando se activa la actividad (por ejemplo, cuando se selecciona en la línea de tiempo). El texto para mostrar se verá en otros dispositivos cuando vean la actividad (en la característica Línea de tiempo de Windows, por ejemplo). iconUri es un vínculo web a una imagen de icono.


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

Cuando la instancia de **MCDUserActivity** se rellena con estos datos, tiene lugar la operación de publicación.

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
> Además de las propiedades anteriores, hay muchas otras características que se pueden configurar. Para ver todos los modos en los que se puede personalizar la construcción UserActivity, consulta las clases **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)** y **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)**. Consulta recomendaciones detalladas sobre cómo diseñar actividades del usuario en la guía [Procedimientos recomendados de las actividades del usuario](/windows/uwp/launch-resume/useractivities-best-practices).

## <a name="update-an-existing-user-activity"></a>Actualización de una actividad del usuario existente

Si ya tienes una actividad y deseas actualizar su información (en el caso de una nueva involucración, un cambio de página, etc.), puedes hacerlo con **MCDUserActivitySession**. 

Una vez que has creado una sesión, la aplicación puede realizar los cambios deseados en las propiedades de la construcción **UserActivity**. Cuando hayas terminado de realizar los cambios, cierra la sesión. 

El siguiente método de la aplicación de ejemplo activa y desactiva una sesión.

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


**MCDUserActivitySession** se puede considerar como una manera de crear una clase **MCDUserActivitySessionHistoryItem** (se explica en la sección siguiente). En lugar de crear una nueva clase **MCDUserActivity** cada vez que un usuario se mueve a una página nueva, puedes crear una nueva sesión para cada página. Así se conseguirá que la experiencia de lectura de la actividad sea más intuitiva y organizada.

## <a name="read-user-activities"></a>Lectura de actividades del usuario

La aplicación puede leer actividades del usuario y presentarlas al usuario, del mismo modo que lo hace la característica Línea de tiempo de Windows. Para configurar la lectura de la actividad del usuario, usa la misma instancia de **MCDUserActivityChannel** que antes. Esta instancia puede exponer instancias de **MCDUserActivitySessionHistoryItem**, que representan la involucración de un usuario en una actividad determinada durante un período de tiempo específico.

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

Ahora la aplicación debe tener una lista rellenada de instancias de **MCDUserActivitySessionHistoryItem**. Cada una de ellas puede ofrecer la actividad **MCDUserActivity** subyacente (consulta **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)**, para obtener más información), que puedes mostrar al usuario.