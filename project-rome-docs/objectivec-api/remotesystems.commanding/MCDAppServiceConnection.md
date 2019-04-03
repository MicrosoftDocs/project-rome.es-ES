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
# <a name="class-mcdappserviceconnection"></a>Clase `MCDAppServiceConnection`

```
@interface MCDAppServiceConnection : NSObject
```
Esta clase administra una conexión a un servicio de aplicación remota determinada.

## <a name="properties"></a>Propiedades

### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, retain, nonnull) MCDAppServiceInfo* appServiceInfo;`

Proporciona detalles sobre el servicio de aplicación de destino al que conectarse.

### <a name="requestreceived"></a>requestReceived 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceRequestReceivedEventArgs*>* requestReceived;`

Evento para cuando se recibe una solicitud de servicio desde una aplicación remota.

### <a name="serviceclosed"></a>serviceClosed 
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDAppServiceConnection*, MCDAppServiceClosedEventArgs*>* serviceClosed;`

Evento para cuando se cierra la conexión con el servicio de aplicación.

## <a name="constructors"></a>Constructores

### <a name="init"></a>Init
`- (nullable instancetype)init;`

Crea e inicializa una nueva instancia de esta clase.

#### <a name="returns"></a>Devuelve
El inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.

### <a name="initwithappserviceinfo"></a>initWithAppServiceInfo
- (instancetype que acepta valores NULL) initWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;

#### <a name="parameters"></a>Parámetros
* `appServiceInfo` La descripción del servicio de aplicación.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.

### <a name="appserviceconnectionwithappserviceinfo"></a>appServiceConnectionWithAppServiceInfo
`+ (nullable instancetype)appServiceConnectionWithAppServiceInfo:(nonnull MCDAppServiceInfo*) appServiceInfo;`

Crea e inicializa una nueva instancia de esta clase con información de servicio de aplicación.

#### <a name="parameters"></a>Parámetros
* `appServiceInfo` 

La descripción del servicio de aplicación.

#### <a name="returns"></a>Devuelve
Devuelve el inicializado [MCDAppServiceConnection](MCDAppServiceConnection.md) si es correcto, en caso contrario nulo.

## <a name="methods"></a>Métodos

### <a name="openremoteasync"></a>openRemoteAsync
`- (void)openRemoteAsync:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest completion:(nonnull void (^)(MCDAppServiceConnectionStatus, NSError* _Nullable))completion;`

Se abre la conexión de servicio de aplicación en el dispositivo remoto especificado o la aplicación. Si no se puede abrir la conexión, se produce una excepción.

>**Nota:** Este método hará que se produce una excepción si se cumple alguna de las siguientes acciones:
> * La conexión ya está abierta o está en proceso de apertura.
> * La descripción del servicio de aplicación no se ha establecido o se ha borrado.
> * No se ha inicializado la plataforma.
> * La aplicación se ha suscrito un método de evento de "solicitud de recibido" de la conexión, pero no ha proporcionado un **MCDNotificationProvider** al inicializar la plataforma. Todos los escenarios de hospedaje requieren un **MCDNotificationProvider**.

#### <a name="parameters"></a>Parámetros
* `connectionRequest` 

La solicitud de conexión que indica qué sistema remoto o RemoteApp al destino.

### <a name="sendmessageasync"></a>sendMessageAsync
`- (void)sendMessageAsync:(nonnull NSDictionary*)message completion:(nonnull void (^)(MCDAppServiceResponse* _Nonnull, NSError* _Nullable))completion;`

Envía un mensaje al servicio de RemoteApp y comienza a realizar escuchas para una respuesta.  Este método realiza un único mensaje de solicitud-respuesta y no establecerá una conexión persistente.  Solo debe llamarse después de la conexión se abrió correctamente.

#### <a name="parameters"></a>Parámetros
* `message` 

El conjunto de pares clave-valor de datos se envíen a app service.

### <a name="close"></a>cerrar
`- (void)close;`

Cierra la conexión con el servicio de aplicación remota. La aplicación cliente debe llamar a este método cada vez que se cierra o se ha detenido por el usuario o del sistema.

### <a name="sendstatelessmessageasync"></a>sendStatelessMessageAsync
```
+ (void)sendStatelessMessageAsync:(nonnull NSDictionary*)message
                     toAppService:(nonnull MCDAppServiceInfo*)appServiceInfo
                connectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connectionRequest
                       completion:(nonnull void (^)(MCDStatelessAppServiceResponse* _Nonnull, NSError* _Nullable))completion;
```

Envía un mensaje a un servicio de aplicación remota especificada y comienza a realizar escuchas para una respuesta.

#### <a name="parameters"></a>Parámetros
* `message` El conjunto de pares clave-valor de datos se envíen a app service.
* `appServiceInfo` La información descriptiva para el servicio de aplicación de destino.
* `connectionRequest` La solicitud de conexión especifica el servicio de aplicación para conectarse a.
* `completion` La devolución de llamada de finalización asincrónico.