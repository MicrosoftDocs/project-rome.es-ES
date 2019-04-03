---
title: MCDAppServiceConnectionOpenedInfo
description: Esta clase proporciona datos para el evento MCDAppServiceProvider.connectionDidOpen, que se produce cuando un dispositivo remoto abre una conexión a un servicio de aplicación local.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b700c95d7ab093b47a94c856c25b946fc5df12d7
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907557"
---
# <a name="class-mcdappserviceconnectionopenedinfo"></a>Clase `MCDAppServiceConnectionOpenedInfo` 

```
@interface MCDAppServiceConnectionOpenedInfo : NSObject
```  

Esta clase proporciona datos para el evento MCDAppServiceProvider.connectionDidOpen, que se produce cuando un dispositivo remoto abre una conexión a un servicio de aplicación local.

## <a name="properties"></a>Propiedades

### <a name="appserviceconnection"></a>appServiceConnection
`@property(nonatomic, readonly, nonnull) MCDAppServiceConnection* appServiceConnection;`

Una instancia de MCDAppServiceConnection que representa la conexión entre el servicio de aplicación local y el dispositivo remoto.

### <a name="remotesystemapp"></a>remoteSystemApp
`@property(nonatomic, readonly, nullable) MCDRemoteSystemApp* remoteSystemApp;`

La aplicación remota MCDRemoteSystemApp que inician una conexión con el servicio de aplicación local.