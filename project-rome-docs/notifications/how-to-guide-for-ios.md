---
title: Integración de aplicaciones de IOs con las notificaciones de Graph
description: Cómo realizar los pasos de registro necesarias para convertirse en un punto de conexión receptor para las notificaciones se publica desde el servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801317"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>Guía de procedimientos: La integración con Graph notificaciones (iOS)

Las notificaciones de Graph habilite la aplicación enviar y administrar las notificaciones de destinatarios de usuario en varios dispositivos. 

Con el SDK de cliente de proyecto Roma en iOS, puede registrar su aplicación iOS para recibir notificaciones publicadas desde el servidor de aplicaciones dirigido a un usuario que inició sesión. El SDK permite al cliente de aplicación recibir nuevas cargas de notificación entrante, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones. Para obtener más información acerca de las notificaciones y cómo habilita la entrega de notificación centrado en humanos, consulte [información general de las notificaciones de Microsoft Graph](index.md)

Todas las características en el SDK de Roma proyecto, las notificaciones de includng gráfico y mucho más, se basan en una plataforma subyacente que se llama a la plataforma de dispositivos conectados. Esta guía está diseñada para guiarle por los pasos necesarios para empezar a usar la plataforma de dispositivos conectados y explicar cómo usar las API del SDK para implementar notificaciones de Graph-características específicas.

