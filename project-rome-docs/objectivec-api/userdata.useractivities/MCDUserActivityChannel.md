---
title: MCDUserActivityChannel
description: Esta clase controla la adición y la consulta de las actividades del usuario para la aplicación.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b047af1da3ba79be88a53cf589c3894892b01ef4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907807"
---
# <a name="class-mcduseractivitychannel"></a><span data-ttu-id="ad33d-104">Clase `MCDUserActivityChannel`</span><span class="sxs-lookup"><span data-stu-id="ad33d-104">class `MCDUserActivityChannel`</span></span>

```
@interface MCDUserActivityChannel : NSObject
```

<span data-ttu-id="ad33d-105">Esta clase controla la adición y la consulta de las actividades del usuario para la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ad33d-105">This class handles the adding and querying of user activities for the application.</span></span>

## <a name="properties"></a><span data-ttu-id="ad33d-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="ad33d-106">Properties</span></span>

### <a name="syncscope"></a><span data-ttu-id="ad33d-107">syncScope</span><span class="sxs-lookup"><span data-stu-id="ad33d-107">syncScope</span></span>
`@property(class, readonly, nonnull) MCDUserDataFeedSyncScope* syncScope;`

<span data-ttu-id="ad33d-108">Obtiene el valor de ámbito de sincronización de datos de usuario para las actividades del usuario.</span><span class="sxs-lookup"><span data-stu-id="ad33d-108">Gets the user data sync scope value for User Activities.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="ad33d-109">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="ad33d-109">appDisplayName</span></span>
`@property(nonatomic, copy, nullable) NSString* appDisplayName;`

<span data-ttu-id="ad33d-110">El nombre para mostrar de la aplicación para todas las actividades.</span><span class="sxs-lookup"><span data-stu-id="ad33d-110">The display name of the app for all activities.</span></span>

## <a name="constructors"></a><span data-ttu-id="ad33d-111">Constructores</span><span class="sxs-lookup"><span data-stu-id="ad33d-111">Constructors</span></span>

### <a name="channelwithuserdatafeed"></a><span data-ttu-id="ad33d-112">channelWithUserDataFeed</span><span class="sxs-lookup"><span data-stu-id="ad33d-112">channelWithUserDataFeed</span></span>
`+ (nullable instancetype)channelWithUserDataFeed:(nonnull MCDUserDataFeed*)userDataFeed;`

<span data-ttu-id="ad33d-113">Crea una instancia de esta clase con la fuente de datos de usuario.</span><span class="sxs-lookup"><span data-stu-id="ad33d-113">Creates an instance of this class with the user data feed.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-114">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-114">Parameters</span></span>
* <span data-ttu-id="ad33d-115">`userDataFeed` Los datos de usuario asociados con las actividades en este canal.</span><span class="sxs-lookup"><span data-stu-id="ad33d-115">`userDataFeed` The user data associated with the activities on this channel.</span></span>

#### <a name="returns"></a><span data-ttu-id="ad33d-116">Devuelve</span><span class="sxs-lookup"><span data-stu-id="ad33d-116">Returns</span></span>
<span data-ttu-id="ad33d-117">Devuelve una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="ad33d-117">Returns a new instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="ad33d-118">Métodos</span><span class="sxs-lookup"><span data-stu-id="ad33d-118">Methods</span></span>

### <a name="getorcreateuseractivityasync"></a><span data-ttu-id="ad33d-119">getOrCreateUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-119">getOrCreateUserActivityAsync</span></span>
`- (void)getOrCreateUserActivityAsync:(nonnull NSString*)activityId
                          completion:(nonnull void (^)(MCDUserActivity* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-120">Crea la actividad del usuario especificado u obtiene una referencia a él si ya existe.</span><span class="sxs-lookup"><span data-stu-id="ad33d-120">Creates the specified user activity, or gets a reference to it if it already exists.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-121">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-121">Parameters</span></span>
* <span data-ttu-id="ad33d-122">`activityId` El identificador para esta actividad.</span><span class="sxs-lookup"><span data-stu-id="ad33d-122">`activityId` The ID for this activity.</span></span>
* <span data-ttu-id="ad33d-123">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-123">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="ad33d-124">Esto proporciona acceso a la actividad recuperada.</span><span class="sxs-lookup"><span data-stu-id="ad33d-124">This provides access to the retrieved activity.</span></span>

### <a name="deleteactivityasync"></a><span data-ttu-id="ad33d-125">deleteActivityAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-125">deleteActivityAsync</span></span>
`- (void)deleteActivityAsync:(nonnull NSString*)activityId completion:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-126">Elimina la actividad de usuario determinado.</span><span class="sxs-lookup"><span data-stu-id="ad33d-126">Deletes the given user activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-127">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-127">Parameters</span></span>
* <span data-ttu-id="ad33d-128">`activityId` El identificador de la actividad va a eliminar.</span><span class="sxs-lookup"><span data-stu-id="ad33d-128">`activityId` The ID of the activity to delete.</span></span>
* <span data-ttu-id="ad33d-129">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-129">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="deleteallactivitiesasync"></a><span data-ttu-id="ad33d-130">deleteAllActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-130">deleteAllActivitiesAsync</span></span>
`- (void)deleteAllActivitiesAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-131">Elimina todas las actividades del usuario.</span><span class="sxs-lookup"><span data-stu-id="ad33d-131">Deletes all user activities.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-132">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-132">Parameters</span></span>
* <span data-ttu-id="ad33d-133">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-133">`completionBlock` The code block to execute upon completion.</span></span>

### <a name="getrecentuseractivitiesasync"></a><span data-ttu-id="ad33d-134">getRecentUserActivitiesAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-134">getRecentUserActivitiesAsync</span></span>
`- (void)getRecentUserActivitiesAsync:(NSInteger)maxUniqueActivities
                          completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-135">Obtiene un historial de las actividades recientes del usuario.</span><span class="sxs-lookup"><span data-stu-id="ad33d-135">Gets a history of recent user activities.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="ad33d-136">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-136">Parameters</span></span>
