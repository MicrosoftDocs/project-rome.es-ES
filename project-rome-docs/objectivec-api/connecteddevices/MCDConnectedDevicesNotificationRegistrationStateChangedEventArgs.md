---
title: MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs
description: Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 83b59cc884cc0e8d59387b95388b4b7b2b5fa273
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800697"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatechangedeventargs"></a><span data-ttu-id="88853-104">Clase `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="88853-104">class `MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs : NSObject
```  
<span data-ttu-id="88853-105">Clase de argumentos de evento para el evento de cambio de estado de MCDConnectedDevicesNotificationRegistration.</span><span class="sxs-lookup"><span data-stu-id="88853-105">Event Args class for the MCDConnectedDevicesNotificationRegistration State Changed event.</span></span> <span data-ttu-id="88853-106">Esto sirve para asegurarse de que la aplicación obtiene informa acerca de nuevos mensajes de la plataforma de dispositivos conectados a través del mecanismo de notificación correcto.</span><span class="sxs-lookup"><span data-stu-id="88853-106">This is used to ensure that the application gets informed about new Connected Devices platform messages via the correct notification mechanism.</span></span>

## <a name="properties"></a><span data-ttu-id="88853-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="88853-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="88853-108">cuenta</span><span class="sxs-lookup"><span data-stu-id="88853-108">account</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="88853-109">La cuenta para el que ha cambiado el estado de registro de notificación para.</span><span class="sxs-lookup"><span data-stu-id="88853-109">The Account for which the notification registration state has changed for.</span></span>

### <a name="registration"></a><span data-ttu-id="88853-110">Registro</span><span class="sxs-lookup"><span data-stu-id="88853-110">registration</span></span>
`@property(nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistration* registration;`

<span data-ttu-id="88853-111">La información de instancia de registro cuyo estado ha cambiado.</span><span class="sxs-lookup"><span data-stu-id="88853-111">The information for registration instance whose state has changed.</span></span>

### <a name="state"></a><span data-ttu-id="88853-112">Estado</span><span class="sxs-lookup"><span data-stu-id="88853-112">state</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationState state;`

<span data-ttu-id="88853-113">El nuevo estado de registro.</span><span class="sxs-lookup"><span data-stu-id="88853-113">The new registration state.</span></span>