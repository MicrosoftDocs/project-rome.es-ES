---
title: MCDStatelessAppServiceResponseStatus
description: Contiene valores que describen el estado de un mensaje enviado desde un app service a otro (si se ha entregado correctamente los datos del mensaje).
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 9d01e892861c8551b7b3e41d1b227f65f07d752a
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907877"
---
# <a name="enum-mcdstatelessappserviceresponsestatus"></a>Enum `MCDStatelessAppServiceResponseStatus`

`typedef NS_ENUM(NSInteger, MCDStatelessAppServiceResponseStatus)`

 Contiene valores que describen el estado de un mensaje enviado desde un app service a otro (si se ha entregado correctamente los datos del mensaje).


| Nombre    |Valor   |Descripción   |                  
|------ |------- |--|
|MCDStatelessAppServiceResponseStatusSuccess | 0| El mensaje se entregó correctamente. |
|MCDStatelessAppServiceResponseStatusAppNotInstalled | 1| El paquete para el servicio de aplicación a la que se intentó realizar una conexión no está instalado en el dispositivo. Compruebe que el paquete está instalado antes de intentar abrir una conexión al servicio de theap p. |
|MCDStatelessAppServiceResponseStatusAppUnavailable | 2 | El paquete para el servicio de aplicación a la que se intentó realizar una conexión no está disponible temporalmente. Intente conectarse de nuevo más tarde. |
|MCDStatelessAppServiceResponseStatusAppServiceUnavailable | 3 | La aplicación con el identificador del paquete especificado está instalado y disponible, pero la aplicación no declara compatibilidad para el servicio de aplicación especificado. Compruebe que el nombre del servicio en la aplicación y la versión de la aplicación son correctos. |
|MCDStatelessAppServiceResponseStatusRemoteSystemUnavailable | 4 | No se entregó el mensaje porque no se pudo establecer una conexión al dispositivo remoto.|
|MCDStatelessAppServiceResponseStatusRemoteSystemNotSupportedByApp | 5 | La aplicación remota no está configurada para admitir la conectividad remota. |
|MCDStatelessAppServiceResponseStatusNotAuthorized | 6 | El servicio de aplicación no está autorizado para comunicarse con el dispositivo remoto. |
|MCDStatelessAppServiceResponseStatusResourceLimitsExceeded | 7 | No se entregó el mensaje porque se superan los límites de memoria de programa del servicio en la aplicación remota.|
|MCDStatelessAppServiceResponseStatusMessageSizeTooLarge | 8 | No se entregó el mensaje porque se superó el tamaño permitido. |
|MCDStatelessAppServiceResponseStatusFailure | 9 | No se entregó el mensaje debido a un error de red. |
|MCDStatelessAppServiceResponseStatusUnknown | 10 |El mensaje no se entregó por un motivo desconocido. |