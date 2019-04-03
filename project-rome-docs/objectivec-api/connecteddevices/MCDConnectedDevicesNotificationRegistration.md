---
title: MCDConnectedDevicesNotificationRegistration
description: Esta clase representa el registro de la aplicación con un servicio de notificaciones de inserción (necesario para algunos escenarios de proyecto Roma).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 38cd140538d6e6dabddda39ba98f736fc708ade7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908887"
---
# <a name="class-mcdconnecteddevicesnotificationregistration"></a><span data-ttu-id="7fdbd-104">Clase `MCDConnectedDevicesNotificationRegistration`</span><span class="sxs-lookup"><span data-stu-id="7fdbd-104">class `MCDConnectedDevicesNotificationRegistration`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistration : NSObject
```  
 <span data-ttu-id="7fdbd-105">Esta clase representa el registro de la aplicación con un servicio de notificaciones de inserción (necesario para algunos escenarios de proyecto Roma).</span><span class="sxs-lookup"><span data-stu-id="7fdbd-105">This class represents the app's registration with a push notification service (necessary for some Project Rome scenarios).</span></span> <span data-ttu-id="7fdbd-106">Transmite esa información a la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-106">It conveys this information to the Connected Devices Platform.</span></span>

## <a name="properties"></a><span data-ttu-id="7fdbd-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="7fdbd-107">Properties</span></span>

### <a name="type"></a><span data-ttu-id="7fdbd-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="7fdbd-108">type</span></span>
`@property(nonatomic, readwrite) MCDConnectedDevicesNotificationType type;`

<span data-ttu-id="7fdbd-109">El tipo de notificaciones en esta configuración.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-109">The type of notifications in this setup.</span></span>

### <a name="token"></a><span data-ttu-id="7fdbd-110">símbolo (token)</span><span class="sxs-lookup"><span data-stu-id="7fdbd-110">token</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* token;`

<span data-ttu-id="7fdbd-111">El token de registro.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-111">The registration token.</span></span>

### <a name="appid"></a><span data-ttu-id="7fdbd-112">appId</span><span class="sxs-lookup"><span data-stu-id="7fdbd-112">appId</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appId;`

<span data-ttu-id="7fdbd-113">El identificador de aplicación para el registro de notificaciones push.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-113">The app ID for push notification registration.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="7fdbd-114">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="7fdbd-114">appDisplayName</span></span>
`@property(nonatomic, readwrite, nonnull) NSString* appDisplayName;`

<span data-ttu-id="7fdbd-115">Nombre para mostrar la aplicación.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-115">The app display name.</span></span> <span data-ttu-id="7fdbd-116">Esto debe ser el nombre de la aplicación que se usó para el registro en el portal de desarrollo de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7fdbd-116">This should be the name of the app that was used for registration on the Microsoft dev portal.</span></span>