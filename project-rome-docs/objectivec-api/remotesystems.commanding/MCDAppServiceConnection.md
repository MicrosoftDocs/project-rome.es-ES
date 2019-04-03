---
title: MCDAppServiceConnection
description: Esta clase administra una conexión a un servicio de aplicación remota determinada.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 22e253f137642ad609a22af33aa62e2ef9543503
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908547"
---
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="9758a-104">Clase `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="9758a-104">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="9758a-105">Esta clase administra una conexión a un servicio de aplicación remota determinada.</span><span class="sxs-lookup"><span data-stu-id="9758a-105">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="9758a-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="9758a-106">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="9758a-107">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="9758a-107">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="9758a-108">Proporciona detalles sobre el servicio de aplicación de destino al que conectarse.</span><span class="sxs-lookup"><span data-stu-id="9758a-108">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="9758a-109">requestReceived</span><span class="sxs-lookup"><span data-stu-id="9758a-109">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="9758a-110">Evento para cuando se recibe una solicitud de servicio desde una aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="9758a-110">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="9758a-111">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="9758a-111">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="9758a-112">Evento para cuando se cierra la conexión con el servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="9758a-112">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="9758a-113">Constructores</span><span class="sxs-lookup"><span data-stu-id="9758a-113">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="9758a-114">Init</span><span class="sxs-lookup"><span data-stu-id="9758a-114">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="9758a-115">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="9758a-115">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="9758a-116">Devuelve</span><span class="sxs-lookup"><span data-stu-id="9758a-116">Returns</span></span>
<span data-ttu-id="9758a-117">El inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="9758a-117">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="9758a-118">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="9758a-118">initWithAppServiceInfo</span></span>
- <span data-ttu-id="9758a-119">(instancetype que acepta valores NULL) initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span><span class="sxs-lookup"><span data-stu-id="9758a-119">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="9758a-120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9758a-120">Parameters</span></span>
* <span data-ttu-id="9758a-121">`appServiceInfo` La descripción del servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="9758a-121">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="9758a-122">Devuelve</span><span class="sxs-lookup"><span data-stu-id="9758a-122">Returns</span></span>
<span data-ttu-id="9758a-123">Devuelve el inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="9758a-123">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="9758a-124">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="9758a-124">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="9758a-125">Crea e inicializa una nueva instancia de esta clase con información de servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="9758a-125">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9758a-126">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9758a-126">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="9758a-127">La descripción del servicio de aplicación.</span><span class="sxs-lookup"><span data-stu-id="9758a-127">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="9758a-128">Devuelve</span><span class="sxs-lookup"><span data-stu-id="9758a-128">Returns</span></span>
<span data-ttu-id="9758a-129">Devuelve el inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.</span><span class="sxs-lookup"><span data-stu-id="9758a-129">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="9758a-130">Métodos</span><span class="sxs-lookup"><span data-stu-id="9758a-130">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="9758a-131">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="9758a-131">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="9758a-132">Se abre la conexión de servicio de aplicación en el dispositivo remoto especificado o la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9758a-132">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="9758a-133">Si no se puede abrir la conexión, se produce una excepción.</span><span class="sxs-lookup"><span data-stu-id="9758a-133">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="9758a-134">**Nota:** Este método hará que se produce una excepción si se cumple alguna de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="9758a-134">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="9758a-135">La conexión ya está abierta o está en proceso de apertura.</span><span class="sxs-lookup"><span data-stu-id="9758a-135">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="9758a-136">La descripción del servicio de aplicación no se ha establecido o se ha borrado.</span><span class="sxs-lookup"><span data-stu-id="9758a-136">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="9758a-137">No se ha inicializado la plataforma.</span><span class="sxs-lookup"><span data-stu-id="9758a-137">The platform has not been initialized.</span></span>
> * <span data-ttu-id="9758a-138">La aplicación se ha suscrito un método de evento de "solicitud de recibido" de la conexión, pero no ha proporcionado un **MCDNotificationProvider** al inicializar la plataforma.</span><span class="sxs-lookup"><span data-stu-id="9758a-138">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="9758a-139">Todos los escenarios de hospedaje requieren un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="9758a-139">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9758a-140">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9758a-140">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="9758a-141">La solicitud de conexión que indica qué sistema remoto o RemoteApp al destino.</span><span class="sxs-lookup"><span data-stu-id="9758a-141">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="9758a-142">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="9758a-142">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="9758a-143">Envía un mensaje al servicio de RemoteApp y comienza a realizar escuchas para una respuesta.</span><span class="sxs-lookup"><span data-stu-id="9758a-143">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="9758a-144">Este método realiza un único mensaje de solicitud-respuesta y no establecerá una conexión persistente.</span><span class="sxs-lookup"><span data-stu-id="9758a-144">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="9758a-145">Solo debe llamarse después de la conexión se abrió correctamente.</span><span class="sxs-lookup"><span data-stu-id="9758a-145">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9758a-146">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9758a-146">Parameters</span></span>
* `message` 

<span data-ttu-id="9758a-147">El conjunto de pares clave-valor de datos se envíen a app service.</span><span class="sxs-lookup"><span data-stu-id="9758a-147">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="9758a-148">cerrar</span><span class="sxs-lookup"><span data-stu-id="9758a-148">close</span></span>
`- (void)close;`

<span data-ttu-id="9758a-149">Cierra la conexión con el servicio de aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="9758a-149">Closes the connection to the remote app service.</span></span> <span data-ttu-id="9758a-150">La aplicación cliente debe llamar a este método cada vez que se cierra o se ha detenido por el usuario o del sistema.</span><span class="sxs-lookup"><span data-stu-id="9758a-150">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="9758a-151">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="9758a-151">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="9758a-152">Envía un mensaje a un servicio de aplicación remota especificada y comienza a realizar escuchas para una respuesta.</span><span class="sxs-lookup"><span data-stu-id="9758a-152">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="9758a-153">Parámetros</span><span class="sxs-lookup"><span data-stu-id="9758a-153">Parameters</span></span>
* <span data-ttu-id="9758a-154">`message` El conjunto de pares clave-valor de datos se envíen a app service.</span><span class="sxs-lookup"><span data-stu-id="9758a-154">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="9758a-155">`appServiceInfo` La información descriptiva para el servicio de aplicación de destino.</span><span class="sxs-lookup"><span data-stu-id="9758a-155">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="9758a-156">`connectionRequest` La solicitud de conexión especifica el servicio de aplicación para conectarse a.</span><span class="sxs-lookup"><span data-stu-id="9758a-156">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="9758a-157">`completion` La devolución de llamada de finalización asincrónico.</span><span class="sxs-lookup"><span data-stu-id="9758a-157">`completion` The async completion callback.</span></span>