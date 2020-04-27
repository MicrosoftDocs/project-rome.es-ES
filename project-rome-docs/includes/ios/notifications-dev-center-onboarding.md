---
title: include file
description: include file
ms.topic: include
ms.assetid: 0741073e-62de-4e31-8e3b-cd1a55027c1c
ms.localizationpriority: medium
ms.openlocfilehash: f302fa886cf342e5116b88f9b7474c0b3660ab18
ms.sourcegitcommit: 7e022438d0414d8f24ee2c048bb018c80b1ea921
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2020
ms.locfileid: "58909297"
---
### <a name="register-your-app-for-push-notifications"></a><span data-ttu-id="d5ab8-103">Registro de la aplicación para notificaciones push</span><span class="sxs-lookup"><span data-stu-id="d5ab8-103">Register your app for push notifications</span></span>

<span data-ttu-id="d5ab8-104">Registra la aplicación con Apple para conseguir la compatibilidad con [Apple Push Notification](https://developer.apple.com/notifications/).</span><span class="sxs-lookup"><span data-stu-id="d5ab8-104">Register your application with Apple for [Apple Push Notification](https://developer.apple.com/notifications/) support.</span></span> <span data-ttu-id="d5ab8-105">No olvides anotar el id. del remitente y la clave de servidor que recibas, ya que los necesitarás más adelante.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-105">Be sure to make note of the sender ID and server key that you receive as you'll need them later.</span></span>

<span data-ttu-id="d5ab8-106">Una vez efectuado el registro, debes asociar la funcionalidad de notificaciones push con la plataforma de dispositivos conectados de tu aplicación.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-106">Once registered, you must associate push notification functionality with the Connected Devices Platform in your app.</span></span>

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

### <a name="register-your-app-in-microsoft-windows-dev-center-for-cross-device-experiences"></a><span data-ttu-id="d5ab8-107">Registro de la aplicación en el Centro de desarrollo de Microsoft Windows para experiencias multidispositivo</span><span class="sxs-lookup"><span data-stu-id="d5ab8-107">Register your app in Microsoft Windows Dev Center for cross-device experiences</span></span>

> [!WARNING]
> <span data-ttu-id="d5ab8-108">Este paso solo es necesario si deseas usar características de Project Rome para acceder a datos de dispositivos que no sean Windows o realizar solicitudes en ellos.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-108">This step is only required if you want to use Project Rome features to access data from or make requests of non-Windows devices.</span></span> <span data-ttu-id="d5ab8-109">Si solo vas a trabajar con dispositivos Windows, no es necesario que realices este paso.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-109">If you only target Windows devices, you do not need to complete this step.</span></span>

<span data-ttu-id="d5ab8-110">Registra la aplicación para acceder a la [característica de experiencias multidispositivo del Panel de desarrolladores de Microsoft](https://developer.microsoft.com/dashboard/crossplatform/web).</span><span class="sxs-lookup"><span data-stu-id="d5ab8-110">Register your app for the [cross-device experiences feature of the Microsoft Developer Dashboard](https://developer.microsoft.com/dashboard/crossplatform/web).</span></span> <span data-ttu-id="d5ab8-111">Se sigue un procedimiento diferente al registro de la aplicación con MSA y AAD anterior.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-111">This is a different procedure from MSA and AAD app registration above.</span></span> <span data-ttu-id="d5ab8-112">El objetivo principal de este proceso consiste en asignar las identidades de la aplicación específicas de la plataforma a una identidad de aplicación multiplataforma que se reconozca en la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-112">The main goal for this process is to map the platform specific app identities with a cross-platform app identity that is recognized by Connected Devices Platform.</span></span> <span data-ttu-id="d5ab8-113">Este paso también permitirá enviar notificaciones mediante los servicios de notificación push nativos correspondientes a las plataformas móviles que utilice la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-113">This step will also enable sending notifications using the native push notification services corresponding to the mobile platform(s) your app utilizes.</span></span> <span data-ttu-id="d5ab8-114">En iOS, permite que las notificaciones se envíen a los puntos de conexión de la aplicación iOS mediante APNS (Apple Push Notification Service).</span><span class="sxs-lookup"><span data-stu-id="d5ab8-114">For iOS, it enables notifications to be sent to iOS app endpoints via APNS – Apple Push Notification Service.</span></span>

<span data-ttu-id="d5ab8-115">Ve al Panel del Centro de desarrollo y allí, a Cross-Device Experiences (Experiencias multidispositivo) en el panel de navegación del lado izquierdo; selecciona la opción de configuración de una nueva aplicación multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-115">Go to Dev Center Dashboard, navigate to Cross-Device Experiences from the left side navigation pane, and select configuring a new cross-device app.</span></span>
<span data-ttu-id="d5ab8-116">![Panel del Centro de desarrollo: experiencias multidispositivo](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span><span class="sxs-lookup"><span data-stu-id="d5ab8-116">![Dev Center Dashboard – Cross-Device Experiences](../../notifications/media/dev_center_portal/dev_center_portal_1_overview.png)</span></span>

<span data-ttu-id="d5ab8-117">El proceso de incorporación del Centro de desarrollo requiere los siguientes pasos:</span><span class="sxs-lookup"><span data-stu-id="d5ab8-117">The Dev Center on-boarding process require the following steps:</span></span>

* <span data-ttu-id="d5ab8-118">Select supported platforms (Seleccionar plataformas compatibles): selecciona las plataformas donde la aplicación estará presente y habilitada para experiencias multidispositivo.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-118">Select supported platforms – select the platforms where your app will have a presence and be enabled for cross-device experiences.</span></span> <span data-ttu-id="d5ab8-119">En el caso de la integración con las notificaciones de Graph, puedes seleccionar Windows, Android o iOS, en función de las plataformas que utilices.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-119">In the case of Graph Notifications integration, you can select from Windows, Android, and/or iOS, depending on what platforms you are using.</span></span> ![Experiencias multidispositivo: plataformas compatibles](../../notifications/media/dev_center_portal/dev_center_portal_2_supported_platforms.png)

* <span data-ttu-id="d5ab8-121">Proporciona los id. de la aplicación: proporciona los id. de la aplicación para cada plataforma que utilices.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-121">Provide app IDs – provide app IDs for each platform you are using.</span></span> <span data-ttu-id="d5ab8-122">En las aplicaciones iOS, es el nombre del paquete que asignaste a la aplicación al crear el proyecto.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-122">For iOS apps, this is the package name you assigned to your app when you created the project.</span></span> <span data-ttu-id="d5ab8-123">Ten en cuenta que puedes agregar varios id. (hasta diez) por plataforma; esto se aplica en el caso de tener varias versiones de la misma aplicación, o incluso diferentes aplicaciones, que quieres que reciban las mismas notificaciones enviadas por el servidor de aplicaciones destinadas al mismo usuario.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-123">Note that you may add different IDs (up to ten) per platform – this is in case you have multiple version of the same app, or even different apps, that want to be able to receive the same notifications sent by your app server targeted at the same user.</span></span> ![Experiencias multidispositivo: id. de la aplicación](../../notifications/media/dev_center_portal/dev_center_portal_3_app_ids.png)

* <span data-ttu-id="d5ab8-125">Proporciona o selecciona los id. de la aplicación de los registros de la aplicación con MSA o AAD obtenidos en los pasos de registro de la aplicación con AAD/MSA anteriores.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-125">Provide or select the app IDs from MSA and/or AAD app registrations obtained in the previous MSA/AAD app registration steps above.</span></span> ![Experiencias multidispositivo: registros de la aplicación con MSA y AAD](../../notifications/media/dev_center_portal/dev_center_portal_4_msa_aad_connections.png)

* <span data-ttu-id="d5ab8-127">Indica tus credenciales para las plataformas de notificación nativas relevantes para la aplicación (es decir, WNS para Windows, FCM para Android o APNS para iOS), para permitir la entrega de notificaciones desde el servidor de aplicaciones al publicar notificaciones destinadas al usuario.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-127">Provide your credentials for the native notification platforms relevant to your app (i.e. WNS for Windows, FCM for Android, and/or APNS for iOS) to enable delivery of notifications from your app server when you publish user-targeted notifications.</span></span> ![Experiencias multidispositivo: credenciales de notificaciones push](../../notifications/media/dev_center_portal/dev_center_portal_5_push_credentials.png)

* <span data-ttu-id="d5ab8-129">Por último, comprueba el dominio de la aplicación multidispositivo para asegurarte de que la aplicación tiene la propiedad del dominio y puede utilizarlo como una identidad multidispositivo para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="d5ab8-129">Finally, verify your cross-device app domain to make sure your app has the ownership of the domain and can use it as a cross-device identity for your app.</span></span> ![Experiencias multidispositivo: verificación del dominio](../../notifications/media/dev_center_portal/dev_center_portal_6_domain_verification.png)
