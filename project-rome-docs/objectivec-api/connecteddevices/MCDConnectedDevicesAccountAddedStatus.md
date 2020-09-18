---
title: MCDConnectedDevicesAccountAddedStatus
description: Obtenga información sobre la enumeración MCDConnectedDevicesAccountAddedStatus. Esta enumeración contiene valores que describen el estado de la operación de agregar cuenta.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761039"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a>enumeración `MCDConnectedDevicesAccountAddedStatus`

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
Contiene los valores que describen el estado de la operación de agregar cuenta.

## <a name="fields"></a>Campos

| NOMBRE                              |   Valor     | Descripción |
|:----------------------------------|:------|:-------------------------------|
| MCDConnectedDevicesAccountAddedStatusSuccess | 0 | La cuenta se ha agregado correctamente a la plataforma. |
| MCDConnectedDevicesAccountAddedStatusErrorNoNetwork | 1 | No se pudo realizar la operación de cuenta porque Roma no detectó acceso a la red. |
| MCDConnectedDevicesAccountAddedStatusErrorServiceFailed | 2 | No se pudo realizar la operación de cuenta porque Roma no pudo ponerse en contacto con los servicios Web. |
| MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber | 3 | No se pudo realizar la operación de cuenta porque la aplicación no se suscribió al evento AccessTokenRequested. |
| MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed | 4 | No se pudo realizar la operación de cuenta porque la aplicación no pudo devolver un token cuando se solicitó. |
| MCDConnectedDevicesAccountAddedStatusErrorUnknown | 5 | No se pudo realizar la operación de cuenta por motivos desconocidos. |
