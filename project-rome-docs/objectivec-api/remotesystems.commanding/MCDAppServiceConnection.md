---
title: MCDAppServiceConnection
description: Obtenga información sobre la clase MCDAppServiceConnection. Esta clase administra una conexión a un servicio de aplicación remoto determinado.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 2d9153eeddb9010ac40ab37d9adb433edd11b0ca
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761059"
---
# <a name="class-mcdappserviceconnection"></a><span data-ttu-id="e07da-105">las `MCDAppServiceConnection`</span><span class="sxs-lookup"><span data-stu-id="e07da-105">class `MCDAppServiceConnection`</span></span>

```
@interface MCDAppServiceConnection : NSObject
```
<span data-ttu-id="e07da-106">Esta clase administra una conexión a un servicio de aplicación remoto determinado.</span><span class="sxs-lookup"><span data-stu-id="e07da-106">This class manages a connection to a particular remote app service.</span></span>

## <a name="properties"></a><span data-ttu-id="e07da-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="e07da-107">Properties</span></span>

### <a name="appserviceinfo"></a><span data-ttu-id="e07da-108">appServiceInfo</span><span class="sxs-lookup"><span data-stu-id="e07da-108">appServiceInfo</span></span>
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

<span data-ttu-id="e07da-109">Proporciona detalles sobre el servicio de aplicaciones de destino al que se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="e07da-109">Provides details about the target app service to connect to.</span></span>

### <a name="requestreceived"></a><span data-ttu-id="e07da-110">requestReceived</span><span class="sxs-lookup"><span data-stu-id="e07da-110">requestReceived</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

<span data-ttu-id="e07da-111">Evento para cuando se recibe una solicitud de servicio de una aplicación remota.</span><span class="sxs-lookup"><span data-stu-id="e07da-111">Event for when a service request is received from a remote app.</span></span>

### <a name="serviceclosed"></a><span data-ttu-id="e07da-112">serviceClosed</span><span class="sxs-lookup"><span data-stu-id="e07da-112">serviceClosed</span></span> 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

<span data-ttu-id="e07da-113">Evento para el momento en que se cierra la conexión a App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-113">Event for when connection to the app service closes.</span></span>

## <a name="constructors"></a><span data-ttu-id="e07da-114">Constructores</span><span class="sxs-lookup"><span data-stu-id="e07da-114">Constructors</span></span>

### <a name="init"></a><span data-ttu-id="e07da-115">init</span><span class="sxs-lookup"><span data-stu-id="e07da-115">init</span></span>
`- (nullable instancetype)init;`

<span data-ttu-id="e07da-116">Crea e inicializa una nueva instancia de esta clase.</span><span class="sxs-lookup"><span data-stu-id="e07da-116">Creates and initializes a new instance of this class.</span></span>

