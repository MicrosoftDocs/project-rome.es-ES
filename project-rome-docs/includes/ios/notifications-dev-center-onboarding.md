---
title: Archivo de inclusión
description: Archivo de inclusión
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909297"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="4885b-103">Registrar la aplicación para notificaciones de inserción</span><span class="sxs-lookup"><span data-stu-id="4885b-103">Register your app for push notifications</span></span>

<span data-ttu-id="4885b-104">Registrar la aplicación con Apple para [notificaciones Push de Apple](https://developer.apple.com/notifications/) admite.</span><span class="sxs-lookup"><span data-stu-id="4885b-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="4885b-105">Asegúrese de anotar el remitente clave de servidor y el identificador que recibe ya que será necesario más adelante.</span><span class="sxs-lookup"><span data-stu-id="4885b-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="4885b-106">Una vez registrado, debe asociar la funcionalidad de notificación de inserción con la plataforma de dispositivos conectados en la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4885b-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

```ObjectiveC
self.notificationRegistration = [[MCDConnectedDevicesNotificationRegistration alloc] init];
    if ([[UIApplication sharedApplication] isRegisteredForRemoteNotifications])
    {
        self.notificationRegistration.type = MCDNotificationTypeAPN;
    }
    else
    {
        self.notificationRegistration.type = MCDNotificationTypePolling;
    }
    self.notificationRegistration.appId = [[NSBundle mainBundle] bundleIdentifier];
    self.notificationRegistration.appDisplayName = (NSString*)[[NSBundle mainBundle] objectForInfoDictionaryKey:@"CFBundleDisplayName"];
    self.notificationRegistration.token = deviceToken;
    self.isRegisteredWithToken = YES;
```

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="4885b-107">Registrar la aplicación en Microsoft Windows Dev Center para experiencias multidispositivo</span><span class="sxs-lookup"><span data-stu-id="4885b-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="4885b-108">Este paso sólo es necesario si desea usar características de proyecto Roma para tener acceso a datos desde o realizar solicitudes de dispositivos que no sean Windows.</span><span class="sxs-lookup"><span data-stu-id="4885b-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="4885b-109">Si solo tiene como destino dispositivos Windows, no es necesario completar este paso.</span><span class="sxs-lookup"><span data-stu-id="4885b-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="4885b-110">Registrar la aplicación para la [experiencias multidispositivo característica del panel del desarrollador de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="4885b-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="4885b-111">Se trata de un procedimiento diferente MSA y AAD del registro de aplicación anterior.</span><span class="sxs-lookup"><span data-stu-id="4885b-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="4885b-112">El objetivo principal de este proceso consiste en asignar las identidades de aplicación específico de plataforma con una identidad de aplicación multiplataforma que es reconocido por la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="4885b-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="4885b-113">Este paso también permitirá el envío de notificaciones mediante los servicios de notificación de inserción nativa correspondiente a las plataformas móviles que usa la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4885b-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="4885b-114">Para iOS, habilita las notificaciones se envíen a los extremos de la aplicación iOS mediante Apple Push Notification Service: Apple Push Notification Service.</span><span class="sxs-lookup"><span data-stu-id="4885b-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="4885b-115">Ir al panel del centro de desarrollo, vaya a experiencias multidispositivo desde el panel de navegación del lado izquierdo y seleccione Configurar una nueva aplicación de dispositivo cruzado.</span><span class="sxs-lookup"><span data-stu-id="4885b-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="4885b-116">![Panel del centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="4885b-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="4885b-117">El proceso de incorporación de centro de desarrollo requieren los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="4885b-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="4885b-118">Seleccione las plataformas admitidas: seleccione las plataformas donde la aplicación tendrá una presencia y habilitarse para experiencias multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="4885b-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="4885b-119">En el caso de integración de las notificaciones de gráfico, puede seleccionar desde Windows, Android o iOS, dependiendo de qué plataformas está utilizando.</span><span class="sxs-lookup"><span data-stu-id="4885b-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![Plataformas compatibles con experiencias multidispositivo:](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="4885b-121">Proporcionar los identificadores de aplicación: proporcione los identificadores de aplicación para cada plataforma que utilice.</span><span class="sxs-lookup"><span data-stu-id="4885b-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="4885b-122">Para las aplicaciones de iOS, esto es el nombre de paquete asignada a la aplicación cuando creó el proyecto.</span><span class="sxs-lookup"><span data-stu-id="4885b-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="4885b-123">Tenga en cuenta que puede agregar distintos identificadores (hasta diez) por plataforma, que es en caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, lo que quiere que sea capaz de recibir las mismas notificaciones enviadas por el servidor de aplicaciones de destino en el mismo usuario.</span><span class="sxs-lookup"><span data-stu-id="4885b-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![Experiencias multidispositivo: identificadores de aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="4885b-125">Proporcionar o seleccione los identificadores de aplicación en registros de aplicaciones MSA o AAD obtenidos en los anteriores pasos de registro de aplicación AAD/MSA anteriores.</span><span class="sxs-lookup"><span data-stu-id="4885b-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![Experiencias multidispositivo – MSA y registros de aplicaciones AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="4885b-127">Proporcione sus credenciales para las plataformas de notificación nativa relevantes para la aplicación (es decir, WNS para Windows, FCM para Android o APNS para iOS) para permitir la entrega de notificaciones desde el servidor de aplicaciones al publicar las notificaciones de usuario de destino.</span><span class="sxs-lookup"><span data-stu-id="4885b-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![Experiencias multidispositivo: credenciales de inserción](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="4885b-129">Por último, compruebe el dominio de aplicación entre dispositivos para asegurarse de que la aplicación tiene la propiedad del dominio y puede utilizarlo como una identidad de dispositivo cruzado de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="4885b-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![Experiencias multidispositivo: comprobación de dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
