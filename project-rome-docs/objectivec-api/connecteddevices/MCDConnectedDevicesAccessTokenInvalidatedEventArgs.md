---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: Informar a ese token asociado ConnectedDevicesAccount informó de un error de token.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801777"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a>Clase `MCDConnectedDevicesAccessTokenInvalidatedEventArgs` 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
Devuelve MCDConnectedDevicesAccount para informar a la que el token asociado MCDConnectedDevicesAccount informó de error de token para los ámbitos contenidos. Proveedor de tokens se necesita para actualizar su caché de tokens o potencialmente emergente de la interfaz de usuario para pedir al usuario iniciar sesión con el fin de corregir la configuración de la cuenta.

## <a name="properties"></a>Propiedades

### <a name="account"></a>cuenta
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

La cuenta asociada con este MCDConnectedDevicesAccessTokenInvalidatedEventArgs.

### <a name="scopes"></a>Ámbitos
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

La lista de ámbitos para los que debe cubrir el token cuando genera.