---
title: Notificaciones de Microsoft Graph
description: Incluya notificaciones de Microsoft Graph en su aplicación para volver a interactuar con los usuarios de forma centrada en el ser humano.
ms.localizationpriority: medium
ms.topic: overview
ms.custom: seodec2018
ms.openlocfilehash: 8a44c645a60848c9bc3c92e61675993eb63f3bc1
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901633"
---
# <a name="microsoft-graph-notifications"></a>Notificaciones de Microsoft Graph
Las notificaciones son la manera más eficaz volver a interactuar con los usuarios. Captan la atención de los usuarios y los devuelven a la aplicación. En un mundo multidispositivo, los usuarios pueden acceder a las aplicaciones y los servicios desde cualquier lugar, en distintas plataformas y dispositivos donde las aplicaciones estén presentes.
Los escenarios de notificación deben diseñarse de forma "centrada en el ser humano", y su objetivo principal será notificar al usuario, estén donde estén. Las soluciones de notificación existentes proporcionadas por las principales plataformas son excelentes para dirigirse a los dispositivos. Las notificaciones de Microsoft Graph van más allá y permiten dirigirse al usuario. Las notificaciones de Microsoft Graph se encargarán del trabajo pesado, incluida la asignación entre los usuarios y los puntos de conexión, la sincronización de estado de la notificación en los distintos puntos de conexión de los usuarios, y mucho más.

## <a name="why-integrate-with-microsoft-graph-notifications"></a>¿Por qué realizar la integración con las notificaciones de Microsoft Graph?

### <a name="deliver-notifications-to-a-user-across-different-endpoints"></a>Entrega de notificaciones a un usuario en distintos puntos de conexión
Como parte de Microsoft Graph, la API de notificaciones permite dirigirse a una cuenta Microsoft, o una cuenta profesional o educativa (Azure Active Directory), para entregar una notificación. La plataforma distribuye esta notificación a todos los puntos de conexión de los usuarios, incluidos iOS, Android y UWP de Windows.

### <a name="manage-notifications-across-endpoints"></a>Administración de las notificaciones en todos los puntos de conexión
La API de notificaciones de Microsoft Graph permite actualizar el estado de una notificación y sincronizarlo en todos los puntos de conexión. Por ejemplo, cuando un usuario actúa sobre una notificación en un dispositivo, puede actualizar el estado de esta notificación (por ejemplo, marcada como leída o descartada) y el mismo cambio de estado se distribuirá a todos los demás puntos de conexión. La API de notificaciones de Microsoft Graph realiza un seguimiento del estado de las notificaciones de los usuarios de forma centralizada, y le asegura que todas las notificaciones se administran una vez y actualizan o descartar en todas partes.

### <a name="retrieve-notification-history"></a>Recuperación del historial de notificaciones
Puede usar la API de notificaciones para recuperar el historial de notificaciones según el tiempo de expiración que defina (hasta 30 días). Las notificaciones que están marcadas como leídas o descartadas se pueden recuperar del historial para poder tener vistas en la aplicación del historial de notificaciones y otros escenarios.

## <a name="integrating-with-microsoft-graph-notifications"></a>Integración con las notificaciones de Microsoft Graph

### <a name="onboarding"></a>Incorporación
Eche un vistazo a la guía de procedimientos de cada nodo de la plataforma (iOS, Android y Windows) para obtener instrucciones detalladas sobre cómo usar las notificaciones de Graph como solución de notificación push para dispositivos móviles para sus aplicaciones y servicios. Tenga en cuenta que las guías de procedimientos se centran en la recepción de notificaciones. Encontrará información sobre el envío de notificaciones en la página [Envío de notificaciones con las API de MS Graph](sending-notifications.md).

La guía incluye los pasos específicos para usar las notificaciones de Graph, incluido el registro de identidades de aplicación multiplataforma y las credenciales de notificación push para dispositivos móviles. Si no está familiarizado con el uso de Microsoft Graph, se incluyen los pasos para registrar la aplicación en una cuenta de Microsoft (MSA), en el caso de las aplicaciones orientadas al consumidor, o Azure Active Directory (AAD) en el caso de cuentas profesionales y educativas. MSA y AAD son identidades de usuario que le permiten aprovechar las ventajas de las cargas de trabajo en Microsoft Graph, no solo las notificaciones, para habilitar escenarios empresariales más completos. 

### <a name="microsoft-graph-apis"></a>Microsoft Graph API
Cuando se usan las notificaciones de Graph, se espera que el servidor de aplicaciones use Microsoft Graph API (beta) para enviar notificaciones. Para más información sobre la integración de aplicaciones en el lado servidor, consulte cómo se utiliza la API en la [documentación de referencia de API](/graph/api/resources/notifications-api-overview). 

### <a name="client-side-sdk"></a>SDK del lado cliente
Para empezar a trabajar con la integración de notificaciones del Graph en el lado cliente y empezar a recibir y administrar notificaciones mediante los SDK nativos, seleccione la plataforma de desarrollo que prefiera en el panel de navegación izquierdo. 

* [Envío de notificaciones con las API de MS Graph](sending-notifications.md)
* [Recepción de notificaciones mediante el SDK de Project Rome](receiving-notifications.md)