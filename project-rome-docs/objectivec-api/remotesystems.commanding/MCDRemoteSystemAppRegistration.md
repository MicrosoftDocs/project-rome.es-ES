---
title: MCDRemoteSystemAppRegistration
description: Esta clase representa una aplicación que va a ser registrada con la plataforma de dispositivos conectados.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 2c931d3eeacd4aa48e1ef22d573bf0325eb5b98b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909917"
---
# <a name="class-mcdremotesystemappregistration"></a>Clase `MCDRemoteSystemAppRegistration` 

```
@interface MCDRemoteSystemAppRegistration : NSObject
```  

Esta clase contiene toda la información sobre esta aplicación que otra podría detectar y utilizar.

> [!NOTE] 
> Información de MCDRemoteSystemAppRegistration debe publicarse antes de cualquier comunicación saliente a otra aplicación possble. Esto es para que la otra aplicación puede saber cómo responder a esa comunicación.

## <a name="properties"></a>Propiedades

### <a name="account"></a>cuenta
`@property(nonatomic, readonly, nullable) MCDConnectedDevicesAccount* account;`

Cuenta que pertenece este registro.

### <a name="attributes"></a>atributos
`@property(nonatomic, copy, nullable) NSDictionary<NSString*, NSString*>* attributes;`

 Diccionario de cadenas que describen los atributos de esta aplicación.

### <a name="appserviceproviders"></a>appServiceProviders
`@property(nonatomic, copy, nullable) NSArray<id<MCDAppServiceProvider>>* appServiceProviders;`

Matriz de AppServiceProviders que admite esta aplicación.

> [!NOTE] 
> Un proveedor de servicios de aplicación debe estar presente en esta matriz para recibir conexiones entrantes.  MCDRemoteSystemAppRegistration.publishAsync() no deben llamarse para que el proveedor de servicios de aplicación recibir solicitudes.  

### <a name="launchuriprovider"></a>launchUriProvider
`@property(nonatomic, readwrite, nullable) id<MCDLaunchUriProvider> launchUriProvider;`

Inicie el Uri del proveedor para esta aplicación.

> [!NOTE] 
> Un proveedor de uri de inicio debe almacenarse en esta propiedad con el fin de recibir solicitudes entrantes.  MCDRemoteSystemAppRegistration.publishAsync() no deben llamarse para que el proveedor de servicios de aplicación recibir solicitudes.  

## <a name="constructors"></a>Constructores

### <a name="getforaccount"></a>getForAccount
`+(nullable instancetype) getForAccount:(MCDConnectedDevicesAccount* _Nonnull) account
                              platform:(MCDConnectedDevicesPlatform* _Nonnull) platform;`

Obtiene el registro de aplicación actual del sistema remoto para la cuenta.

#### <a name="parameters"></a>Parámetros
* `account` 

Para recuperar el registro de la cuenta.

* `platform` 

Obtener registro de plataforma.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemAppRegistration para la cuenta proporcionada.

## <a name="methods"></a>Métodos

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(BOOL, NSError* _Nullable))callback  __attribute__((deprecated("Use publishAsync instead")));`

Guarda la información almacenada actualmente en el RemoteSystemAppRegistration tal que otras aplicaciones pueden detectarlo.

> [!NOTE] 
> MCDConnectedDevicesNotificationRegistration debe estar registrado para que esta llamada se realice correctamente.

> [!WARNING] 
> En desuso. Use publishAsync en su lugar.

#### <a name="parameters"></a>Parámetros

* `callback`

La devolución de llamada indica el resultado de guardar la información.

### <a name="publishasync"></a>publishAsync
`- (void)publishAsync:(nonnull void (^)(MCDRemoteSystemAppRegistrationPublishResult* _Nonnull, NSError* _Nullable))completionBlock;`

Publica la información almacenada actualmente en el MCDRemoteSystemAppRegistration tal que otras aplicaciones pueden detectarlo.

> [!NOTE] 
> MCDConnectedDevicesNotificationRegistration debe estar registrado para que esta llamada se realice correctamente.

#### <a name="parameters"></a>Parámetros

* `callback`

La devolución de llamada indica el resultado de guardar la información.
