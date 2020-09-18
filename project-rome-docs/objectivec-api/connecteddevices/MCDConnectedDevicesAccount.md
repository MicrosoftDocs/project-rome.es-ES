---
title: MCDConnectedDevicesAccount
description: Obtenga información sobre la clase MCDConnectedDevicesAccount. Esta clase representa una cuenta de usuario única conocida por una aplicación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: b3004681c2bcbb0ad9d5b1dcb15fe8a711773767
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761049"
---
# <a name="class-mcdconnecteddevicesaccount"></a>las `MCDConnectedDevicesAccount`

```
@interface MCDConnectedDevicesAccount : NSObject
```  

Esta clase representa una cuenta de usuario única conocida por una aplicación.

## <a name="properties"></a>Propiedades

### <a name="anonymousaccount"></a>anonymousAccount
`+ (nullable instancetype)anonymousAccount;`

Instancia singleton de la cuenta anónima.

### <a name="accountid"></a>accountId
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

Identificador único de esta cuenta de usuario.

### <a name="type"></a>type
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

Un valor de MCDConnectedDevicesAccountType que describe el tipo de cuenta.

## <a name="constructors"></a>Constructores

### <a name="accountwithaccountid"></a>accountWithAccountId
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Nueva instancia de esta clase con el identificador único para esta cuenta de usuario.

#### <a name="parameters"></a>Parámetros 

* `accountId` 

Una cadena de identificador único para esta cuenta de usuario.

`type` 

El MCDConnectedDevicesAccountType de la cuenta (depende del proveedor de IDENTIFICADOres de la cuenta).

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDConnectedDevicesAccount con el identificador de cuenta.

### <a name="initwithaccountid"></a>initWithAccountId
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

Nueva instancia de esta clase con el identificador único para esta cuenta de usuario.

#### <a name="parameters"></a>Parámetros 
* `type`

El MCDConnectedDevicesAccountType de la cuenta (depende del proveedor de IDENTIFICADOres de la cuenta).

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDConnectedDevicesAccount inicializado con el identificador de cuenta.