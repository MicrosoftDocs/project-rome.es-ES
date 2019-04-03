---
title: MCDUserActivity
description: Esta clase representa una instancia de la actividad de usuario único.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907427"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="d58cf-104">Clase `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="d58cf-104">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="d58cf-105">Esta clase representa una instancia de la actividad de usuario único.</span><span class="sxs-lookup"><span data-stu-id="d58cf-105">This class represents a single user activity instance.</span></span> <span data-ttu-id="d58cf-106">Se crea una actividad de usuario por una aplicación durante su ejecución para notificar al sistema de un flujo de trabajo de usuario que se puede continuar en otro dispositivo o en otro momento en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d58cf-106">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="d58cf-107">Proporciona información acerca de una tarea que el usuario está ocupado en.</span><span class="sxs-lookup"><span data-stu-id="d58cf-107">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="d58cf-108">**Nota:** Las instancias de MCDUserActivity tienen un límite de tamaño de 100KB, por encima del cual no se pueden publicar.</span><span class="sxs-lookup"><span data-stu-id="d58cf-108">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="d58cf-109">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d58cf-109">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="d58cf-110">activityId</span><span class="sxs-lookup"><span data-stu-id="d58cf-110">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="d58cf-111">El identificador único para esta actividad.</span><span class="sxs-lookup"><span data-stu-id="d58cf-111">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="d58cf-112">Estado</span><span class="sxs-lookup"><span data-stu-id="d58cf-112">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="d58cf-113">El estado de esta actividad.</span><span class="sxs-lookup"><span data-stu-id="d58cf-113">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="d58cf-114">activationUri</span><span class="sxs-lookup"><span data-stu-id="d58cf-114">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="d58cf-115">El URI que seguir cuando se activa esta actividad de usuario.</span><span class="sxs-lookup"><span data-stu-id="d58cf-115">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="d58cf-116">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="d58cf-116">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="d58cf-117">El URI de aptos para la web mantenido por esta actividad, que se utilizará si se produce un error en el URI de la principal.</span><span class="sxs-lookup"><span data-stu-id="d58cf-117">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="d58cf-118">contentUri</span><span class="sxs-lookup"><span data-stu-id="d58cf-118">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="d58cf-119">El URI de contenido para esta actividad (el URI de la imagen que se usará para representar la actividad en otro dispositivo).</span><span class="sxs-lookup"><span data-stu-id="d58cf-119">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="d58cf-120">contentType</span><span class="sxs-lookup"><span data-stu-id="d58cf-120">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="d58cf-121">el tipo MIME (Multipurpose Internet Mail Extensions) del contenido almacenado en **contentUri**.</span><span class="sxs-lookup"><span data-stu-id="d58cf-121">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="d58cf-122">Por ejemplo, "text/plain".</span><span class="sxs-lookup"><span data-stu-id="d58cf-122">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="d58cf-123">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="d58cf-123">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="d58cf-124">La información básica de contenido para esta actividad.</span><span class="sxs-lookup"><span data-stu-id="d58cf-124">The basic content info for this activity.</span></span> <span data-ttu-id="d58cf-125">Por ejemplo, si su actividad estaba leyendo una fuente RSS, la cadena de contenido puede incluir el nombre del artículo y su autor.</span><span class="sxs-lookup"><span data-stu-id="d58cf-125">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="d58cf-126">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="d58cf-126">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="d58cf-127">El nombre para mostrar aplicaciones para esta actividad.</span><span class="sxs-lookup"><span data-stu-id="d58cf-127">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="d58cf-128">visualElements</span><span class="sxs-lookup"><span data-stu-id="d58cf-128">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="d58cf-129">Los elementos visuales de esta actividad (información que se puede usar para el icono "Detalles" de la actividad).</span><span class="sxs-lookup"><span data-stu-id="d58cf-129">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="d58cf-130">apto</span><span class="sxs-lookup"><span data-stu-id="d58cf-130">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="d58cf-131">Obtiene o establece si esta actividad se ha movido a otros puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="d58cf-131">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="d58cf-132">Constructores</span><span class="sxs-lookup"><span data-stu-id="d58cf-132">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="d58cf-133">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="d58cf-133">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="d58cf-134">Crea una instancia de esta clase con un identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="d58cf-134">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d58cf-135">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d58cf-135">Parameters</span></span>
* `activityId` 

<span data-ttu-id="d58cf-136">El identificador para esta actividad (debe ser una cadena única).</span><span class="sxs-lookup"><span data-stu-id="d58cf-136">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="d58cf-137">Devuelve</span><span class="sxs-lookup"><span data-stu-id="d58cf-137">Returns</span></span>
<span data-ttu-id="d58cf-138">Devuelve una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="d58cf-138">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="d58cf-139">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="d58cf-139">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="d58cf-140">Crea una instancia de esta clase con un identificador especificado.</span><span class="sxs-lookup"><span data-stu-id="d58cf-140">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="d58cf-141">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d58cf-141">Parameters</span></span>
* `activityId`

<span data-ttu-id="d58cf-142">El identificador para esta actividad (debe ser una cadena única).</span><span class="sxs-lookup"><span data-stu-id="d58cf-142">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="d58cf-143">Devuelve</span><span class="sxs-lookup"><span data-stu-id="d58cf-143">Returns</span></span>
<span data-ttu-id="d58cf-144">Devuelve una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="d58cf-144">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="d58cf-145">Métodos</span><span class="sxs-lookup"><span data-stu-id="d58cf-145">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="d58cf-146">createSession</span><span class="sxs-lookup"><span data-stu-id="d58cf-146">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="d58cf-147">Crea una sesión de la actividad de usuario que se asociará este MCDUserActivity.</span><span class="sxs-lookup"><span data-stu-id="d58cf-147">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="d58cf-148">Un asociado MCDUserActivitySession indica que el usuario esté implicado actualmente en la actividad.</span><span class="sxs-lookup"><span data-stu-id="d58cf-148">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="d58cf-149">Devuelve</span><span class="sxs-lookup"><span data-stu-id="d58cf-149">Returns</span></span>
<span data-ttu-id="d58cf-150">La sesión creada.</span><span class="sxs-lookup"><span data-stu-id="d58cf-150">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="d58cf-151">saveAsync</span><span class="sxs-lookup"><span data-stu-id="d58cf-151">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="d58cf-152">Publica la actividad del usuario.</span><span class="sxs-lookup"><span data-stu-id="d58cf-152">Publishes the user activity.</span></span> <span data-ttu-id="d58cf-153">El MCDUserActivity debe tener una identificador URI de la activación y un miembro VisualElements con conjunto de texto para mostrar antes de llama a este método.</span><span class="sxs-lookup"><span data-stu-id="d58cf-153">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="d58cf-154">Este método debe llamarse siempre que la aplicación modifica una propiedad de la MCDUserActivity (con el fin de publicar la actualización).</span><span class="sxs-lookup"><span data-stu-id="d58cf-154">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="d58cf-155">Parámetros</span><span class="sxs-lookup"><span data-stu-id="d58cf-155">Parameters</span></span>
* <span data-ttu-id="d58cf-156">`completionBlock` El bloque de código para ejecutar la finalización.</span><span class="sxs-lookup"><span data-stu-id="d58cf-156">`completionBlock` The code block to execute upon completion.</span></span>