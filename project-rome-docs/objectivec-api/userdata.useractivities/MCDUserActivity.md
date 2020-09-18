---
title: MCDUserActivity
description: Obtenga información sobre la clase MCDUserActivity y sus propiedades. Esta clase representa una instancia de actividad de un solo usuario.
keywords: Microsoft, Windows, actividades de usuario, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760149"
---
# <a name="class-mcduseractivity"></a><span data-ttu-id="4cbb5-105">las `MCDUserActivity`</span><span class="sxs-lookup"><span data-stu-id="4cbb5-105">class `MCDUserActivity`</span></span>

```
@interface MCDUserActivity : NSObject
```

<span data-ttu-id="4cbb5-106">Esta clase representa una instancia de actividad de un solo usuario.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-106">This class represents a single user activity instance.</span></span> <span data-ttu-id="4cbb5-107">Una aplicación crea una actividad de usuario durante su ejecución para notificar al sistema de un flujo de trabajo de usuario que puede continuar en otro dispositivo o en otro momento en el mismo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-107">A user activity is created by an app during its execution to notify the system of a user work stream that can be continued on another device or at another time on the same device.</span></span> <span data-ttu-id="4cbb5-108">Proporciona información sobre una tarea en la que está trabajando el usuario.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-108">It provides information about a task the user is engaged in.</span></span>

><span data-ttu-id="4cbb5-109">**Nota:** Las instancias de MCDUserActivity tienen un límite de tamaño de 100 KB, por encima de las cuales no se pueden publicar.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-109">**Note:** MCDUserActivity instances have a size limit of 100KB, above which they cannot be published.</span></span>

## <a name="properties"></a><span data-ttu-id="4cbb5-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4cbb5-110">Properties</span></span>

### <a name="activityid"></a><span data-ttu-id="4cbb5-111">activityId</span><span class="sxs-lookup"><span data-stu-id="4cbb5-111">activityId</span></span>
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

<span data-ttu-id="4cbb5-112">IDENTIFICADOR único de esta actividad.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-112">The unique ID for this activity.</span></span>

### <a name="state"></a><span data-ttu-id="4cbb5-113">state</span><span class="sxs-lookup"><span data-stu-id="4cbb5-113">state</span></span>
`@property(nonatomic, readonly) MCDUserActivityState state;`

<span data-ttu-id="4cbb5-114">Estado de esta actividad.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-114">The state of this activity.</span></span>

### <a name="activationuri"></a><span data-ttu-id="4cbb5-115">activationUri</span><span class="sxs-lookup"><span data-stu-id="4cbb5-115">activationUri</span></span>
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

<span data-ttu-id="4cbb5-116">URI que se va a seguir cuando se active esta actividad de usuario.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-116">The URI to follow when this user activity is activated.</span></span>

### <a name="fallbackuri"></a><span data-ttu-id="4cbb5-117">fallbackUri</span><span class="sxs-lookup"><span data-stu-id="4cbb5-117">fallbackUri</span></span>
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

<span data-ttu-id="4cbb5-118">El URI descriptivo de la Web mantenido por esta actividad que se usará si se produce un error en el URI principal.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-118">The web-friendly URI held by this activity, to be used if the primary URI fails.</span></span>

### <a name="contenturi"></a><span data-ttu-id="4cbb5-119">contentUri</span><span class="sxs-lookup"><span data-stu-id="4cbb5-119">contentUri</span></span>
`@property(nonatomic, copy, nullable) NSString* contentUri;`

<span data-ttu-id="4cbb5-120">El URI de contenido para esta actividad (el URI de la imagen que se usará para representar la actividad en otro dispositivo).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-120">The content URI for this activity (the URI of the image that will be used to represent the activity on another device).</span></span>

### <a name="contenttype"></a><span data-ttu-id="4cbb5-121">contentType</span><span class="sxs-lookup"><span data-stu-id="4cbb5-121">contentType</span></span>
`@property(nonatomic, copy, nullable) NSString* contentType;`

<span data-ttu-id="4cbb5-122">el tipo MIME (Extensiones multipropósito de correo Internet) del contenido almacenado en **contentUri**.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-122">the MIME (Multipurpose Internet Mail Extensions) type of the content stored in **contentUri**.</span></span> <span data-ttu-id="4cbb5-123">Por ejemplo, "text/plain".</span><span class="sxs-lookup"><span data-stu-id="4cbb5-123">For example, "text/plain".</span></span>

### <a name="contentinfojson"></a><span data-ttu-id="4cbb5-124">contentInfoJson</span><span class="sxs-lookup"><span data-stu-id="4cbb5-124">contentInfoJson</span></span>
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

<span data-ttu-id="4cbb5-125">Información básica de contenido de esta actividad.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-125">The basic content info for this activity.</span></span> <span data-ttu-id="4cbb5-126">Por ejemplo, si la actividad estaba leyendo una fuente RSS, la cadena de contenido podría incluir el nombre del artículo y su autor.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-126">For example, if your activity was reading an RSS feed, the content string might include the name of the article and its author.</span></span>

### <a name="appdisplayname"></a><span data-ttu-id="4cbb5-127">appDisplayName</span><span class="sxs-lookup"><span data-stu-id="4cbb5-127">appDisplayName</span></span>
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

