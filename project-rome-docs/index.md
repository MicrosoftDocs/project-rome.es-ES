---
title: Creación de aplicaciones multidispositivo
description: Obtenga información sobre las características multiplataforma y multidispositivo disponibles para las aplicaciones de Windows 10 con Project Rome.
ms.topic: overview
ms.custom: seodec2018, RS5
ms.openlocfilehash: 977d64749544d1991a40eff5d80a1cd6186aba97
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115549"
---
# <a name="project-rome"></a><span data-ttu-id="b6cc3-103">Project Rome</span><span class="sxs-lookup"><span data-stu-id="b6cc3-103">Project Rome</span></span>

<span data-ttu-id="b6cc3-104">[Project Rome](https://developer.microsoft.com/windows/project-rome) es una plataforma multidispositivo de Microsoft para aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-104">[Project Rome](https://developer.microsoft.com/windows/project-rome) is Microsoft's cross-device experiences platform for apps.</span></span> 

<span data-ttu-id="b6cc3-105">En este sitio, encontrará documentación de Project Rome para desarrolladores y vínculos a otros recursos útiles.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-105">On this site you will find developer documentation for Project Rome and links to other useful resources.</span></span>

<span data-ttu-id="b6cc3-106">Para ver noticias, blogs y vídeos sobre Project Rome, visite la [página de inicio de Project Rome](https://developer.microsoft.com/windows/project-rome).</span><span class="sxs-lookup"><span data-stu-id="b6cc3-106">For news, blog posts, and videos about Project Rome, visit the [Project Rome landing page](https://developer.microsoft.com/windows/project-rome).</span></span>

<span data-ttu-id="b6cc3-107">Para ver aplicaciones de ejemplo que usan Project Rome, consulte la siguiente tabla de SDK o visite el [repositorio de ejemplos de Project Rome](https://github.com/Microsoft/project-rome).</span><span class="sxs-lookup"><span data-stu-id="b6cc3-107">For sample applications using Project Rome, check out the SDK table below, or visit the [Project Rome samples repo](https://github.com/Microsoft/project-rome).</span></span>

## <a name="about-project-rome"></a><span data-ttu-id="b6cc3-108">Acerca de Project Rome</span><span class="sxs-lookup"><span data-stu-id="b6cc3-108">About Project Rome</span></span>

<span data-ttu-id="b6cc3-109">Project Rome permite a los desarrolladores escribir aplicaciones que pueden ejecutarse en varios dispositivos y viajar con el usuario cuando cambian de un dispositivo a otro.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-109">Project Rome allows developers to write apps that can run on multiple devices and travel with the user as they switch between devices.</span></span>

<span data-ttu-id="b6cc3-110">Project Rome incluye características que se exponen mediante Microsoft Graph y los SDK nativos específicos de la plataforma.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-110">Project Rome includes features exposed via Microsoft Graph and platform-specific native SDKs.</span></span> <span data-ttu-id="b6cc3-111">Estas características habilitan diversas funcionalidades multidispositivo y para dispositivos conectados, lo que permite a las aplicaciones estar centralizadas en torno a la identidad de usuario que inició sesión.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-111">These features enable multiple cross-device and connected-device capabilities, allowing your apps to be centralized around a logged-in user identity.</span></span> <span data-ttu-id="b6cc3-112">Las características asociadas con Project Rome son, entre otras, actividades del usuario, notificaciones, retransmisión de dispositivo y uso compartido en proximidad.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-112">Features associated with Project Rome include but are not limited to user activities, notifications, device relay, and nearby share.</span></span>

## <a name="choosing-between-native-apis-and-graph-apis"></a><span data-ttu-id="b6cc3-113">Elección entre API nativas y API de Graph</span><span class="sxs-lookup"><span data-stu-id="b6cc3-113">Choosing between native APIs and Graph APIs</span></span>

<span data-ttu-id="b6cc3-114">Algunos escenarios están disponibles *tanto* en los SDK nativos de la plataforma como en las API REST mediante Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-114">Some scenarios are available through *both* the native platform SDKs and REST APIs via Microsoft Graph.</span></span> <span data-ttu-id="b6cc3-115">En general, las API REST permiten una implementación rápida y sencilla de las características de Project Rome.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-115">In general, the REST APIs enable quick and simple implementation of the Project Rome features.</span></span> <span data-ttu-id="b6cc3-116">Sin embargo, usar las implementaciones específicas de la plataforma tiene algunas ventajas:</span><span class="sxs-lookup"><span data-stu-id="b6cc3-116">However, there are some advantages to using platform-specific implementations:</span></span>

* <span data-ttu-id="b6cc3-117">Para actualizar la aplicación cuando cambia la información en el servidor, los SDK de la plataforma proporcionan un modelo de objetos con el lenguaje, el almacenamiento local y el patrón de publicación-suscripción nativos.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-117">The platform SDKs provide an object model in the native language, local storage, and a publish-subscribe pattern to update the app when server-side information changes.</span></span>
* <span data-ttu-id="b6cc3-118">Si la aplicación se ejecuta en Windows (aplicaciones de UWP o Win32), el SDK de la plataforma proporciona una serie de características adicionales, como el uso de la cuenta predeterminada de los usuarios y el seguimiento automático de la interacción de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-118">If your app runs on Windows (UWP or Win32 apps), the platform SDK provides a number of additional features, such as using the users' default account and automatically tracking user engagement.</span></span>
* <span data-ttu-id="b6cc3-119">Si tiene previsto usar otras características de Project Rome que solo están disponibles mediante los SDK de la plataforma, quizás quiera implementar cada una de las características de la misma manera.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-119">If you plan to use other Project Rome features that are only available through the platform SDKs, you may wish to implement each of the features in the same way.</span></span>

<span data-ttu-id="b6cc3-120">La combinación de las API de Microsoft Graph API y los SDK de cliente habilitan algunos otros escenarios.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-120">Some other scenarios are enabled by using a combination of Microsoft Graph APIs and client SDKs.</span></span> <span data-ttu-id="b6cc3-121">Un ejemplo de esto son las notificaciones.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-121">An example of this is Notifications.</span></span> <span data-ttu-id="b6cc3-122">En este caso, se usa Microsoft Graph API para publicar notificaciones desde el lado del servidor de aplicaciones, y se usan los SDK de cliente nativos de la plataforma para recibir y administrar las notificaciones en cada aplicación nativa del lado cliente.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-122">In this case, MS Graph API is used to publish notifications from app server side, and the native-platform client SDKs are utilized to receive and manage notifications in each client-side native apps.</span></span>

## <a name="sdk"></a><span data-ttu-id="b6cc3-123">SDK</span><span class="sxs-lookup"><span data-stu-id="b6cc3-123">SDK</span></span>

<span data-ttu-id="b6cc3-124">Project Rome está implementado actualmente para las plataformas siguientes.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-124">Project Rome is currently implemented for the below platforms.</span></span> <span data-ttu-id="b6cc3-125">Siga los vínculos para descargas los SDK y ejemplos.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-125">Follow the links for samples and SDK downloads.</span></span>

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



|   <span data-ttu-id="b6cc3-126">Plataforma</span><span class="sxs-lookup"><span data-stu-id="b6cc3-126">Platform</span></span>                        | <span data-ttu-id="b6cc3-127">Características</span><span class="sxs-lookup"><span data-stu-id="b6cc3-127">Features</span></span>                                                         |           <span data-ttu-id="b6cc3-128">Paquete de SDK</span><span class="sxs-lookup"><span data-stu-id="b6cc3-128">SDK Package</span></span>                          |   <span data-ttu-id="b6cc3-129">Muestras</span><span class="sxs-lookup"><span data-stu-id="b6cc3-129">Samples</span></span>                                       |
| :-------------------------------- | :--------------------------------------------------------------- |:---------------------------------------------- | :---------------------------------------------- |
| <span data-ttu-id="b6cc3-130">**Windows SDK**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-130">**Windows SDK**</span></span>                   | <span data-ttu-id="b6cc3-131">Retransmisión de dispositivo, Actividades/Línea de tiempo</span><span class="sxs-lookup"><span data-stu-id="b6cc3-131">Device Relay, Activities/Timeline</span></span>                                | <span data-ttu-id="b6cc3-132">[![SDK][windows-sdk-badge]][windows-sdk]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-132">[![SDK][windows-sdk-badge]][windows-sdk]</span></span>       | <span data-ttu-id="b6cc3-133">[Ejemplo de retransmisión de dispositivo con Project Rome para Windows][windows-drsample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-133">[Project Rome for Device Relay Windows sample][windows-drsample]</span></span> <br> <span data-ttu-id="b6cc3-134">[Ejemplo de actividades con Project Rome para Windows][windows-afsample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-134">[Project Rome for Activities Windows sample][windows-afsample]</span></span>
| <span data-ttu-id="b6cc3-135">**Windows (versión preliminar)**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-135">**Windows (Preview)**</span></span>             |                                    <span data-ttu-id="b6cc3-136">Notificaciones de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="b6cc3-136">Microsoft Graph Notifications</span></span> | <span data-ttu-id="b6cc3-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-137">[![Nuget][winredist-sdk-badge]][winredist-sdk]</span></span> | <span data-ttu-id="b6cc3-138">[Ejemplos de notificaciones de Graph para Windows][winredist-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-138">[Graph Notifications for Windows sample][winredist-sample]</span></span> 
| <span data-ttu-id="b6cc3-139">**Android**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-139">**Android**</span></span>             | <span data-ttu-id="b6cc3-140">Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="b6cc3-140">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="b6cc3-141">[![Maven][android-sdk-badge]][android-sdk]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-141">[![Maven][android-sdk-badge]][android-sdk]</span></span>     | <span data-ttu-id="b6cc3-142">[Ejemplo de Project Rome para Android][android-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-142">[Project Rome for Android sample][android-sample]</span></span>
| <span data-ttu-id="b6cc3-143">**iOS**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-143">**iOS**</span></span>                 | <span data-ttu-id="b6cc3-144">Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="b6cc3-144">Device Relay, Activities/Timeline, Microsoft Graph Notifications (Preview)</span></span> | <span data-ttu-id="b6cc3-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-145">[![CocoaPod][ios-sdk-badge]][ios-sdk]</span></span>          | <span data-ttu-id="b6cc3-146">[Ejemplo de Project Rome para iOS][ios-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-146">[Project Rome for iOS sample][ios-sample]</span></span>
| <span data-ttu-id="b6cc3-147">**Xamarin para Android (versión preliminar)**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-147">**Xamarin for Android (Preview)**</span></span> | <span data-ttu-id="b6cc3-148">Retransmisión de dispositivo</span><span class="sxs-lookup"><span data-stu-id="b6cc3-148">Device Relay</span></span>                                                     | <span data-ttu-id="b6cc3-149">[![NuGet][xamarin-sdk-badge]][xamarin-sdk]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-149">[![Nuget][xamarin-sdk-badge]][xamarin-sdk]</span></span>     | <span data-ttu-id="b6cc3-150">[Ejemplo de Xamarin para Android][xamarin-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-150">[Xamarin for Android sample][xamarin-sample]</span></span>
| <span data-ttu-id="b6cc3-151">**MSGraph**</span><span class="sxs-lookup"><span data-stu-id="b6cc3-151">**MSGraph**</span></span>                       | <span data-ttu-id="b6cc3-152">Retransmisión de dispositivo, Actividades/Línea de tiempo, Notificaciones de Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="b6cc3-152">Device Relay, Activities/Timeline, Microsoft Graph Notifications</span></span> | <span data-ttu-id="b6cc3-153">[![REST][graph-relay-badge]][graph-relay]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-153">[![REST][graph-relay-badge]][graph-relay]</span></span><br> <span data-ttu-id="b6cc3-154">[![REST][graph-activities-badge]][graph-activities]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-154">[![REST][graph-activities-badge]][graph-activities]</span></span><br><span data-ttu-id="b6cc3-155">[![REST][graph-notification-badge]][graph-notification]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-155">[![REST][graph-notification-badge]][graph-notification]</span></span>          | <span data-ttu-id="b6cc3-156">[Retransmisión de dispositivo][graph-relay-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-156">[Device Relay][graph-relay-sample]</span></span><br><span data-ttu-id="b6cc3-157">[Actividades/Línea de tiempo][graph-activities-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-157">[Activities/Timeline][graph-activities-sample]</span></span><br><span data-ttu-id="b6cc3-158">[Notificaciones de Graph][graph-notification-sample]</span><span class="sxs-lookup"><span data-stu-id="b6cc3-158">[Graph Notifications][graph-notification-sample]</span></span>

## <a name="project-rome-blog-posts"></a><span data-ttu-id="b6cc3-159">Entradas de blog sobre Project Rome</span><span class="sxs-lookup"><span data-stu-id="b6cc3-159">Project Rome blog posts</span></span>
* [<span data-ttu-id="b6cc3-160">Experiencias entre dispositivos con Project Rome</span><span class="sxs-lookup"><span data-stu-id="b6cc3-160">Cross-device experiences with Project Rome</span></span>](https://blogs.windows.com/buildingapps/2016/10/11/cross-device-experience-with-project-rome/#iQTseFlAMJRopU9k.97)

* [<span data-ttu-id="b6cc3-161">Hacia un mundo social: integración de Project Rome, mapas y redes sociales</span><span class="sxs-lookup"><span data-stu-id="b6cc3-161">Going social: Project Rome, Maps, & Social Network Integration</span></span>](https://blogs.windows.com/buildingapps/2016/10/27/going-social-project-rome-maps-social-network-integration-app-dev-on-xbox-series/#SCfoEZ1q8c1yBMei.97)

* [<span data-ttu-id="b6cc3-162">Anuncio del SDK de Project Rome para Android</span><span class="sxs-lookup"><span data-stu-id="b6cc3-162">Announcing Project Rome Android SDK</span></span>](https://blogs.windows.com/buildingapps/2017/02/08/announcing-project-rome-android-sdk/#obDkvwkXOGa3tcTx.97)

* [<span data-ttu-id="b6cc3-163">Actualización de Project Rome para Android: ahora con compatibilidad para servicios de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="b6cc3-163">Project Rome for Android Update: Now with App Services Support</span></span>](https://blogs.windows.com/buildingapps/2017/03/23/project-rome-android-update-now-app-services-support/#DBm1Ic4JX8vXv2h0.97)

* [<span data-ttu-id="b6cc3-164">Creación de una aplicación complementaria de control remoto para Android con Project Rome</span><span class="sxs-lookup"><span data-stu-id="b6cc3-164">Building a Remote Control Companion App for Android with Project Rome</span></span>](https://devblogs.microsoft.com/xamarin/building-remote-control-companion-app-android-project-rome/)

* [<span data-ttu-id="b6cc3-165">Nueva experiencia de uso compartido en Windows 10 Creators Update</span><span class="sxs-lookup"><span data-stu-id="b6cc3-165">New Share Experience in Windows 10 Creators Update</span></span>](https://blogs.windows.com/buildingapps/2017/04/06/new-share-experience-windows-10-creators-update/#OGskrWcLLlrCTCSH.97)

* [<span data-ttu-id="b6cc3-166">Vinculación entre web y aplicación con AppUriHandlers</span><span class="sxs-lookup"><span data-stu-id="b6cc3-166">Web-to-App Linking with AppUriHandlers</span></span>](https://blogs.windows.com/buildingapps/2016/10/14/web-to-app-linking-with-appurihandlers/#fIh7USaxBYS8JqfT.97)

## <a name="other-resources"></a><span data-ttu-id="b6cc3-167">Otros recursos</span><span class="sxs-lookup"><span data-stu-id="b6cc3-167">Other resources</span></span>

* [<span data-ttu-id="b6cc3-168">Vinculación de Web a aplicaciones</span><span class="sxs-lookup"><span data-stu-id="b6cc3-168">Web-to-app linking</span></span>](https://docs.microsoft.com/windows/uwp/launch-resume/web-to-app-linking)

* [<span data-ttu-id="b6cc3-169">Conferencia en Build 2016</span><span class="sxs-lookup"><span data-stu-id="b6cc3-169">//Build 2016 talk</span></span>](https://channel9.msdn.com/Events/Build/2016/B831)

* [<span data-ttu-id="b6cc3-170">Podcast de MS Dev Show</span><span class="sxs-lookup"><span data-stu-id="b6cc3-170">MS Dev Show podcast</span></span>](http://msdevshow.com/2016/11/project-rome-with-shawn-henry/)

## <a name="give-feedback"></a><span data-ttu-id="b6cc3-171">Enviar comentarios</span><span class="sxs-lookup"><span data-stu-id="b6cc3-171">Give feedback</span></span>

|[<span data-ttu-id="b6cc3-172">UserVoice</span><span class="sxs-lookup"><span data-stu-id="b6cc3-172">UserVoice</span></span>](https://wpdev.uservoice.com/forums/110705-universal-windows-platform/category/183208-connected-apps-and-devices-project-rome)|[<span data-ttu-id="b6cc3-173">Centro de opiniones</span><span class="sxs-lookup"><span data-stu-id="b6cc3-173">Feedback Hub</span></span>](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)|[<span data-ttu-id="b6cc3-174">Ponte en contacto con nosotros</span><span class="sxs-lookup"><span data-stu-id="b6cc3-174">Contact Us</span></span>](mailto:projectrometeam@microsoft.com)|
|-----|-----|-----|
