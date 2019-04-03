---
title: MCDRemoteLauncher
description: Una clase que se utiliza para iniciar una aplicación en un dispositivo remoto mediante un URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: aa0211c1edc33e8a277c4954d94fbcbb6565c923
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907387"
---
# <a name="class-mcdremotelauncher"></a>Clase `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

Una clase que se utiliza para iniciar una aplicación en un dispositivo remoto mediante un URI.


## <a name="methods"></a>Métodos

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Inicia un URI con el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Parámetros
* `uri` El URI que hará que el inicio de una aplicación.  Si el destino es Windows, se elegirá la aplicación de destino en función de esquema. Si el destino es que no son de Windows, la aplicación de destino se elegirá según la MCDRemoteSystemConnectionRequest.

* `connection` Especifica qué sistema remoto o una aplicación para conectarse a.
* `completionBlock` El bloque para invocar la finalización.

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Inicia un URI con las opciones en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Parámetros
* `uri` El URI que hará que el inicio de una aplicación, según su esquema.
* `connection` Especifica qué sistema remoto o una aplicación para conectarse a.
* `options` Las especificaciones de inicio de la aplicación.
* `completionBlock` El bloque para invocar la finalización.