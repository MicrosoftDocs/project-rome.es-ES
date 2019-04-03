---
title: MCDRemoteSystemStatus
description: Contiene valores que describen la disponibilidad de un sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4a69961b12def736733e1b6a78d376d57b2fa33f
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907587"
---
# <a name="enum-mcdremotesystemstatus"></a>Enum `MCDRemoteSystemStatus` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemStatus)
```  
Contiene valores que describen la disponibilidad de un sistema remoto. En las aplicaciones de iOS, un valor de **MCDRemoteSystemStatusUnknown** siempre se encuentre; otros valores solo están disponibles en sistemas Windows.

## <a name="fields"></a>Campos

| Nombre                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemStatusUnavailable | 0 | El sistema remoto se notifica como no disponible. |
| MCDRemoteSystemStatusDiscoveringAvailablilty | 1 | Se está determinando el estado del sistema remoto (que se produce durante el proceso de detección). |
| MCDRemoteSystemStatusAvailable | 2 | El sistema remoto se notifica como disponibles. |
| MCDRemoteSystemStatusUnknown | 3 | El estado es desconocido. |