Este pasos hará referencia a código desde el [iOS Roma de proyecto aplicación de ejemplo](https://github.com/Microsoft/project-rome/tree/master/iOS/samples) que está disponible en GitHub.  

Consulte la [referencia de API](api-reference-for-ios/index.md) página para obtener vínculos a los documentos de referencia relevantes para escenarios de notificación.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configurar la plataforma de dispositivos conectados y notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Con la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>Inicializar un canal de notificación de Graph
El SDK de proyecto Roma permite la aplicación para suscribirse a distintos canales para recibir y administrar varios tipos de datos de usuario: incluidas las notificaciones de gráfico, las actividades del usuario y mucho más. Estos son almacenados y sincronizados en **MCDUserDataFeed**. **MCDUserNotification** es el tipo de clase y los datos correspondientes a dirigida al usuario enviada una notificación a través de las notificaciones del gráfico.
Para integrar con notificación de Graph y comience a recibir MCDUserNotification publicado por el servidor de aplicaciones, primero debe inicializar los datos de usuario fuente mediante la creación de un **MCDUserNotificationChannel**. Debe tratar como el paso de inicialización de la plataforma anterior: debe ser activada y, posiblemente, puestos al día siempre que la aplicación se pone en primer plano (pero no antes de la inicialización de plataforma).

Los siguientes métodos de inicializan un **MCDUserNotificationChannel**.
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
En este momento, debe tener un **MCDUserNotificationChannel** hace referencia en `channel`.

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>Crear un MCDUserNotificationReader para recibir MCDUserNotifications entrantes y acceder al historial de MCDUserNotification
Tal como se mostró anteriormente, el APNS inicial silenciosa mensajes que llegan en el cliente de aplicación solo contiene una derivación de hombros y necesita pasar esa carga de tap hombro a la plataforma de dispositivos conectados para desencadenar el SDK para llevar a cabo una sincronización completa con el dispositivo conectado servidor, que contiene todas las MCDUserNotifications publicados por el servidor de aplicaciones. Extraerá la carga de notificación completa publicada por el servidor de aplicaciones correspondiente a este tap hombro (y en el caso si las notificaciones anteriores se han publicado, pero no se recibe en este cliente de aplicación debido a la conectividad de dispositivos u otros problemas, estará extraje también). Con estas sincronizaciones en tiempo real constantemente realizadas por el SDK, el cliente de la aplicación es capaz de tener acceso a una caché local de la fuente de datos de MCDUserNotification ha iniciado la sesión de este usuario. Un MCDUserNotificationReader en este caso permite el acceso de la aplicación cliente a esta fuente de datos: para recibir la carga de la notificación más reciente mediante el agente de escucha de eventos o tener acceso a la colección MCDUserNotification completa que se puede utilizar como modelo de vista de notificación del usuario historial.  
### <a name="receiving-mcdusernotifications"></a>Recibir MCDUserNotifications
Primero deberá crear una instancia de un MCDUserNotificationReader y obtener todas las MCDUserNotifications existentes ya en el lector si está interesado en el consumo de esa información para la experiencia que está intentando habilitar. Es seguro suponer siempre que el servidor de aplicaciones ya publicado las notificaciones se registran en el usuario, dado que este punto de conexión de dispositivo en particular podría no ser la única o el primer punto de conexión que el usuario ha instalado la aplicación. A continuación, agregue un agente de escucha de evento que se desencadena cuando la plataforma de dispositivos conectados se completa una sincronización y tiene nuevos cambios para notificarle acerca de. En el caso de las notificaciones de Graph, podrían ser nuevo nuevos cambios entrantes MCDUserNotifications publicados por las eliminaciones de aplicación de servidor o MCDUserNotifcation actualizaciones, y caducidad de las que se produjeron desde el servidor o de otros puntos de conexión registrados que el mismo usuario iniciar sesión.

> [!TIP] 
> Este agente de escucha de eventos es donde se controle la lógica de negocios principal y "usar" el contenido de la carga de la notificación basándose en sus escenarios. Si actualmente utiliza la notificación silenciosa de APNS para construir una notificación visual en el centro de notificaciones de nivel de sistema operativo, o si usa el contenido en la notificación silenciosa actualizar alguna IU en la aplicación, esto es el lugar para hacerlo. 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>Actualizar el estado de un MCDUserNotification existente
En la sección anterior, hemos mencionado que a veces un cambio MCDUserNotification recibido a través el lector podría ser una actualización de estado en una existente MCDUserNotification – si se está marcando como descartado o se marca como leído. En este caso, el cliente de la aplicación puede elegir qué hacer, como la habilitación de universal descartar mediante la eliminación de la notificación visual correspondiente en este dispositivo concreto. Dar un paso atrás, el cliente de aplicación es a menudo la que inició esta actualización de cambio MCDUserNotification para comenzar: desde un dispositivo diferente. Puede elegir el momento para actualizar el estado de su MCDUserNotifications, pero normalmente se actualizan cuando la notificación visual correspondiente se controla por el usuario en ese dispositivo o la notificación es aún más controlada por el usuario en algo de experiencia en la aplicación habilitar. Este es un ejemplo del aspecto que podría tener el flujo: El servidor de la aplicación publica una notificación dirigida a los usuarios a. usuario A recibe esta notificación en su PC y su teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en PC y realiza un seguimiento en la aplicación a los controladores de la tarea correspondiente. El cliente de aplicación en este equipo, a continuación, llamará a conectado de Platform SDK de dispositivos para actualizar el estado de la notificación de usuario correspondiente para disponer de esta actualización sincronizar en todos los dispositivos de este usuario. Los demás clientes de aplicación, al recibir este estado de actualización en tiempo real, se, a continuación, quitará la alerta correspondiente visual /Message / notificación desde el centro de notificaciones del dispositivo del sistema / bandeja notificación / acción Center. Se trata cómo notificaciones obtengan descartar universalmente en todos los dispositivos del usuario. 

> [!TIP]
> Clase MCDUserNotification proporciona actualmente 2 tipos de actualizaciones de estado, puede modificar el MCDUserNotificationReadState o la MCDUserNotificationUserActionState y definir su propia lógica de qué debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puede marcar el estado de acción para ser activado o descartada y descartar la dinamización de ese valor para implementar universal. Como alternativa, o al mismo tiempo, se puede marcar leer el estado como de lectura o no leído y se basa en que determinan qué notificaciones deben mostrarse en la vista de historial de notificación en aplicación. 

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
