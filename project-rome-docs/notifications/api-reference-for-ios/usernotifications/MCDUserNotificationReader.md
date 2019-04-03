---
title: MCDUserNotificationReader
description: Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones. También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.
keywords: Microsoft, windows, retransmisión de dispositivo, iOS procedimientos, procedimientos iPhone
ms.openlocfilehash: 486e98c30c82a7607569d252c84e4314738df6c9
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909027"
---
# <a name="class-mcdusernotificationreader"></a><span data-ttu-id="4be7a-105">Clase `MCDUserNotificationReader`</span><span class="sxs-lookup"><span data-stu-id="4be7a-105">class `MCDUserNotificationReader`</span></span>

```
@interface MCDUserNotificationReader : NSObject
```

<span data-ttu-id="4be7a-106">Esta clase proporciona nuevas notificaciones entrantes de usuario y la notificación al usuario las actualizaciones.</span><span class="sxs-lookup"><span data-stu-id="4be7a-106">This class provides new incoming user notifications and user notification updates.</span></span> <span data-ttu-id="4be7a-107">También proporciona acceso a la colección del usuario, las notificaciones se conservan en la plataforma de dispositivos conectados.</span><span class="sxs-lookup"><span data-stu-id="4be7a-107">It also provides access to the collection of user notifications persisted in the Connected Device Platform.</span></span>  

## <a name="properties"></a><span data-ttu-id="4be7a-108">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4be7a-108">Properties</span></span>

### <a name="serializedstate"></a><span data-ttu-id="4be7a-109">serializedState</span><span class="sxs-lookup"><span data-stu-id="4be7a-109">serializedState</span></span>
`@property(nonatomic, readonly, nonnull) NSString* serializedState;`

<span data-ttu-id="4be7a-110">Devuelve el estado actual del lector de cambio.</span><span class="sxs-lookup"><span data-stu-id="4be7a-110">Returns the current state of the change reader.</span></span> <span data-ttu-id="4be7a-111">Puede usarse para construir un nuevo lector desde el mismo estado.</span><span class="sxs-lookup"><span data-stu-id="4be7a-111">Can be used to construct a new reader starting from the same state.</span></span>
<span data-ttu-id="4be7a-112">Según el último lote completado de notificación cambios (o el estado inicial, si no se han completado correctamente).</span><span class="sxs-lookup"><span data-stu-id="4be7a-112">Based upon the last completed batch of notification changes (or initial state, if none have completed successfully).</span></span>

### <a name="datachanged"></a><span data-ttu-id="4be7a-113">dataChanged</span><span class="sxs-lookup"><span data-stu-id="4be7a-113">dataChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDUserNotificationReader*, MCDUserNotificationReaderDataChangedEventArgs*>* dataChanged;`

<span data-ttu-id="4be7a-114">Cambia la suscripción de eventos para MCDUserNotificationReader.</span><span class="sxs-lookup"><span data-stu-id="4be7a-114">Event subscription for MCDUserNotificationReader changed.</span></span>

## <a name="methods"></a><span data-ttu-id="4be7a-115">Métodos</span><span class="sxs-lookup"><span data-stu-id="4be7a-115">Methods</span></span>

### <a name="readbatchasyncwithmaxsize"></a><span data-ttu-id="4be7a-116">readBatchAsyncWithMaxSize</span><span class="sxs-lookup"><span data-stu-id="4be7a-116">readBatchAsyncWithMaxSize</span></span>
`- (void)readBatchAsyncWithMaxSize:(NSUInteger)maxBatchSize
                       completion:(nonnull void (^)(NSArray<MCDUserNotification*>* _Nullable, NSError* _Nullable))completion;`

<span data-ttu-id="4be7a-117">Leer los cambios de notificación incluidos nuevas notificaciones entrantes y las actualizaciones en las notificaciones existentes en lote.</span><span class="sxs-lookup"><span data-stu-id="4be7a-117">Read notification changes including new incoming notifications and updates on existing notifications in batch.</span></span>