---
title: MCDAppServiceProvider
description: Este protocolo contiene métodos para hacer que un servicio de aplicación local puede tener acceso a los dispositivos remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: f5af56a2c87e3b4335a2a59a0130ef3622af6c26
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800457"
---
# <a name="protocol-mcdappserviceprovider"></a>Protocolo `MCDAppServiceProvider`

```
@protocol MCDAppServiceProvider<NSObject>
```

Este protocolo contiene métodos para hacer que un servicio de aplicación local puede tener acceso a los dispositivos remotos. Los desarrolladores deben implementar este protocolo para que sus servicios de aplicación esté disponible para la conectividad remota.

## <a name="properties"></a>Propiedades
 
### <a name="appserviceinfo"></a>appServiceInfo
`@property(nonatomic, readonly, strong, nonnull) MCDAppServiceInfo* appServiceInfo;`

La información descriptiva acerca de este servicio de aplicación.

## <a name="methods"></a>Métodos

### <a name="connectiondidopen"></a>connectionDidOpen
`- (void)connectionDidOpen:(nonnull MCDAppServiceConnectionOpenedInfo*)openedInfo;`

Este método se llama cuando se abre una conexión de servicio de aplicación remota para este servicio de aplicaciones.

#### <a name="parameters"></a>Parámetros 
* `openedInfo`

Una instancia de MDCAppServiceConnectionOpenedInfo que contiene información para la mensajería de remoto con el servicio de aplicación.