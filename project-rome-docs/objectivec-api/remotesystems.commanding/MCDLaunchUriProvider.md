---
title: MCDLaunchUriProvider
description: Obtenga información sobre el protocolo MCDLaunchUriProvider. Este protocolo se utiliza para administrar el control de un URI a través del inicio de una aplicación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 3339f9b5c8ab14dddf519618795c4150b69dfe3e
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760759"
---
# <a name="protocol-mcdlaunchuriprovider"></a>n° `MCDLaunchUriProvider`

```
@protocol MCDLaunchUriProvider <NSObject>
```

Esta clase administra el control de un identificador URI mediante el inicio de una aplicación.

## <a name="properties"></a>Propiedades 
### <a name="supportedurischemes"></a>supportedUriSchemes
`@property(nonatomic, readonly, strong, nullable) NSArray<NSString*>* supportedUriSchemes;`

Matriz de cadenas que representan los esquemas de URI admitidos.

## <a name="methods"></a>Métodos

### <a name="onlaunchuriasync"></a>onLaunchUriAsync
```
- (void)onLaunchUriAsync:(nonnull NSString*)uri
         options:(nullable MCDRemoteLauncherOptions*)options
              completion:(nonnull void (^)(BOOL, NSError* _Nullable))completionBlock;
```

Se llama a este método cuando un dispositivo remoto intenta iniciar un URI en este dispositivo.

#### <a name="parameters"></a>Parámetros 
* `uri` URI que se va a iniciar.
* `options` Conjunto de opciones para iniciar el URI. El URI de reserva es solo una de las opciones posibles que se pueden establecer.
* `completionBlock` Bloque de código que se va a ejecutar cuando se complete.