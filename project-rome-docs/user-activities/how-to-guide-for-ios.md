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
# <a name="implementing-user-activities-for-ios"></a>Implementación de las actividades del usuario para iOS

Las actividades del usuario son construcciones de datos que representan las tareas de un usuario dentro de una aplicación. Hacen posible guardar una instantánea de una tarea actual que se puede continuar en un momento posterior. El [escala de tiempo de Windows](https://blogs.windows.com/windowsexperience/2018/04/27/make-the-most-of-your-time-with-the-new-windows-10-update/) característica presenta a los usuarios de Windows con una lista desplazable de todas sus actividades recientes, representado como tarjetas con texto y gráficos. Para obtener más información acerca de las actividades del usuario en general, vea [continuar con la actividad del usuario, incluso en dispositivos](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities). Para obtener recomendaciones sobre cuándo crear o actualizar las actividades, vea el [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía.

Con el SDK de proyecto Roma, la aplicación de iOS no puede publicar solo las actividades del usuario para su uso en las características de Windows, como la escala de tiempo, pero también puede actuar como un punto de conexión y las actividades de lectura al usuario igual que lo hace la escala de tiempo. Esto permite que las aplicaciones entre dispositivos trascender completamente sus plataformas y presentes experiencias que siguen los usuarios en lugar de los dispositivos.

Se admiten las características de proyecto Roma una plataforma subyacente que se llama a la plataforma de dispositivos conectados. Esta guía proporciona los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y, a continuación, explica cómo usar la plataforma para implementar características relacionadas de las actividades de usuario.

Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.  

Consulte la [referencia de API](api-reference-for-ios.md) página para obtener vínculos a los documentos de referencia pertinentes para estos escenarios.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configurar la plataforma de dispositivos conectados y notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Con la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

### <a name="initialize-a-user-activity-channel"></a>Inicializar un canal de la actividad del usuario

Para implementar características de la actividad del usuario en la aplicación, primero deberá inicializar la actividad del usuario mediante la creación de un MCDUserActivityChannel de fuente. Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).

Necesitará una cuenta de usuario que inició sesión para este paso. Como anteriormente, puede usar una clase en el ejemplo de proveedor de autenticación para adquirir fácilmente el MCDUserAccount(s). También necesitará el identificador de aplicación multiplataforma, que se ha recuperado mediante el registro del panel para desarrolladores de Microsoft.
El método de la aplicación de ejemplo siguiente inicializa un MCDUserActivityChannel.

El método de la aplicación de ejemplo siguiente inicializa un MCDUserActivityChannel.

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
En este momento, debe tener una referencia MCDUserActivityChannel en el canal.

### <a name="create-and-publish-a-user-activity"></a>Creación y publicación de una actividad de usuario

El siguiente ejemplo de código se muestra cómo una nueva **MCDUserActivity** se crea la instancia.

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

En el siguiente método, los datos visuales de la **MCDUserActivity** se establece antes de publica la actividad. La activación URI determinará qué acción se realiza cuando se activa la actividad (cuando está seleccionado en la escala de tiempo, por ejemplo). El texto se mostrará en otros dispositivos cuando los vean la actividad (en la escala de tiempo de Windows, por ejemplo). El iconUri es un vínculo web a una imagen de icono.


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

Una vez el **MCDUserActivity** se rellena con estos datos, realiza la operación de publicación.

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
> Además de las propiedades anteriores, hay muchas otras características que se pueden configurar. Para completar las distintas maneras en que se puede personalizar un UserActivity, consulte el  **[MCDUserActivity](../objectivec-api/userdata.useractivities/MCDUserActivity.md)**, **[MCDUserActivityVisualElements](../objectivec-api/userdata.useractivities/MCDUserActivityVisualElements.md)**, y **[MCDUserActivityAttribution](../objectivec-api/userdata.useractivities/MCDUserActivityAttribution.md)** clases. Consulte la [prácticas recomendadas de las actividades del usuario](https://docs.microsoft.com/windows/uwp/launch-resume/useractivities-best-practices) guía para recomendaciones detalladas sobre cómo al diseño de las actividades del usuario.

## <a name="update-an-existing-user-activity"></a>Actualización de una actividad de usuario existente

Si tiene una actividad existente y desea actualizar su información (en el caso de una nueva contratación, página cambiada etc.), puede hacerlo mediante el uso de un **MCDUserActivitySession**. 

Una vez que ha creado una sesión, la aplicación puede realizar los cambios deseados a las propiedades de la **UserActivity**. Cuando haya terminado de realizar los cambios, cierre la sesión. 

El método de la aplicación de ejemplo siguiente activa una sesión y se desactiva.

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


Un **MCDUserActivitySession** puede considerarse como una manera de crear un **MCDUserActivitySessionHistoryItem** (que se describe en la sección siguiente). En lugar de crear un nuevo **MCDUserActivity** cada vez que un usuario se mueve a una página nueva, simplemente puede crear una nueva sesión para cada página. Esto hará que para una actividad más intuitiva y organizada de experiencia de lectura.

## <a name="read-user-activities"></a>Leer las actividades del usuario

La aplicación puede leer las actividades del usuario y presentarlos al usuario, igual que lo hace la característica de escala de tiempo de Windows. Para configurar la lectura de la actividad del usuario, use el mismo **MCDUserActivityChannel** anteriormente. Esta instancia puede exponer **MCDUserActivitySessionHistoryItem** las instancias que representan la contratación de un usuario en una actividad determinada durante un período de tiempo específico.

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

Ahora la aplicación debe tener una lista rellenada de **MCDUserActivitySessionHistoryItem**s. Cada una de ellas puede entregar subyacente **MCDUserActivity** (consulte **[MCDUserActivitySessionHistoryItem](../objectivec-api/userdata.useractivities/MCDUserActivitySessionHistoryItem.md)** para obtener más información), que, a continuación, se puede mostrar al usuario.
