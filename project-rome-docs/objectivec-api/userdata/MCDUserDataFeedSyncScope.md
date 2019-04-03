---
title: MCDUserDataFeedSyncScope
description: Esta clase representa los datos de usuario que se sincronizan con la plataforma de dispositivos conectados de back-end cuando la aplicación usa cierta funcionalidad de dispositivos conectados específicos del usuario.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 941381a61c9b17c837c25b089f7c7073d581c4a8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907177"
---
# <a name="class-mcduserdatafeedsyncscope"></a><span data-ttu-id="de2be-104">Clase `MCDUserDataFeedSyncScope`</span><span class="sxs-lookup"><span data-stu-id="de2be-104">class `MCDUserDataFeedSyncScope`</span></span>

```
@interface MCDUserDataFeedSyncScope : NSObject
```
 <span data-ttu-id="de2be-105">Esta interfaz representa los datos de usuario que se sincronizan con la plataforma de dispositivos conectados de back-end cuando la aplicación usa cierta funcionalidad de dispositivos conectados específicos del usuario, como las actividades del usuario.</span><span class="sxs-lookup"><span data-stu-id="de2be-105">This interface represents the user data that is synchronized with the Connected Devices Platform backend when the app uses certain user-specific Connected Devices functionality, such as user activities.</span></span> <span data-ttu-id="de2be-106">Una instancia se recupera de forma estática desde la clase que administra dicha funcionalidad (por ejemplo, **MCDUserActivityChannel**), y se usa en la construcción de **MCDUserDataFeed**.</span><span class="sxs-lookup"><span data-stu-id="de2be-106">An instance is retrieved statically from the class that manages such functionality (e.g. **MCDUserActivityChannel**), and it is used in the construction of **MCDUserDataFeed**.</span></span>

## <a name="properties"></a><span data-ttu-id="de2be-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="de2be-107">Properties</span></span>

### <a name="platform"></a><span data-ttu-id="de2be-108">Plataforma</span><span class="sxs-lookup"><span data-stu-id="de2be-108">platform</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* platform;`

<span data-ttu-id="de2be-109">El **ConnectedDevicesPlatform** instancia que se ha inicializado para la funcionalidad de dispositivos conectados a esta aplicación.</span><span class="sxs-lookup"><span data-stu-id="de2be-109">The **ConnectedDevicesPlatform** instance that has been initialized for this app's Connected Devices functionality.</span></span>

### <a name="syncscopeflags"></a><span data-ttu-id="de2be-110">syncScopeFlags</span><span class="sxs-lookup"><span data-stu-id="de2be-110">syncScopeFlags</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSArray<NSString*>* syncScopeFlags;`

<span data-ttu-id="de2be-111">Establezca cualquier indicador opcional para filtrar las actividades entrantes.</span><span class="sxs-lookup"><span data-stu-id="de2be-111">Set any optional flags for filtering incoming activities.</span></span>

### <a name="notificationtype"></a><span data-ttu-id="de2be-112">notificationType</span><span class="sxs-lookup"><span data-stu-id="de2be-112">notificationType</span></span>
`@property (nonatomic, readwrite, nullable, copy) NSString* notificationType;`

<span data-ttu-id="de2be-113">Establecer tipo de cambio de tipo de notificación para recibir para el ámbito de sincronización de la fuente de datos de usuario</span><span class="sxs-lookup"><span data-stu-id="de2be-113">Set type of change notification type to receive for user data feed sync scope</span></span>

```