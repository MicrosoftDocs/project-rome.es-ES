---
title: MCDRemoteLaunchUriStatus
description: Contiene valores que describen el estado de un inicio de la aplicación remota mediante un identificador URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 1a0302cd570b8cb25476a8188e3bcb1667707461
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907147"
---
# <a name="enum-mcdremotelaunchuristatus"></a>Enum `MCDRemoteLaunchUriStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteLaunchUriStatus)`

Contiene valores que describen el estado de un inicio de la aplicación remota mediante un identificador URI.


| Nombre    |Valor   |Descripción   |                  
|------ |------- |--|
|MCDRemoteLaunchUriStatusUnknown | 0| El estado es desconocido.|
|MCDRemoteLaunchUriStatusSuccess | 1| El inicio remoto fue correcto.|
|MCDRemoteLaunchUriStatusAppUnavailable | 2 | La aplicación de destino no está disponible.|
|MCDRemoteLaunchUriStatusProtocolUnavailable | 3 | La aplicación de destino no es compatible con este identificador URI.|
|MCDRemoteLaunchUriStatusRemoteSystemUnavailable | 4 | El dispositivo al que se envió el mensaje no está disponible.|
|MCDRemoteLaunchUriStatusValueSetTooLarge | 5 | El paquete de datos que se envían a la aplicación de destino era demasiado grande.|
|MCDRemoteLaunchUriStatusDeniedByLocalSystem | 6 | El sistema cliente ha impedido que el uso de la plataforma de sistemas remotos.|
|MCDRemoteLaunchUriStatusDeniedByRemoteSystem | 7 | El dispositivo de destino ha impedido que el uso de la plataforma de sistemas remotos.|