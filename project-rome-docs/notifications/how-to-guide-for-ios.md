---
title: Integración de aplicaciones de IOs con las notificaciones de Graph
description: Procedimiento para realizar los pasos de registro necesarios para convertirte en un punto de conexión de recepción de notificaciones publicadas desde tu servidor de aplicaciones.
ms.assetid: c973d534-08e9-4f6e-8b54-bcae97067961
ms.localizationpriority: medium
ms.custom: seodec18
ms.openlocfilehash: 889d2a72752a01b60ab1585dd3d4f78624b2b214
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "59801317"
---
# <a name="how-to-guide-integrating-with-graph-notifications-ios"></a>Guía de procedimientos: Integración con las notificaciones de Graph (iOS)

Las notificaciones de Graph permiten a la aplicación enviar y administrar notificaciones destinadas al usuario en múltiples dispositivos. 

Con el SDK del lado cliente de Project Rome en iOS, tu aplicación de iOS puede registrarse para recibir notificaciones publicadas desde tu servidor de aplicaciones destinadas a un usuario conectado. El SDK permite al cliente de la aplicación recibir nuevas cargas útiles de notificaciones entrantes, administrar el estado de las notificaciones existentes y recuperar el historial de notificaciones. Para obtener más información acerca de las notificaciones y cómo permiten la entrega de notificaciones centradas en las personas, consulta [Notificaciones de Microsoft Graph](index.md).

Todas las características del SDK de Project Rome, incluidas las notificaciones de Graph y otras, están construidas sobre una plataforma subyacente llamada plataforma de dispositivos conectados. Esta guía está diseñada para guiarte por los pasos necesarios para empezar a utilizar la plataforma de dispositivos conectados y para explicar cómo consumir API en el SDK para implementar características específicas de las notificaciones de Graph.

