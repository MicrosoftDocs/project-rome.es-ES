---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: dc4d7bbd-bc87-42b1-9924-52c7bfcd5b5f
ms.localizationpriority: medium
ms.openlocfilehash: f085486eece082366dddc00d86f0c4959d09a5cf
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907307"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="72b4a-103">Registrar la aplicación para notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="72b4a-103">Register your app for push notifications</span></span>

<span data-ttu-id="72b4a-104">Registrar la aplicación con Google para [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) admite.</span><span class="sxs-lookup"><span data-stu-id="72b4a-104">Register your application with Google for [Firebase Cloud Messaging](https://firebase.google.com/docs/cloud-messaging/android/client) support.</span></span> <span data-ttu-id="72b4a-105">No olvide tomar nota del remitente clave de servidor y el identificador que recibe; los necesitará más adelante.</span><span class="sxs-lookup"><span data-stu-id="72b4a-105">Be sure to make note of the sender ID and server key that you receive; you'll need them later.</span></span>

<span data-ttu-id="72b4a-106">Una vez registrado, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="72b4a-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

```Java
mNotificationRegistration = new ConnectedDevicesNotificationRegistration();
mNotificationRegistration.setType(ConnectedDevicesNotificationType.FCM);
mNotificationRegistration.setToken(token);
mNotificationRegistration.setAppId(Secrets.FCM_SENDER_ID);
mNotificationRegistration.setAppDisplayName("SampleApp");
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="72b4a-107">Registrar la aplicación en Microsoft Windows Dev Center para experiencias multidispositivo</span><span class="sxs-lookup"><span data-stu-id="72b4a-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!IMPORTANT]
> <span data-ttu-id="72b4a-108">Este paso sólo es necesario si desea usar características de proyecto Roma para tener acceso a datos desde o realizar solicitudes de dispositivos que no sean Windows.</span><span class="sxs-lookup"><span data-stu-id="72b4a-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="72b4a-109">Si solo tiene como destino dispositivos Windows, no es necesario completar este paso.</span><span class="sxs-lookup"><span data-stu-id="72b4a-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="72b4a-110">Ir al panel del centro de desarrollo, vaya a experiencias multidispositivo desde el panel de navegación del lado izquierdo y seleccione Configurar una nueva aplicación entre dispositivos, que se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="72b4a-110">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app, shown as below.</span></span>
<span data-ttu-id="72b4a-111">![Panel del centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-111">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="72b4a-112">El proceso de incorporación de centro de desarrollo requiere los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="72b4a-112">The Dev Center on-boarding process requires the following steps:</span></span>
* <span data-ttu-id="72b4a-113">Seleccione las plataformas admitidas: seleccione las plataformas donde la aplicación tendrá una presencia y habilitarse para experiencias multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="72b4a-113">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="72b4a-114">En el caso de integración de las notificaciones de gráfico, puede seleccionar desde Windows, Android o iOS.</span><span class="sxs-lookup"><span data-stu-id="72b4a-114">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS.</span></span>
<span data-ttu-id="72b4a-115">![Plataformas compatibles con experiencias multidispositivo:](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-115">![Cross-Device Experiences – Supported Platforms](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)</span></span>

* <span data-ttu-id="72b4a-116">Proporcione los identificadores de aplicación: proporcione los identificadores de aplicación para cada uno de la plataforma donde la aplicación tiene una presencia.</span><span class="sxs-lookup"><span data-stu-id="72b4a-116">Provide app IDs – provide app IDs for each of the platform where your app has a presence.</span></span> <span data-ttu-id="72b4a-117">Las aplicaciones Android, esto es el nombre de paquete asignada a la aplicación cuando creó el proyecto.</span><span class="sxs-lookup"><span data-stu-id="72b4a-117">For Android apps, this is the Package Name you assigned to your app when you created the project.</span></span> <span data-ttu-id="72b4a-118">El nombre del paquete puede encontrarse en la consola de Firebase en información general del proyecto -> General.</span><span class="sxs-lookup"><span data-stu-id="72b4a-118">The Package Name can be found in your Firebase console under Project Overview -> General.</span></span> <span data-ttu-id="72b4a-119">Puede agregar distintos identificadores (hasta diez) por plataforma, que es en caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, lo que quiere que sea capaz de recibir las mismas notificaciones enviadas por el servidor de aplicaciones de destino en el mismo usuario.</span><span class="sxs-lookup"><span data-stu-id="72b4a-119">You may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> 
<span data-ttu-id="72b4a-120">![Experiencias multidispositivo: identificadores de aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-120">![Cross-Device Experiences – App IDs](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)</span></span>

* <span data-ttu-id="72b4a-121">Proporcione o seleccione la aplicación de los identificadores de MSA o AAD registros de aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="72b4a-121">Provide or select the app IDs from MSA and/or AAD app registrations.</span></span> <span data-ttu-id="72b4a-122">Estos identificadores de cliente correspondientes al registro de aplicación AAD o de MSA se obtuvieron en los pasos de registro de aplicación AAD/MSA anteriores desde arriba.</span><span class="sxs-lookup"><span data-stu-id="72b4a-122">These client IDs corresponding to MSA or AAD app registration were obtained in the previous MSA/AAD app registration steps from above.</span></span> 
<span data-ttu-id="72b4a-123">![Experiencias multidispositivo – MSA y registros de aplicaciones AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-123">![Cross-Device Experiences – MSA and AAD App Registrations](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)</span></span>

* <span data-ttu-id="72b4a-124">Las notificaciones de Graph y otras capacidades de plataforma de dispositivos conectados aprovechan cada una de las plataformas de notificación nativa en las plataformas principales para enviar notificaciones a la aplicación de extremos de cliente, es decir, WNS (para Windows UWP), FCM (para Android) y Apple Push Notification Service (para iOS) .</span><span class="sxs-lookup"><span data-stu-id="72b4a-124">Graph Notifications and other Connected Devices Platform capabilities leverage each of the native notification platforms on major platforms to send notifications down to the app client endpoints, namely, WNS (for Windows UWP), FCM (for Android) and APNS (for iOS).</span></span> <span data-ttu-id="72b4a-125">Proporcione sus credenciales para estas plataformas de notificación habilitar las notificaciones de Graph entregar las notificaciones para el servidor de aplicaciones, al publicar las notificaciones de usuario de destino.</span><span class="sxs-lookup"><span data-stu-id="72b4a-125">Provide your credentials for these notification platforms to enable Graph Notifications to deliver the notifications for your app server, when you publish user-targeted notifications.</span></span> <span data-ttu-id="72b4a-126">Para Android, [habilitar el servicio de mensajería de nube](https://firebase.google.com/docs/cloud-messaging/android/client) es un requisito previo para usar notificaciones de Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="72b4a-126">For Android, [enabling the Cloud Messaging service](https://firebase.google.com/docs/cloud-messaging/android/client) is a prerequisite to using Microsoft Graph Notifications.</span></span> <span data-ttu-id="72b4a-127">Además, tenga en cuenta que el identificador de remitente requerido se corresponde con el identificador del remitente Firebase Cloud Messaging y la clave de API que se corresponde con la clave del servidor heredado.</span><span class="sxs-lookup"><span data-stu-id="72b4a-127">Also, note that the required Sender ID corresponds to the Firebase Cloud Messaging Sender ID, and the API key corresponds to the Legacy Server Key.</span></span> <span data-ttu-id="72b4a-128">Ambos pueden encontrarse en la consola de Firebase -> proyecto -> configuración, en la pestaña de mensajería en la nube, como se muestra en la captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="72b4a-128">Both can be found in Firebase Console -> Project -> Settings, under the Cloud Messaging tab, as shown in the screenshot.</span></span>
<span data-ttu-id="72b4a-129">![Experiencias multidispositivo: credenciales de inserción](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-129">![Cross-Device Experiences – Push Credentials](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)</span></span>

* <span data-ttu-id="72b4a-130">El último paso es comprobar el dominio de aplicación entre dispositivos, que actúa como un proceso de comprobación para demostrar que la aplicación tiene que actúa como una identidad de aplicación entre dispositivos de la aplicación que registró la propiedad de este dominio.</span><span class="sxs-lookup"><span data-stu-id="72b4a-130">The last step is to verify your cross-device app domain, which serves as a verification process to prove that your app has the ownership of this domain which acts like a cross-device app identity for the app you registered.</span></span>
<span data-ttu-id="72b4a-131">![Experiencias multidispositivo: comprobación de dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span><span class="sxs-lookup"><span data-stu-id="72b4a-131">![Cross-Device Experiences – Domain Verification](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)</span></span>