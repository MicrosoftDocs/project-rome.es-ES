---
title: Creación de aplicaciones multidispositivo
description: Obtenga información sobre las características multiplataforma y multidispositivo disponibles para las aplicaciones de Windows 10 con Project Rome.
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: 13dcef5e158cf0cfd122afaef5f376ed06267790
ms.sourcegitcommit: 5bf261d8d6ebe89d6d075d851f9255c806f5a649
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2020
ms.locfileid: "91716699"
---
# <a name="project-rome"></a>Project Rome

[Project Rome](https://developer.microsoft.com/windows/project-rome) es una plataforma multidispositivo de Microsoft para aplicaciones. 

En este sitio, encontrará documentación de Project Rome para desarrolladores y vínculos a otros recursos útiles.

Para ver noticias, blogs y vídeos sobre Project Rome, visite la [página de inicio de Project Rome](https://developer.microsoft.com/windows/project-rome).

Para ver aplicaciones de ejemplo que usan Project Rome, consulte la siguiente tabla de SDK o visite el [repositorio de ejemplos de Project Rome](https://github.com/Microsoft/project-rome).

## <a name="about-project-rome"></a>Acerca de Project Rome

Project Rome permite a los desarrolladores escribir aplicaciones que pueden ejecutarse en varios dispositivos y viajar con el usuario cuando cambian de un dispositivo a otro.

Project Rome incluye características que se exponen mediante Microsoft Graph y los SDK nativos específicos de la plataforma. Estas características habilitan diversas funcionalidades multidispositivo y para dispositivos conectados, lo que permite a las aplicaciones estar centralizadas en torno a la identidad de usuario que inició sesión. Las características asociadas con Project Rome son, entre otras, actividades del usuario, notificaciones, retransmisión de dispositivo y uso compartido en proximidad.

## <a name="choosing-between-native-apis-and-graph-apis"></a>Elección entre API nativas y API de Graph

Algunos escenarios están disponibles *tanto* en los SDK nativos de la plataforma como en las API REST mediante Microsoft Graph. En general, las API REST permiten una implementación rápida y sencilla de las características de Project Rome. Sin embargo, usar las implementaciones específicas de la plataforma tiene algunas ventajas:

* Para actualizar la aplicación cuando cambia la información en el servidor, los SDK de la plataforma proporcionan un modelo de objetos con el lenguaje, el almacenamiento local y el patrón de publicación-suscripción nativos.
* Si la aplicación se ejecuta en Windows (aplicaciones de UWP o Win32), el SDK de la plataforma proporciona una serie de características adicionales, como el uso de la cuenta predeterminada de los usuarios y el seguimiento automático de la interacción de los usuarios.
* Si tiene previsto usar otras características de Project Rome que solo están disponibles mediante los SDK de la plataforma, quizás quiera implementar cada una de las características de la misma manera.

La combinación de las API de Microsoft Graph API y los SDK de cliente habilitan algunos otros escenarios. Un ejemplo de esto son las notificaciones. En este caso, se usa Microsoft Graph API para publicar notificaciones desde el lado del servidor de aplicaciones, y se usan los SDK de cliente nativos de la plataforma para recibir y administrar las notificaciones en cada aplicación nativa del lado cliente.

## <a name="sdk"></a>SDK

Project Rome está implementado actualmente para las plataformas siguientes. Siga los vínculos para descargas los SDK y ejemplos.

[windows-sdk]:             https://developer.microsoft.com/windows/downloads
[windows-sdk-badge]:       https://img.shields.io/badge/sdk-April%202018%20Update-brightgreen.svg
[windows-drsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/RemoteSystems
[windows-afsample]:        https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/UserActivity 

[winredist-sdk]:           https://www.nuget.org/packages/Microsoft.ConnectedDevices.UserNotifications
[winredist-sdk-badge]:     https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.UserNotifications.svg
[winredist-sample]:        https://github.com/microsoft/project-rome/tree/master/Windows/samples

[xamarin-sdk]:             https://www.nuget.org/packages/Microsoft.ConnectedDevices.Xamarin.Droid
[xamarin-sdk-badge]:       https://img.shields.io/nuget/v/Microsoft.ConnectedDevices.Xamarin.Droid.svg
[xamarin-sample]:          https://github.com/Microsoft/project-rome/tree/0.8.1/Xamarin/samples

[ios-sdk]:                 https://cocoapods.org/pods/ProjectRomeSdk
[ios-sdk-badge]:           https://img.shields.io/cocoapods/v/ProjectRomeSdk.svg
[ios-sample]:              https://github.com/microsoft/project-rome/tree/master/iOS/samples

[android-sdk]:             https://bintray.com/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/_latestVersion
[android-sdk-badge]:       https://api.bintray.com/packages/connecteddevices/maven/com.microsoft.connecteddevices%3Aconnecteddevices-sdk/images/download.svg
[android-sample]:          https://github.com/microsoft/project-rome/tree/master/Android/samples

[graph-relay]:             https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities]:        https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification]:      https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview

[graph-relay-badge]:       https://img.shields.io/badge/Device_Relay-Beta-orange.svg
[graph-activities-badge]:  https://img.shields.io/badge/Activities-1.0-brightgreen.svg
[graph-notification-badge]:https://img.shields.io/badge/Graph_Notifications-Beta-orange.svg

[graph-relay-sample]:        https://developer.microsoft.com/graph/docs/api-reference/beta/resources/project_rome_overview
[graph-activities-sample]:   https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/activity-feed-api-overview
[graph-notification-sample]: https://developer.microsoft.com/graph/docs/api-reference/beta/resources/notifications-api-overview



|   Plataforma                        | Características                                                         |           Paquete de SDK                          |   Ejemplos                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| **Windows SDK**                   | Retransmisión de dispositivo, Actividades/Línea de tiempo                                | [![SDK][windows-sdk-badge]][windows-sdk]       | [Ejemplo de retransmisión de dispositivo con Project Rome para Windows][windows-drsample] <br> [Ejemplo de actividades con Project Rome para Windows][windows-afsample]
| **Windows (versión preliminar)**             |                                    Notificaciones de Microsoft Graph | [![Nuget][winredist-sdk-badge]][winredist-sdk] | [Ejemplos de notificaciones de Graph para Windows][winredist-sample] 
| **Android**             | Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph (versión preliminar) | [![Maven][android-sdk-badge]][android-sdk]     | [Ejemplo de Project Rome para Android][android-sample]
| **iOS**                 | Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph (versión preliminar) | [![CocoaPod][ios-sdk-badge]][ios-sdk]          | [Ejemplo de Project Rome para iOS][ios-sample]
| **Xamarin para Android (versión preliminar)** | Retransmisión de dispositivo                                                     | [![NuGet][xamarin-sdk-badge]][xamarin-sdk]     | [Ejemplo de Xamarin para Android][xamarin-sample]
| **MSGraph**                       | Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph | [![REST][graph-relay-badge]][graph-relay]<br> [![REST][graph-activities-badge]][graph-activities]<br>[![REST][graph-notification-badge]][graph-notification]          | [Retransmisión de dispositivo][graph-relay-sample]<br>[Actividades/Línea de tiempo][graph-activities-sample]<br>[Notificaciones de Graph][graph-notification-sample]

## <a name="project-rome-blog-posts"></a>Entradas de blog sobre Project Rome
* [Presentación del SDK de Project Rome para la versión 1.0 de Android e iOS](https://blogs.windows.com/windowsdeveloper/2019/01/29/announcing-project-rome-sdk-for-android-and-ios-version-1-0/)

* [Experiencias entre dispositivos con Project Rome](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [Hacia un mundo social: integración de Project Rome, mapas y redes sociales](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [Anuncio del SDK de Project Rome para Android](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [Actualización de Project Rome para Android: ahora con compatibilidad para servicios de aplicaciones](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [Creación de una aplicación complementaria de control remoto para Android con Project Rome](https://devblogs.microsoft.com/xamarin/building-remote-control-companion-app-android-project-rome/)

* [Nueva experiencia de uso compartido en Windows 10 Creators Update](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [Vinculación entre web y aplicación con AppUriHandlers](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

* [Project Rome: cómo impulsar la interacción del usuario en dispositivos, aplicaciones y plataformas

* [Creación de aplicaciones conectadas con UWP y Proyecto Roma](https://docs.microsoft.com/archive/msdn-magazine/2018/may/universal-windows-platform-building-connected-apps-with-uwp-and-project-rome)

* [Proyecto Roma: Cómo impulsar la interacción del usuario en dispositivos, aplicaciones y plataformas](https://blogs.windows.com/windowsdeveloper/2017/05/16/project-rome-driving-user-engagement-across-devices-apps-platforms/#hZYfcfYVCFfBv0pS.97)

* [Habilitación de experiencias de notificación centradas en el usuario mediante notificaciones de Microsoft Graph](https://docs.microsoft.com/graph/notifications-concept-overview)

## <a name="podcasts-and-recordings"></a>Podcasts y grabaciones

* [Proyecto Roma en Microsoft/Compilación 2018](https://channel9.msdn.com/Events/Build/2018/BRK2417)

* [Compilación 2017: Channel 9 en directo: preguntas y respuestas sobre el Proyecto Roma](https://channel9.msdn.com/Events/Build/2017/C9R11)

* [Compilación 2017: MS Dev Show: Proyecto Roma](https://channel9.msdn.com/Shows/msdevshow/Episode-153-Project-Rome-with-Vikas-Bhatia-and-Shawn-Henry)

* [Podcast de MS Dev Show: Proyecto Roma con Shawn Henry (8 de noviembre de 2016)](https://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

* [Vinculación de Web a aplicaciones](https://docs.microsoft.com/windows/uwp/launch-resume/web-to-app-linking)

* [Compilación 2016: Cómo impulsar la interacción del usuario con aplicaciones y dispositivos conectados](https://channel9.msdn.com/Events/Build/2016/B831)

* [One Dev Minute: Creación de aplicaciones para todos los dispositivos con Project Rome](https://www.youtube.com/watch?v=7jn-kooKE8U)

* [Introducción a Microsoft Graph y las notificaciones](https://www.youtube.com/watch?v=cmpPFhrS8ZA)

## <a name="give-feedback"></a>Proporcionar comentarios

|[Centro de opiniones](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[Póngase en contacto con nosotros](mailto:projectrometeam@microsoft.com)|
|-----|-----|

