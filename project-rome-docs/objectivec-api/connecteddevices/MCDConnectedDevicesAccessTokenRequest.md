---
title: MCDConnectedDevicesAccessTokenRequest
description: Solicitud de un token de acceso para el MCDConnectedDevicesAccount independiente que satisface los ámbitos contenidos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b1cd9b747e98d5e9ccf4885b33897e8c240d7673
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907617"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a>Clase `MCDConnectedDevicesAccessTokenRequest` 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
Solicitud de un token de acceso para el MCDConnectedDevicesAccount independiente que satisface los ámbitos contenidos.

## <a name="properties"></a>Propiedades

### <a name="account"></a>cuenta
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

La cuenta asociada con este MCDConnectedDevicesAccessTokenInvalidatedEventArgs.

### <a name="scopes"></a>Ámbitos
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

La lista de ámbitos para los que debe cubrir el token cuando genera.

## <a name="methods"></a>Métodos

### <a name="completewithaccesstoken"></a>completeWithAccessToken
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

Si un token con los ámbitos solicitados se generó correctamente, llame a este método con el token para completar la solicitud.

#### <a name="parameters"></a>Parámetros 
* `token` 

Token generado correctamente

### <a name="completewitherrormessage"></a>completeWithErrorMessage
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

Si un token con los ámbitos solicitados no se generó correctamente por cualquier motivo, llame a este método con un mensaje que se usará para el registro.

#### <a name="parameters"></a>Parámetros 
* `errorMessage`

Un mensaje que describe por qué el token no tuvo éxito.