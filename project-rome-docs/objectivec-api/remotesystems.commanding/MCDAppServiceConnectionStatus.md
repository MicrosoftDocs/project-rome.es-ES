---
title: MCDAppServiceConnectionStatus
description: Contiene valores que describen el estado de una conexión a un servicio de aplicaciones remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: cf272326ce5c88f7c847a2a03eafe5b8bbbaa56e
ms.sourcegitcommit: 79c254e48c00d7a050864b90ddb2b727f67b0e8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/27/2021
ms.locfileid: "98901643"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>enumeración `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

Contiene valores que describen el estado de una conexión a un servicio de aplicaciones remoto. Consulte [creación y uso de un servicio de aplicaciones](/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener información sobre App Services en dispositivos Windows.

|Name   |Value   |Descripción   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| La conexión a App Service se abrió correctamente.|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| El paquete para el servicio de aplicaciones en el que se intentó una conexión no está instalado en el dispositivo. Compruebe que el paquete está instalado antes de intentar abrir una conexión a App Service.|
|MCDAppServiceConnectionStatusAppUnavailable | 2| El paquete para el servicio de aplicaciones en el que se intentó una conexión no está disponible temporalmente. Intente conectarse de nuevo más tarde.|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| La aplicación con el identificador de paquete especificado está instalada y disponible, pero la aplicación no declara la compatibilidad con el servicio de aplicaciones especificado. Compruebe que el nombre de App Service y la versión de la aplicación son correctos.|
|MCDAppServiceConnectionStatusUnknown | 4| No se pudo establecer la conexión por un motivo desconocido.|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| La aplicación o el dispositivo remoto de destino ya no está disponible para la conexión.|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|La aplicación cliente no está configurada para admitir la conectividad remota.|
|MCDAppServiceConnectionStatusNotAuthorized | 7| El dispositivo cliente no está autorizado para admitir la conectividad remota. Esto puede deberse a que se ha pasado un token no válido a MCDAppServiceConnection.|