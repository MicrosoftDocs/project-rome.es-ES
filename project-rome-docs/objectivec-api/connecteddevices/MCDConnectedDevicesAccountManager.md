---
title: MCDConnectedDevicesAccountManager
description: Proporciona un punto de entrada único para todas las características relacionadas con la cuenta en el SDK.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801647"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a>Clase `MCDConnectedDevicesAccountManager` 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
Proporciona un punto de entrada único para todas las características relacionadas con la cuenta en el SDK.

## <a name="properties"></a>Propiedades

### <a name="accesstokenrequested"></a>accessTokenRequested
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

Este evento se desencadena cuando hay una necesidad de solicitar un token. Este evento debe ser suscrito y listo para responder antes de que se envía ninguna solicitud.

### <a name="accesstokeninvalidated"></a>accessTokenInvalidated
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

Este evento se desencadena cuando un consumidor de token notifica un error de token. El proveedor de tokens se necesita para actualizar su caché de tokens o solicitar un nuevo inicio de sesión de usuario para corregir su configuración de la cuenta.

### <a name="allaccounts"></a>allAccounts
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

MCDConnectedDevicesAccount todos los que se realiza un seguimiento actualmente por este administrador.

## <a name="methods"></a>Métodos

### <a name="addaccountasync"></a>addAccountAsync
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

Agregar un administrador de cuenta para cuentas, se invocará la devolución de llamada cuando se complete.

#### <a name="parameters"></a>Parámetros 
* `callback`

El resultado de la devolución de llamada indica si la suma de la cuenta es correcta o no. 

### <a name="removeaccountasync"></a>removeAccountAsync
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

Quitar una cuenta de administrador de cuentas, se invocará la devolución de llamada cuando se complete.

#### <a name="parameters"></a>Parámetros 
* `callback` 

 El resultado de la devolución de llamada indica si la eliminación de la cuenta es correcta o no. 