#### <a name="returns"></a><span data-ttu-id="e07da-117">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="e07da-117">Returns</span></span>
<span data-ttu-id="e07da-118">[MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto, de lo contrario, Nil.</span><span class="sxs-lookup"><span data-stu-id="e07da-118">The initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="initwithappserviceinfo"></a><span data-ttu-id="e07da-119">initWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="e07da-119">initWithAppServiceInfo</span></span>
- <span data-ttu-id="e07da-120">(Nullable instanceType) initWithAppServiceInfo: (nonnull MCDAppServiceInfo \*) appServiceInfo;</span><span class="sxs-lookup"><span data-stu-id="e07da-120">(nullable instancetype)initWithAppServiceInfo:(nonnull MCDAppServiceInfo\*) appServiceInfo;</span></span>

#### <a name="parameters"></a><span data-ttu-id="e07da-121">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e07da-121">Parameters</span></span>
* <span data-ttu-id="e07da-122">`appServiceInfo` La descripción de App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-122">`appServiceInfo` The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="e07da-123">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="e07da-123">Returns</span></span>
<span data-ttu-id="e07da-124">Devuelve el [MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto; de lo contrario, es nulo.</span><span class="sxs-lookup"><span data-stu-id="e07da-124">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

### <a name="appserviceconnectionwithappserviceinfo"></a><span data-ttu-id="e07da-125">appServiceConnectionWithAppServiceInfo</span><span class="sxs-lookup"><span data-stu-id="e07da-125">appServiceConnectionWithAppServiceInfo</span></span>
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

<span data-ttu-id="e07da-126">Crea e inicializa una nueva instancia de esta clase con información de App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-126">Creates and initializes a new instance of this class with app service information.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e07da-127">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e07da-127">Parameters</span></span>
* `appServiceInfo` 

<span data-ttu-id="e07da-128">La descripción de App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-128">The app service description.</span></span>

#### <a name="returns"></a><span data-ttu-id="e07da-129">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="e07da-129">Returns</span></span>
<span data-ttu-id="e07da-130">Devuelve el [MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto; de lo contrario, es nulo.</span><span class="sxs-lookup"><span data-stu-id="e07da-130">Returns the initialized [MCDAppServiceConnection](MCDAppServiceConnection.md) if successful, otherwise nil.</span></span>

## <a name="methods"></a><span data-ttu-id="e07da-131">Métodos</span><span class="sxs-lookup"><span data-stu-id="e07da-131">Methods</span></span>

### <a name="openremoteasync"></a><span data-ttu-id="e07da-132">openRemoteAsync</span><span class="sxs-lookup"><span data-stu-id="e07da-132">openRemoteAsync</span></span>
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

<span data-ttu-id="e07da-133">Abre la conexión de App Service en la aplicación o el dispositivo remoto especificado.</span><span class="sxs-lookup"><span data-stu-id="e07da-133">Opens the app service connection on the specified remote device or application.</span></span> <span data-ttu-id="e07da-134">Si no se puede abrir la conexión, se produce una excepción.</span><span class="sxs-lookup"><span data-stu-id="e07da-134">If the connection fails to open, an exception is thrown.</span></span>

><span data-ttu-id="e07da-135">**Nota:** Este método producirá una excepción si se cumple alguna de las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="e07da-135">**Note:** This method will thrown an exception if any of the following are true:</span></span>
> * <span data-ttu-id="e07da-136">La conexión ya está abierta o está en proceso de apertura.</span><span class="sxs-lookup"><span data-stu-id="e07da-136">The connection is already open or is in the process of opening.</span></span>
> * <span data-ttu-id="e07da-137">La descripción de App Service no se ha establecido o se ha borrado.</span><span class="sxs-lookup"><span data-stu-id="e07da-137">The app service description has not been set or has been cleared.</span></span>
> * <span data-ttu-id="e07da-138">La plataforma no se ha inicializado.</span><span class="sxs-lookup"><span data-stu-id="e07da-138">The platform has not been initialized.</span></span>
> * <span data-ttu-id="e07da-139">La aplicación ha suscrito un método al evento "solicitud recibida" de la conexión, pero no ha proporcionado un **MCDNotificationProvider** al inicializar la plataforma.</span><span class="sxs-lookup"><span data-stu-id="e07da-139">The app has subscribed a method to the connection's "request received" event but has not provided a **MCDNotificationProvider** when initializing the platform.</span></span> <span data-ttu-id="e07da-140">Todos los escenarios de hospedaje requieren un **MCDNotificationProvider**.</span><span class="sxs-lookup"><span data-stu-id="e07da-140">All hosting scenarios require a **MCDNotificationProvider**.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e07da-141">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e07da-141">Parameters</span></span>
* `connectionRequest` 

<span data-ttu-id="e07da-142">Solicitud de conexión que indica el sistema remoto o la aplicación remota a la que se va a dirigir.</span><span class="sxs-lookup"><span data-stu-id="e07da-142">The connection request indicating which remote system or remote app to target.</span></span>

### <a name="sendmessageasync"></a><span data-ttu-id="e07da-143">sendMessageAsync</span><span class="sxs-lookup"><span data-stu-id="e07da-143">sendMessageAsync</span></span>
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

<span data-ttu-id="e07da-144">Envía un mensaje al servicio de la aplicación remota y comienza a realizar escuchas para obtener una respuesta.</span><span class="sxs-lookup"><span data-stu-id="e07da-144">Sends a message to the remote app service and begins listening for a response.</span></span>  <span data-ttu-id="e07da-145">Este método realiza un único mensaje/respuesta y no establece una conexión persistente.</span><span class="sxs-lookup"><span data-stu-id="e07da-145">This method performs a single message/response and does not establish a persistent connection.</span></span>  <span data-ttu-id="e07da-146">Solo se debe llamar después de que la conexión se haya abierto correctamente.</span><span class="sxs-lookup"><span data-stu-id="e07da-146">It should only be called after the connection was opened successfully.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e07da-147">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e07da-147">Parameters</span></span>
* `message` 

<span data-ttu-id="e07da-148">Conjunto de datos de clave-valor que se va a enviar a App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-148">The key-value set of data to be sent to the app service.</span></span>

### <a name="close"></a><span data-ttu-id="e07da-149">cerrar</span><span class="sxs-lookup"><span data-stu-id="e07da-149">close</span></span>
`- (void)close;`

<span data-ttu-id="e07da-150">Cierra la conexión con el servicio de aplicaciones remotas.</span><span class="sxs-lookup"><span data-stu-id="e07da-150">Closes the connection to the remote app service.</span></span> <span data-ttu-id="e07da-151">La aplicación cliente debe llamar a este método siempre que sea cerrado o detenido por el usuario o el sistema.</span><span class="sxs-lookup"><span data-stu-id="e07da-151">The client app should call this method whenever it is closed or stopped by the user or system.</span></span>

### <a name="sendstatelessmessageasync"></a><span data-ttu-id="e07da-152">sendStatelessMessageAsync</span><span class="sxs-lookup"><span data-stu-id="e07da-152">sendStatelessMessageAsync</span></span>
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

<span data-ttu-id="e07da-153">Envía un mensaje a un servicio de aplicación remoto especificado y comienza a realizar escuchas para obtener una respuesta.</span><span class="sxs-lookup"><span data-stu-id="e07da-153">Sends a message to a specified remote app service and begins listening for a response.</span></span>

#### <a name="parameters"></a><span data-ttu-id="e07da-154">Parámetros</span><span class="sxs-lookup"><span data-stu-id="e07da-154">Parameters</span></span>
* <span data-ttu-id="e07da-155">`message` Conjunto de datos de clave-valor que se va a enviar a App Service.</span><span class="sxs-lookup"><span data-stu-id="e07da-155">`message` The key-value set of data to be sent to the app service.</span></span>
* <span data-ttu-id="e07da-156">`appServiceInfo` Información descriptiva para el servicio de aplicaciones de destino.</span><span class="sxs-lookup"><span data-stu-id="e07da-156">`appServiceInfo` The descriptive info for the target app service.</span></span>
* <span data-ttu-id="e07da-157">`connectionRequest` La solicitud de conexión que especifica la instancia de App Service a la que se va a conectar.</span><span class="sxs-lookup"><span data-stu-id="e07da-157">`connectionRequest` The connection request specifying the app service to connect to.</span></span>
* <span data-ttu-id="e07da-158">`completion` Devolución de llamada de finalización asincrónica.</span><span class="sxs-lookup"><span data-stu-id="e07da-158">`completion` The async completion callback.</span></span>