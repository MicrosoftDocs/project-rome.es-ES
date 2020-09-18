---
title: MCDRemoteSystemStatus
description: Obtenga información sobre la enumeración MCDRemoteSystemStatus. Esta enumeración contiene valores que describen la disponibilidad de un sistema remoto.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 71e4216c949506f45f26a7c035ff043a55168b23
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760659"
---
# <a name="enum-mcdremotesystemstatus"></a>enumeración `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
Contiene valores que describen la disponibilidad de un sistema remoto. En las aplicaciones iOS, siempre se encontrará un valor de **MCDRemoteSystemStatusUnknown** . otros valores solo están disponibles en los sistemas Windows.

## <a name="fields"></a>Campos

| NOMBRE                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | El sistema remoto se muestra como no disponible. |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | Se está determinando el estado del sistema remoto (se produce durante el proceso de detección). |
| MCDRemoteSystemStatusAvailable | 2 | El sistema remoto se muestra como disponible. |
| MCDRemoteSystemStatusUnknown | 3 | El estado es desconocido. |
