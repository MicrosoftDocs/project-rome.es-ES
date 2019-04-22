---
title: MCDAppServiceConnectionStatus
description: Contiene valores que describen el estado de una conexión a un servicio de aplicación remota.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5beba7ae30d8ffd9149c5e8a599eacc38213b6d2
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801457"
---
# <a name="enum-mcdappserviceconnectionstatus"></a>Enum `MCDAppServiceConnectionStatus`

```
typedef NS_ENUM(NSInteger, MCDAppServiceConnectionStatus)
```

Contiene valores que describen el estado de una conexión a un servicio de aplicación remota. Consulte [crear y consumir un servicio de aplicación](https://docs.microsoft.com/windows/uwp/launch-resume/how-to-create-and-consume-an-app-service) para obtener información sobre los servicios de aplicaciones en dispositivos de Windows.

|Nombre   |Valor   |Descripción   |
|--------|-------|-------------|
|MCDAppServiceConnectionStatusSuccess | 0| La conexión con el servicio de aplicación se abrió correctamente.|
|MCDAppServiceConnectionStatusAppNotInstalled | 1| El paquete para el servicio de aplicación a la que se intentó realizar una conexión no está instalado en el dispositivo. Compruebe que el paquete está instalado antes de intentar abrir una conexión con el servicio de aplicación.|
|MCDAppServiceConnectionStatusAppUnavailable | 2| El paquete para el servicio de aplicación a la que se intentó realizar una conexión no está disponible temporalmente. Intente conectarse de nuevo más tarde.|
|MCDAppServiceConnectionStatusAppServiceUnavailable | 3| La aplicación con el identificador del paquete especificado está instalado y disponible, pero la aplicación no declara compatibilidad para el servicio de aplicación especificado. Compruebe que el nombre del servicio en la aplicación y la versión de la aplicación son correctos.|
|MCDAppServiceConnectionStatusUnknown | 4| No se pudo establecer la conexión por un motivo desconocido.|
|MCDAppServiceConnectionStatusRemoteSystemUnavailable | 5| El dispositivo remoto de destino o la aplicación ya no está disponible para la conexión.|
|MCDAppServiceConnectionStatusRemoteSystemNotSupportedByApp | 6|La aplicación cliente no está configurada para admitir la conectividad remota.|
|MCDAppServiceConnectionStatusNotAuthorized | 7| El dispositivo cliente no está autorizado para admitir la conectividad remota. Esto puede ocurrir porque el MCDAppServiceConnection se pasó un token no válido.|