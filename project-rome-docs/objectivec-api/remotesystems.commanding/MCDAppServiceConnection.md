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
# <a name="class-mcdappserviceconnection"></a>las `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
Esta clase administra una conexión a un servicio de aplicación remoto determinado.

## <a name="properties"></a>Propiedades

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

Proporciona detalles sobre el servicio de aplicaciones de destino al que se va a conectar.

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

Evento para cuando se recibe una solicitud de servicio de una aplicación remota.

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

Evento para el momento en que se cierra la conexión a App Service.

## <a name="constructors"></a>Constructores

### <a name="init"></a>init
`- (nullable instancetype)init;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="returns"></a>Devoluciones
[MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto, de lo contrario, Nil.

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (Nullable instanceType) initWithAppServiceInfo: (nonnull MCDAppServiceInfo *) appServiceInfo;

#### <a name="parameters"></a>Parámetros
* `appServiceInfo` La descripción de App Service.

#### <a name="returns"></a>Devoluciones
Devuelve el [MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto; de lo contrario, es nulo.

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

Crea e inicializa una nueva instancia de esta clase con información de App Service.

#### <a name="parameters"></a>Parámetros
* `appServiceInfo` 

La descripción de App Service.

#### <a name="returns"></a>Devoluciones
Devuelve el [MCDAppServiceConnection](MCDAppServiceConnection.md) inicializado si es correcto; de lo contrario, es nulo.

## <a name="methods"></a>Métodos

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

Abre la conexión de App Service en la aplicación o el dispositivo remoto especificado. Si no se puede abrir la conexión, se produce una excepción.

>**Nota:** Este método producirá una excepción si se cumple alguna de las siguientes condiciones:
> * La conexión ya está abierta o está en proceso de apertura.
> * La descripción de App Service no se ha establecido o se ha borrado.
> * La plataforma no se ha inicializado.
> * La aplicación ha suscrito un método al evento "solicitud recibida" de la conexión, pero no ha proporcionado un **MCDNotificationProvider** al inicializar la plataforma. Todos los escenarios de hospedaje requieren un **MCDNotificationProvider**.

#### <a name="parameters"></a>Parámetros
* `connectionRequest` 

Solicitud de conexión que indica el sistema remoto o la aplicación remota a la que se va a dirigir.

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

Envía un mensaje al servicio de la aplicación remota y comienza a realizar escuchas para obtener una respuesta.  Este método realiza un único mensaje/respuesta y no establece una conexión persistente.  Solo se debe llamar después de que la conexión se haya abierto correctamente.

#### <a name="parameters"></a>Parámetros
* `message` 

Conjunto de datos de clave-valor que se va a enviar a App Service.

### <a name="close"></a>cerrar
`- (void)close;`

Cierra la conexión con el servicio de aplicaciones remotas. La aplicación cliente debe llamar a este método siempre que sea cerrado o detenido por el usuario o el sistema.

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

Envía un mensaje a un servicio de aplicación remoto especificado y comienza a realizar escuchas para obtener una respuesta.

#### <a name="parameters"></a>Parámetros
* `message` Conjunto de datos de clave-valor que se va a enviar a App Service.
* `appServiceInfo` Información descriptiva para el servicio de aplicaciones de destino.
* `connectionRequest` La solicitud de conexión que especifica la instancia de App Service a la que se va a conectar.
* `completion` Devolución de llamada de finalización asincrónica.