---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908447"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a><span data-ttu-id="c4749-104">Clase `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="c4749-104">class `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
<span data-ttu-id="c4749-105">Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration.</span><span class="sxs-lookup"><span data-stu-id="c4749-105">Event Args class for the MCDConnectedDevicesNotificationRegistration State Changed event.</span></span> <span data-ttu-id="c4749-106">Esto sirve para asegurarse de que la aplicación obtiene informa acerca de nuevos mensajes de la plataforma de dispositivos conectados a través del mecanismo de notificación correcto.</span><span class="sxs-lookup"><span data-stu-id="c4749-106">This is used to ensure that the application gets informed about new Connected Devices platform messages via the correct notification mechanism.</span></span>

## <a name="properties"></a><span data-ttu-id="c4749-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="c4749-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="c4749-108">cuenta</span><span class="sxs-lookup"><span data-stu-id="c4749-108">account</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="c4749-109">La cuenta para el que ha cambiado el estado de registro de notificación para.</span><span class="sxs-lookup"><span data-stu-id="c4749-109">The Account for which the notification registration state has changed for.</span></span>

### <a name="registration"></a><span data-ttu-id="c4749-110">Registro</span><span class="sxs-lookup"><span data-stu-id="c4749-110">registration</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

<span data-ttu-id="c4749-111">La información de instancia de registro cuyo estado ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="c4749-111">The information for registration instance whose state has changed.</span></span>

### <a name="state"></a><span data-ttu-id="c4749-112">Estado</span><span class="sxs-lookup"><span data-stu-id="c4749-112">state</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

<span data-ttu-id="c4749-113">El nuevo estado de registro.</span><span class="sxs-lookup"><span data-stu-id="c4749-113">The new registration state.</span></span>