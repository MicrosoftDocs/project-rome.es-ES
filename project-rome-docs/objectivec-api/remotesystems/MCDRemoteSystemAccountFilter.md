---
title: MCDRemoteSystemAccountFilter
description: Obtenga información sobre cómo filtrar cuentas para detectar sistemas remotos mediante el uso de constructores como "filterwithAccount".
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760729"
---
# <a name="class-mcdremotesystemaccountfilter"></a>las `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

Filtre las cuentas para detectar sistemas remotos con.

## <a name="properties"></a>Propiedades

### <a name="account"></a>account
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

La cuenta asociada a este MCDRemoteSystemAccountFilter.

## <a name="constructors"></a>Constructores

### <a name="filterwithaccount"></a>filterWithAccount
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Inicialice la clase con la cuenta MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Parámetros 
* `account` 

La cuenta MCDConnectedDevicesAccount que se está usando.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemAccountFilter filtrado con la cuenta.

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Inicialice la clase con la cuenta MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Parámetros 
* `account` 

La cuenta MCDConnectedDevicesAccount que se está usando.

#### <a name="returns"></a>Devoluciones
Devuelve un objeto MCDRemoteSystemAccountFilter inicializado con la cuenta.