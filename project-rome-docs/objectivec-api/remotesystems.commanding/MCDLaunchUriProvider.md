---
title: MCDLaunchUriProvider
description: ''
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4cbfaa9fd1e88345f4ce35987508b061e479854e
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907467"
---
# <a name="protocol-mcdlaunchuriprovider"></a>Protocolo `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

Esta clase administra el control de un identificador URI mediante el inicio de una aplicación.

## <a name="properties"></a>Propiedades 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

Una matriz de cadenas que representan admite esquemas de URI.

## <a name="methods"></a>Métodos

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

Este método se llama cuando un dispositivo remoto intenta iniciar un URI de este dispositivo.

#### <a name="parameters"></a>Parámetros 
* `uri` El URI para iniciar.
* `options` Un conjunto de opciones para iniciar el URI. URI de la reserva es sólo una de las opciones posibles que se pueden establecer.
* `completionBlock` El bloque de código para ejecutar la finalización.