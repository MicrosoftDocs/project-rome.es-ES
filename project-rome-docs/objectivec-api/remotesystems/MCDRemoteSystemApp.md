---
title: MCDRemoteSystemApp
description: Representa una aplicación en un sistema remoto que está disponible para la conectividad.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 28ec3fbe03150cb45c0a554a0499f1a6b657e50d
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907657"
---
# <a name="class-mcdremotesystemapp"></a>Clase `MCDRemoteSystemApp` 

```
@interface MCDRemoteSystemApp : NSObject
```  

Representa una aplicación en un sistema remoto que está disponible para la conectividad.

## <a name="properties"></a>Propiedades

### <a name="appid"></a>appId
`@property(nonatomic, readonly, nonnull) NSString* appId;`

Un identificador único para esta aplicación.

### <a name="displayname"></a>displayName
`@property(nonatomic, readonly, nonnull) NSString* displayName;`

El nombre para mostrar descriptivo para esta aplicación. Este es el nombre utilizado por el dispositivo para la identificación de Bluetooth. Si esto no se ha establecido o el dispositivo no es compatible con Bluetooth, este campo estará vacío.

### <a name="availablebyproximity"></a>availableByProximity
`@property(nonatomic, readonly, getter=isAvailableByProximity) BOOL availableByProximity;`

Indica si esta aplicación está actualmente disponible para la conexión articulaciones próximas.

### <a name="availablebyspatialproximity"></a>availableBySpatialProximity
`@property(nonatomic, readonly, getter=isAvailableBySpatialProximity) BOOL availableBySpatialProximity;`

Indica si esta aplicación está disponible actualmente para la conexión compartida espacial.

### <a name="attributes"></a>atributos
`@property(nonatomic, readonly, nonnull) NSDictionary<NSString*, NSString*>* attributes;`

Un diccionario de pares clave/valor que define los atributos de esta aplicación.

### <a name="appservices"></a>appServices
`@property(nonatomic, readonly, nullable) NSArray<MCDAppServiceDescription*>* appServices;`

Una matriz de instancias de MCDAppServiceDescription que describe los servicios de aplicación que proporciona esta aplicación para la conectividad remota.

### <a name="accounts"></a>cuentas
`@property(nonatomic, readonly, nullable) NSArray<MCDConnectedDevicesAccount*>* accounts;`

La cuenta asociada con el MCDRemoteSystemApp que debe saber acerca de los permisos. ¿Qué determina los permisos es si el MCDConnectedDevicesAccount existe en el MCDConnectedDevicesAccountManager cuando se inicia el MCDRemoteSystemWatcher.