<span data-ttu-id="4cbb5-128">El nombre para mostrar de la aplicación para esta actividad.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-128">The app display name for this activity.</span></span>

### <a name="visualelements"></a><span data-ttu-id="4cbb5-129">visualElements</span><span class="sxs-lookup"><span data-stu-id="4cbb5-129">visualElements</span></span>
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

<span data-ttu-id="4cbb5-130">Los elementos visuales de esta actividad (información que se puede usar para el icono de "detalles" de la actividad).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-130">The visual elements for this activity (information that can be used for the "details" tile of the activity).</span></span>

### <a name="roamable"></a><span data-ttu-id="4cbb5-131">apto</span><span class="sxs-lookup"><span data-stu-id="4cbb5-131">roamable</span></span>
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

<span data-ttu-id="4cbb5-132">Obtiene o establece si esta actividad se va a desplazar a otros puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-132">Gets or sets whether this activity is roamed to other endpoints.</span></span>

## <a name="constructors"></a><span data-ttu-id="4cbb5-133">Constructores</span><span class="sxs-lookup"><span data-stu-id="4cbb5-133">Constructors</span></span>

### <a name="activitywithactivityid"></a><span data-ttu-id="4cbb5-134">activityWithActivityId</span><span class="sxs-lookup"><span data-stu-id="4cbb5-134">activityWithActivityId</span></span>
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="4cbb5-135">Crea una instancia de esta clase con un identificador determinado.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-135">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4cbb5-136">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4cbb5-136">Parameters</span></span>
* `activityId` 

<span data-ttu-id="4cbb5-137">Identificador de esta actividad (debe ser una cadena única).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-137">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="4cbb5-138">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="4cbb5-138">Returns</span></span>
<span data-ttu-id="4cbb5-139">Devuelve una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-139">Returns an instance of this class.</span></span>

### <a name="initwithactivityid"></a><span data-ttu-id="4cbb5-140">initWithActivityId</span><span class="sxs-lookup"><span data-stu-id="4cbb5-140">initWithActivityId</span></span>
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

<span data-ttu-id="4cbb5-141">Crea una instancia de esta clase con un identificador determinado.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-141">Creates an instance of this class with a given ID.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4cbb5-142">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4cbb5-142">Parameters</span></span>
* `activityId`

<span data-ttu-id="4cbb5-143">Identificador de esta actividad (debe ser una cadena única).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-143">The identifier for this Activity (should be a unique string).</span></span>

#### <a name="returns"></a><span data-ttu-id="4cbb5-144">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="4cbb5-144">Returns</span></span>
<span data-ttu-id="4cbb5-145">Devuelve una instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-145">Returns an instance of this class.</span></span>

## <a name="methods"></a><span data-ttu-id="4cbb5-146">Métodos</span><span class="sxs-lookup"><span data-stu-id="4cbb5-146">Methods</span></span>

### <a name="createsession"></a><span data-ttu-id="4cbb5-147">createSession</span><span class="sxs-lookup"><span data-stu-id="4cbb5-147">createSession</span></span>
`- (nonnull MCDUserActivitySession*)createSession;`

<span data-ttu-id="4cbb5-148">Crea una sesión de actividad de usuario a la que se asociará este MCDUserActivity.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-148">Creates a user activity session that this MCDUserActivity will be associated with.</span></span> <span data-ttu-id="4cbb5-149">Un MCDUserActivitySession asociado indica que el usuario está ocupado actualmente en la actividad.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-149">An associated MCDUserActivitySession indicates that the user is currently engaged in the activity.</span></span>

#### <a name="returns"></a><span data-ttu-id="4cbb5-150">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="4cbb5-150">Returns</span></span>
<span data-ttu-id="4cbb5-151">La sesión creada.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-151">The created session.</span></span>

### <a name="saveasync"></a><span data-ttu-id="4cbb5-152">saveAsync</span><span class="sxs-lookup"><span data-stu-id="4cbb5-152">saveAsync</span></span>
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

<span data-ttu-id="4cbb5-153">Publica la actividad del usuario.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-153">Publishes the user activity.</span></span> <span data-ttu-id="4cbb5-154">El MCDUserActivity debe tener un URI de activación y un miembro de VisualElements con el texto para mostrar establecido antes de llamar a este método.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-154">The MCDUserActivity must have an activation URI and a VisualElements member with set display text before this method is called.</span></span> <span data-ttu-id="4cbb5-155">Se debe llamar a este método siempre que la aplicación modifique una propiedad de MCDUserActivity (para publicar la actualización).</span><span class="sxs-lookup"><span data-stu-id="4cbb5-155">This method should be called whenever the app modifies a property of the MCDUserActivity (in order to publish the update).</span></span>

#### <a name="parameters"></a><span data-ttu-id="4cbb5-156">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4cbb5-156">Parameters</span></span>
* <span data-ttu-id="4cbb5-157">`completionBlock` Bloque de código que se va a ejecutar cuando se complete.</span><span class="sxs-lookup"><span data-stu-id="4cbb5-157">`completionBlock` The code block to execute upon completion.</span></span>