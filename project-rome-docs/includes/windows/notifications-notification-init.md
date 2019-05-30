---
ms.openlocfilehash: f81fbbffb2ec54f8d9a252a00fc3822f1f3f9582
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800857"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-platform"></a>Asociar la plataforma de dispositivos conectados a la notificación de inserción nativa para cada plataforma. 

Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de notificaciones de inserción nativa que se va a usar para cada plataforma para el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro para permitir que el gráfico servicio de notificación para enviar notificaciones cargabilidad de salida a cada punto de conexión del cliente de aplicación cuando el servidor de la aplicación publica una notificación de destinatarios de usuario a través de MS Graph API.
En los pasos anteriores, se inicializa la plataforma sin **NotificationProvider** parámetro. En este caso, deberá construir y pasar un objeto que implementa **NotificationProvider**. Consulte **GraphNotificationProvider.cs** de ejemplo para obtener más información. 



Entregar este registro en la implementación de **NotificationProvider**. A continuación, la **plataforma** llamada de inicialización debe proporcionar local **plataforma** con el acceso al servicio de notificaciones de inserción, lo que permite la aplicación para recibir datos desde el servidor de notificaciones de MS Graph. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Pasar notificaciones entrantes de inserción para el SDK de cliente
Ahora, puede controlar la carga de entrada UserNotification dentro de la tarea en segundo plano nativa registrada con PushNotificationTrigger o en el agente de escucha de Windows la [PushNotificationReceived eventos](https://docs.microsoft.com/en-us/uwp/api/windows.networking.pushnotifications.pushnotificationchannel.pushnotificationreceived). 

Por motivos incluidos posibles optimizaciones, seguridad y cumplimiento de normas, la notificación de WNS sin formato entrante procedente de las notificaciones de gráfico en el servidor podría ser a menudo una derivación de hombros que no contiene ningún dato que se publica inicialmente por el servidor de aplicaciones. La recuperación de la notificación real contenida publicada por el servidor de aplicaciones está oculta detrás de la API del SDK de cliente. En este caso, el SDK siempre le preguntará el cliente de aplicación para pasar la carga de notificación sin procesar de WNS entrante para el SDK. Esto permite que el SDK determinar si se trata de una notificación para escenarios de notificaciones de Graph o no (en caso de inserción sin procesar de WNS también puede usarse por el cliente de aplicación para otros fines). 
