---
title: MCDRemoteSystemAppRegistrationPublishStatus
description: Contiene valores que describen el estado de un inicio de la aplicación remota mediante un identificador URI.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 32c3e473938925f12838bf6dc5ccc3e98a3394a6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907547"
---
# <a name="enum-mcdremotesystemappregistrationpublishstatus"></a>Enum `MCDRemoteSystemAppRegistrationPublishStatus`

`typedef NS_ENUM(NSInteger, MCDRemoteSystemAppRegistrationPublishStatus)`

Enumeración que indica el estado de la operación de publicación.
Los Estados de error indican condiciones transitorias, donde el desarrollador puede querer vuelva a intentar publicarla.

| Nombre    |Valor   |Descripción   |                  
|------ |------- |--|
|MCDRemoteSystemAppRegistrationPublishStatusSuccess | 0 | Operación se completó correctamente.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoNetwork | 1 | Red no estaba disponible. |
|MCDRemoteSystemAppRegistrationPublishStatusErrorWebFailure | 2 | Error en un servicio web.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorNoTokenRequestSubscriber | 3 | No hay ningún suscriptor de la solicitud de token respondió.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorTokenRequestFailed | 4 | Error en la solicitud de token.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorAccountNotFound | 5 | No se encontró la cuenta para publicar información de.|
|MCDRemoteSystemAppRegistrationPublishStatusErrorUnknown | 6 | Operación encontró un error desconocido.|