Los pasos siguientes hacen referencia a código de la [aplicación de ejemplo para iOS de Project Rome](https://github.com/Microsoft/project-rome/tree/master/iOS/samples), disponible en GitHub.  

Consulta en la página de [referencia de API](api-reference-for-ios/index.md) los vínculos a los documentos de referencia pertinentes para escenarios de notificación.

## <a name="setting-up-the-connected-devices-platform-and-notifications"></a>Configuración de la plataforma de dispositivos conectados y las notificaciones

[!INCLUDE [ios/preliminary-setup](../includes/ios/preliminary-setup.md)]

[!INCLUDE [auth-scopesiOS](../includes/auth-scopesiOS.md)]

[!INCLUDE [ios/dev-center-onboarding](../includes/ios/notifications-dev-center-onboarding.md)]

## <a name="using-the-platform"></a>Uso de la plataforma

[!INCLUDE [ios/create-setup-events-start-platform](../includes/ios/create-setup-events-start-platform.md)]

## <a name="initialize-a-graph-notification-channel"></a>Inicialización de un canal de notificaciones de Graph
El SDK de Project Rome permite que la aplicación se suscriba a diferentes canales para recibir y administrar diferentes tipos de datos de usuario, incluidas las notificaciones de Graph y las actividades de usuario entre otras. Todos ellos se almacenan y sincronizan en **MCDUserDataFeed**. **MCDUserNotification** es la clase y el tipo de datos correspondiente a una notificación destinada al usuario enviada mediante las notificaciones de Graph.
Para la integración con las notificaciones de Graph y comenzar a recibir la MCDUserNotification publicada por tu servidor de aplicaciones, primero es necesario inicializar la fuente de datos de usuario mediante la creación de una clase **MCDUserNotificationChannel**. Debes tratar este paso como el paso anterior de inicialización de la plataforma: debe comprobarse y, posiblemente, rehacerse siempre que la aplicación pasa al primer plano (pero no antes de la inicialización de la plataforma).

Los siguientes métodos inicializan una clase **MCDUserNotificationChannel**.
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
En este momento, deberías tener una referencia a la clase **MCDUserNotificationChannel** en `channel`.

## <a name="create-a-mcdusernotificationreader-to-receive-incoming-mcdusernotifications-and-access-mcdusernotification-history"></a>Creación de una clase MCDUserNotificationReader para recibir MCDUserNotifications entrantes y acceder al historial de MCDUserNotification.
Como se mostró anteriormente, la notificación inicial de APNS que llega al cliente de la aplicación solo contiene un toque de atención, y es necesario pasar esa carga útil del toque de atención a la plataforma de dispositivos conectados para que el SDK realice una sincronización completa con el servidor de dispositivos conectados, que contiene todas las MCDUserNotifications publicadas por el servidor de aplicaciones. Esto reducirá la carga útil de la notificación completa publicada por tu servidor de aplicaciones correspondiente a ese toque de atención (y en caso de que se publicaran notificaciones previas pero no se recibieran en este cliente de la aplicación debido a la conectividad del dispositivo u otros problemas, también se reducirán). Con estas sincronizaciones en tiempo real realizadas constantemente por el SDK, el cliente de la aplicación puede tener acceso a una caché local de la fuente de datos de MCDUserNotification del usuario que ha iniciado sesión. En este caso, una clase MCDUserNotificationReader permite al cliente de la aplicación acceder a esta fuente de datos para recibir la última carga útil de la notificación a través de la escucha de eventos; o bien para acceder a la colección completa de MCDUserNotification que puede utilizarse como modelo de visualización del historial de notificaciones del usuario.  
### <a name="receiving-mcdusernotifications"></a>Recepción de MCDUserNotifications
Primero es necesario crear una instancia de MCDUserNotificationReader y obtener todas las MCDUserNotifications existentes ya en la escucha si estás interesado en consumir esa información para la experiencia que estás intentando habilitar. Es seguro asumir siempre que el servidor de aplicaciones ya ha publicado notificaciones a este usuario conectado, ya que el punto de conexión de este dispositivo puede no ser el único o el primer punto de conexión en el que el usuario ha instalado su aplicación. A continuación, agrega una escucha de eventos que se activará cuando la plataforma de dispositivos conectados complete una sincronización y tenga nuevos cambios que notificarte. En el caso de las notificaciones de Graph, los nuevos cambios pueden ser nuevas MCDUserNotifications entrantes publicadas por tu servidor de aplicaciones; o bien actualizaciones, eliminaciones y expiraciones de MCDUserNotifcation que ocurrieron desde el servidor o desde otros puntos de conexión registrados en los que inició sesión el mismo usuario.

> [!TIP] 
> En esta escucha de eventos es donde se controla la lógica principal del negocio y "consume" el contenido de la carga útil de la notificación en función en tus escenarios. Si utilizas la notificación sin procesar de APNS para crear una notificación visual en el centro de notificaciones a nivel de sistema operativo o si utilizas el contenido de la notificación para actualizar una interfaz de usuario en la aplicación, este es el lugar para hacerlo. 

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

## <a name="update-the-state-of-an-existing-mcdusernotification"></a>Actualización del estado de una clase MCDUserNotification existente
En la sección anterior se mencionó que a veces un cambio en MCDUserNotification recibido a través de la escucha puede ser una actualización de estado de una MCDUserNotification existente, independientemente de si está marcada como descartada o como leída. En este caso, el cliente de la aplicación puede elegir qué hacer; por ejemplo, habilitar el descarte universal al eliminar la notificación visual correspondiente en este dispositivo concreto. Dando un paso atrás, el cliente de la aplicación es a menudo el que inició esta actualización de cambio de MCDUserNotification desde otro dispositivo. Puedes elegir la hora para actualizar el estado de tus MCDUserNotifications, pero normalmente se actualizan cuando el usuario controla la notificación visual correspondiente en ese dispositivo o en alguna experiencia en la aplicación que habilites. Aquí te mostramos un ejemplo del flujo que verás: El servidor de aplicaciones publica una notificación destinada al usuario A. El usuario A recibe esta notificación tanto en su PC como en el teléfono donde están instalados los clientes de la aplicación. El usuario hace clic en la notificación en su PC y se dirige a la aplicación para controlar la tarea correspondiente. El cliente de la aplicación en su PC llamará al SDK de la plataforma de dispositivos conectados para actualizar el estado de la notificación de usuario correspondiente con el fin de sincronizar esta actualización en todos los dispositivos de este usuario. Los demás clientes de la aplicación, al recibir esta actualización de estado en tiempo real, eliminarán la alerta visual, mensaje o notificación del sistema correspondiente del centro de notificación, la bandeja de notificación o el centro de actividades del dispositivo. Así es como las notificaciones se descartan universalmente en los dispositivos de un usuario. 

> [!TIP]
> Actualmente, la clase MCDUserNotification proporciona dos tipos de actualizaciones de estado: puedes modificar MCDUserNotificationReadState o MCDUserNotificationUserActionState y definir tu propia lógica sobre lo que debe ocurrir cuando se actualizan las notificaciones. Por ejemplo, puedes marcar la acción para que esté activada o descartada y basarte en ese valor para implementar el descarte universal. Si lo prefieres, o al mismo tiempo, puedes marcar el estado de lectura como leído o no leído y, en función de ello, determinar qué notificaciones deben aparecer en la vista del historial de notificaciones en la aplicación. 

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
