---
title: MCDRemoteLauncher
description: Obtenga información sobre la clase MCDRemoteLauncher. Esta clase se usa para iniciar una aplicación en un dispositivo remoto mediante un URI.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: e5231897241e54c44b4f3fb299adf68af396cac9
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760749"
---
# <a name="class-mcdremotelauncher"></a>las `MCDRemoteLauncher` 

```
@interface MCDRemoteLauncher : NSObject
```  

Una clase que se usa para iniciar una aplicación en un dispositivo remoto mediante un URI.


## <a name="methods"></a>Métodos

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Inicia un URI en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Parámetros
* `uri` El URI que hará que se inicie una aplicación.  Si el destino es Windows, la aplicación de destino se elegirá según el esquema. Si el destino no es Windows, la aplicación de destino se elegirá en función de MCDRemoteSystemConnectionRequest.

* `connection` Especifica a qué sistema o aplicación remoto se va a conectar.
* `completionBlock` Bloque que se va a invocar al finalizar.

### <a name="launchuriasync"></a>launchUriAsync
```
- (void)launchUriAsync:(nonnull NSString*)uri
 withConnectionRequest:(nonnull MCDRemoteSystemConnectionRequest*)connection
               options:(nullable MCDRemoteLauncherOptions*)options
            completion:(nullable void (^)(MCDRemoteLaunchUriStatus result, NSError* _Nullable error))completionBlock;
```

Inicia un URI con opciones en el sistema remoto especificado en un [MCDRemoteSystemConnectionRequest](MCDRemoteSystemConnectionRequest.md).

#### <a name="parameters"></a>Parámetros
* `uri` El URI que hará que se inicie una aplicación, según su esquema.
* `connection` Especifica a qué sistema o aplicación remoto se va a conectar.
* `options` Especificaciones de inicio de la aplicación.
* `completionBlock` Bloque que se va a invocar al finalizar.