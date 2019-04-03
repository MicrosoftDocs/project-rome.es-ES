---
title: MCDAppServiceInfo
description: Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5cb01d664a07653387b523eeec68ebd50bbc2798
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907117"
---
# <a name="class-mcdappserviceinfo"></a>Clase `MCDAppServiceInfo` 

```
@interface MCDAppServiceInfo : NSObject<NSCopying>
```  

Esta clase describe un servicio de aplicación que pertenece a una aplicación o dispositivo remoto.

## <a name="properties"></a>Propiedades

### <a name="name"></a>NAME
`@property(nonatomic, readonly, nullable) NSString* name;`

El nombre del servicio en la aplicación que se describe.

### <a name="packageid"></a>packageId
`@property(nonatomic, readonly, nullable) NSString* packageId;`

El identificador del paquete de app service que se describe.

## <a name="constructors"></a>Constructores

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name;`

Inicializar la clase con información y el nombre del servicio en la aplicación.

#### <a name="parameters"></a>Parámetros 
* `name` 

El nombre del servicio en la aplicación que se describe.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name;`

Inicializar la clase con el nombre del servicio en la aplicación.

#### <a name="parameters"></a>Parámetros 
* `name` 

El nombre del servicio en la aplicación que se describe.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.

### <a name="infowithname"></a>infoWithName
`+ (nullable instancetype)infoWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

Inicializar la clase con información y el nombre del servicio en la aplicación.

#### <a name="parameters"></a>Parámetros 
* `name` 

El nombre del servicio en la aplicación que se describe.

* `packageId` 

El identificador del paquete de app service que se describe.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDAppServiceInfo que contiene el nombre proporcionado.

### <a name="initwithname"></a>initWithName
`- (nullable instancetype)initWithName:(nonnull NSString*)name packageId:(nonnull NSString*)packageId;`

Inicializar la clase con el nombre del servicio en la aplicación.

#### <a name="parameters"></a>Parámetros 
* `name` 

El nombre del servicio en la aplicación que se describe.

* `packageId` 

El identificador del paquete de app service que se describe.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDAppServiceInfo inicializado con el nombre proporcionado.
