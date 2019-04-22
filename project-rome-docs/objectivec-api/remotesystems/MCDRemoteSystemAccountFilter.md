---
title: MCDRemoteSystemAccountFilter
description: Filtro para las cuentas descubrir los sistemas remotos con.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801557"
---
# <a name="class-mcdremotesystemaccountfilter"></a>Clase `MCDRemoteSystemAccountFilter` 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

Filtro para las cuentas descubrir los sistemas remotos con.

## <a name="properties"></a>Propiedades

### <a name="account"></a>cuenta
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

La cuenta asociada con este MCDRemoteSystemAccountFilter.

## <a name="constructors"></a>Constructores

### <a name="filterwithaccount"></a>filterWithAccount
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Inicializar la clase con la cuenta MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Parámetros 
* `account` 

La cuenta MCDConnectedDevicesAccount utilizada.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemAccountFilter filtrado con la cuenta.

### <a name="initwithaccount"></a>initWithAccount
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

Inicializar la clase con la cuenta MCDConnectedDevicesAccount.

#### <a name="parameters"></a>Parámetros 
* `account` 

La cuenta MCDConnectedDevicesAccount utilizada.

#### <a name="returns"></a>Devuelve
Devuelve un objeto MCDRemoteSystemAccountFilter inicializa filtradas con la cuenta.