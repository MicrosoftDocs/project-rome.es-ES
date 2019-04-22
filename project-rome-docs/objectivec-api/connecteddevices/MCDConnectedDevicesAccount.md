---
title: MCDConnectedDevicesAccount
description: Esta clase representa una única cuenta de usuario conocida por una aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800937"
---
# <a name="class-mcdconnecteddevicesaccount"></a>Clase `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

Esta clase representa una única cuenta de usuario conocida por una aplicación.

## <a name="properties"></a>Propiedades

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

La instancia de singleton de la cuenta anónima.

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

El identificador único para esta cuenta de usuario.

### <a name="type"></a>Tipo
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

Un valor MCDConnectedDevicesAccountType que describe el tipo de cuenta.

## <a name="constructors"></a>Constructores

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.

#### <a name="parameters"></a>Parámetros 

* `accountId` 

Una cadena de identificador único para esta cuenta de usuario.

`type` 

El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDConnectedDevicesAccount con el identificador de cuenta.

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.

#### <a name="parameters"></a>Parámetros 
* `type`

El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDConnectedDevicesAccount inicializado con el identificador de cuenta.