* <span data-ttu-id="ad33d-137">`maxUniqueActivities` El número máximo de las actividades del usuario para recuperar.</span><span class="sxs-lookup"><span data-stu-id="ad33d-137">`maxUniqueActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="ad33d-138">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-138">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="ad33d-139">Esto proporciona acceso al historial de la actividad.</span><span class="sxs-lookup"><span data-stu-id="ad33d-139">This provides access to the activity history.</span></span>

### <a name="getsessionhistoryitemsforuseractivityasync"></a><span data-ttu-id="ad33d-140">getSessionHistoryItemsForUserActivityAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-140">getSessionHistoryItemsForUserActivityAsync</span></span>
`- (void)getSessionHistoryItemsForUserActivityAsync:(nonnull NSString*)activityId
                                     withStartTime:(nonnull NSDate*)startTime
                                        completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull, NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-141">Obtiene las entradas del historial de la sesión para una actividad determinada.</span><span class="sxs-lookup"><span data-stu-id="ad33d-141">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-142">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-142">Parameters</span></span>
* <span data-ttu-id="ad33d-143">`activityId` Identificador de la actividad para obtener el historial.</span><span class="sxs-lookup"><span data-stu-id="ad33d-143">`activityId` The ID of the activity to get history for.</span></span>
* <span data-ttu-id="ad33d-144">`startTime` La hora en que se considere la posibilidad de historial de la sesión.</span><span class="sxs-lookup"><span data-stu-id="ad33d-144">`startTime` The time at which to consider session history.</span></span>
* <span data-ttu-id="ad33d-145">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-145">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="ad33d-146">Esto proporciona acceso al historial de la actividad.</span><span class="sxs-lookup"><span data-stu-id="ad33d-146">This provides access to the activity history.</span></span>

### <a name="getrecentsessionhistoryitemsfortimerangeasync"></a><span data-ttu-id="ad33d-147">getRecentSessionHistoryItemsForTimeRangeAsync</span><span class="sxs-lookup"><span data-stu-id="ad33d-147">getRecentSessionHistoryItemsForTimeRangeAsync</span></span>
`- (void)getRecentSessionHistoryItemsForTimeRangeAsync:(nonnull NSDate*)startTime
                                 endTime:(nonnull NSDate*)endTime
                                 maxActivities:(NSInteger)maxActivities
                                 completion:(void (^_Nonnull)(NSArray<MCDUserActivitySessionHistoryItem*>* _Nonnull,
                                                       NSError* _Nullable))completionBlock;`

<span data-ttu-id="ad33d-148">Obtiene las entradas del historial de la sesión para una actividad determinada.</span><span class="sxs-lookup"><span data-stu-id="ad33d-148">Gets the session history entries for a given activity.</span></span>

#### <a name="parameters"></a><span data-ttu-id="ad33d-149">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ad33d-149">Parameters</span></span>
* <span data-ttu-id="ad33d-150">`startTime` La hora en que se va a empezar a considerar el historial de la sesión.</span><span class="sxs-lookup"><span data-stu-id="ad33d-150">`startTime` The time at which to start considering session history.</span></span>
* <span data-ttu-id="ad33d-151">`endTime` La hora en que se va a terminar teniendo en cuenta el historial de la sesión.</span><span class="sxs-lookup"><span data-stu-id="ad33d-151">`endTime` The time at which to end considering session history.</span></span>
* <span data-ttu-id="ad33d-152">`maxActivities` El número máximo de las actividades del usuario para recuperar.</span><span class="sxs-lookup"><span data-stu-id="ad33d-152">`maxActivities` The maximum number of user activities to retrieve.</span></span>
* <span data-ttu-id="ad33d-153">`completion` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-153">`completion` The code block to execute upon completion.</span></span>
* <span data-ttu-id="ad33d-154">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="ad33d-154">`completionBlock` The code block to execute upon completion.</span></span> <span data-ttu-id="ad33d-155">Esto proporciona acceso al historial de la actividad.</span><span class="sxs-lookup"><span data-stu-id="ad33d-155">This provides access to the activity history.</span></span>