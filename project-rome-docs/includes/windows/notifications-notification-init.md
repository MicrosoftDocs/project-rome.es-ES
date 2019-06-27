---
ms.openlocfilehash: f81fbbffb2ec54f8d9a252a00fc3822f1f3f9582
ms.sourcegitcommit: e95423df0e4427377ab74dbd12b0056233181d32
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/14/2019
ms.locfileid: "59800857"
---
### <a name="associate-the-connected-devices-platform-with-the-native-push-notification-for-each-platform"></a>Asociación de la plataforma de dispositivos conectados a la notificación push nativa para cada plataforma 

Como se mencionó anteriormente, los clientes de la aplicación deben proporcionar el conocimiento acerca de la canalización de las notificaciones push nativas que se usa para cada plataforma en el SDK de cliente y la plataforma de dispositivos conectados durante el proceso de registro, de forma que el servicio de notificaciones de Graph pueda realizar la distribución ramificada de las notificaciones a cada punto de conexión cliente de la aplicación cuando el servidor de aplicaciones publique una notificación destinada al usuario a través de las API de MS Graph.
En los pasos anteriores, inicializaste la plataforma sin el parámetro **NotificationProvider**. Ahora debes construir y pasar un objeto que implemente **NotificationProvider**. Consulta el archivo **GraphNotificationProvider.cs** del ejemplo para obtener más información. 



Incluye este registro en la implementación de **NotificationProvider**. A continuación, la llamada de inicialización de **Platform** debe proporcionar a la instancia de **Platform** local el acceso al servicio de notificaciones push, lo que permite que la aplicación reciba datos de las notificaciones de MS Graph en el servidor. 

### <a name="pass-incoming-push-notifications-to-the-client-sdk"></a>Paso de notificaciones push entrantes al SDK de cliente
Ahora, puedes controlar la carga entrante de UserNotification dentro de la tarea en segundo plano nativa de Windows registrada con PushNotificationTrigger o en el cliente de escucha del [evento PushNotificationReceived](https://docs.microsoft.com/en-us/uwp/api/windows.networking.pushnotifications.pushnotificationchannel.pushnotificationreceived). 

Por motivos de cumplimiento, seguridad y posibles optimizaciones, la notificación sin procesar entrante de WNS procedente de las notificaciones de Graph en el servidor podría ser con frecuencia un simple toque, que no contenga ningún dato inicialmente publicado por el servidor de aplicaciones. La recuperación del contenido real de la notificación publicada por el servidor de aplicaciones se oculta detrás de las API del SDK de cliente. En este caso, el SDK siempre pedirá al cliente de la aplicación que le pase la carga entrante de notificación sin procesar de WNS. Esto permite que el SDK determine si se trata de una notificación para escenarios de la característica Notificaciones de Graph o no (ya que el cliente de la aplicación puede usar las inserciones sin procesar de WNS para otros fines). 
