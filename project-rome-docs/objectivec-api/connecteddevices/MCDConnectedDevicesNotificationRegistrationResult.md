---
title: MCDConnectedDevicesNotificationRegistrationResult
description: Se comunica el resultado asincrónico de registrar información de notificación de una cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9ee253ff1c07f498b42ccf0cd0edeb9937f31f59
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907747"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationresult"></a><span data-ttu-id="c3078-104">Clase `MCDConnectedDevicesNotificationRegistrationResult`</span><span class="sxs-lookup"><span data-stu-id="c3078-104">class `MCDConnectedDevicesNotificationRegistrationResult`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationResult : NSObject
```  
<span data-ttu-id="c3078-105">MCDConnectedDevicesNotificationRegistrationResult se comunica el resultado asincrónico de registrar información de notificación de una cuenta.</span><span class="sxs-lookup"><span data-stu-id="c3078-105">MCDConnectedDevicesNotificationRegistrationResult communicates the async result of registering notification information for an account.</span></span> <span data-ttu-id="c3078-106">Los Estados de error que se comunica a través de este resultado se deben usar por la aplicación para volver a intentar el registro en el caso de ciertas condiciones transitorias como la red no esté disponible.</span><span class="sxs-lookup"><span data-stu-id="c3078-106">The error statuses communicated through this result should be used by the app to retry registration in the event of certain transient conditions like the network being unavailable.</span></span>

## <a name="properties"></a><span data-ttu-id="c3078-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="c3078-107">Properties</span></span>

### <a name="status"></a><span data-ttu-id="c3078-108">status</span><span class="sxs-lookup"><span data-stu-id="c3078-108">status</span></span>

`@property(nonatomic, readonly) MCDConnectedDevicesNotificationRegistrationStatus status;`

<span data-ttu-id="c3078-109">Enumeración de estado de la operación de registro.</span><span class="sxs-lookup"><span data-stu-id="c3078-109">Status enum of the registration operation.</span></span>