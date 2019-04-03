---
title: MCDConnectedDevicesAccountAddedStatus
description: Contiene los valores que describen el estado de operación de agregar la cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907207"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>Enum `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
Contiene los valores que describen el estado de operación de agregar la cuenta.

## <a name="fields"></a>Campos

| Nombre                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | La cuenta se agregó correctamente a la plataforma. |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | Error en la operación de cuenta desde que Roma no detectó ningún acceso a la red. |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | Error en la operación de cuenta como Roma no pudo ponerse en contacto con los servicios web. |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | Error en la operación de cuenta dado que la aplicación no suscribirse al evento AccessTokenRequested. |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | Error en la operación de cuenta dado que la aplicación no pudo devolver un token cuando se solicita. |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | Error en la operación de cuenta por razones desconocidas. |
