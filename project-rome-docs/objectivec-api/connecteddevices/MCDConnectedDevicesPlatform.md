---
title: MCDConnectedDevicesPlatform
description: Una clase para representar la plataforma de dispositivos conectados y administrar la conexión de la aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 33fdb6f7dfd7d11831da1f7710215e35306d79d1
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909747"
---
# <a name="class-mcdconnecteddevicesplatform"></a>Clase `MCDConnectedDevicesPlatform` 

```
@interface MCDConnectedDevicesPlatform : NSObject
```  
Esta clase para representar la plataforma de dispositivos conectados y administrar la conexión de la aplicación.

## <a name="properties"></a>Propiedades

### <a name="accountmanager"></a>accountManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccountManager* accountManager;`

Instancia de MCDConnectedDevicesAccountManager mantenido por la plataforma.

### <a name="notificationregistrationmanager"></a>notificationRegistrationManager
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesNotificationRegistrationManager* notificationRegistrationManager;`

Instancia de MCDConnectedDevicesNotificationRegistrationManager mantenido por la plataforma.

## <a name="constructors"></a>Constructores

### <a name="platformwithsettings"></a>platformWithSettings
`+ (nullable instancetype)platformWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

Una nueva instancia de esta clase con la configuración de plataforma especificado.

#### <a name="parameters"></a>Parámetros 
* `settings` 

El objeto MCDConnectedDevicesPlatformSettings que almacena la configuración de la aplicación de la plataforma.

#### <a name="returns"></a>Devuelve

Devuelve un objeto MCDConnectedDevicesPlatform que contiene la configuración de la plataforma de la aplicación.

### <a name="initwithsettings"></a>initWithSettings
`- (nullable instancetype)initWithSettings:(MCDConnectedDevicesPlatformSettings* _Nonnull)settings;`

Una nueva instancia de esta clase con la configuración de plataforma.

#### <a name="parameters"></a>Parámetros 
* `settings` 

El objeto MCDConnectedDevicesPlatformSettings que almacena la configuración de la aplicación de la plataforma.

#### <a name="returns"></a>Devuelve

Devuelve un objeto MCDConnectedDevicesPlatform inicializado con la configuración de la plataforma de la aplicación.

## <a name="methods"></a>Métodos

### <a name="processnotification"></a>processNotification
`- (MCDConnectedDevicesProcessNotificationOperation* _Nonnull)processNotification:(NSDictionary* _Nonnull)notification;`

Procesar la notificación de APNs entrante.

#### <a name="parameters"></a>Parámetros 
* `notification` 

Contiene la notificación de APNs para procesar.

#### <a name="returns"></a>Devuelve

Una instancia de la clase MCDConnectedDevicesProcessNotificationOperation.

### <a name="start"></a>start
`- (void) start;`

Inicie la plataforma.

### <a name="shutdownasync"></a>shutdownAsync
`- (void)shutdownAsync:(void (^_Nonnull)(NSError* _Nullable))completionBlock;`

Se cierra la plataforma de dispositivos conectados.

#### <a name="parameters"></a>Parámetros 
* `completionBlock` 

El bloque para invocar la finalización.