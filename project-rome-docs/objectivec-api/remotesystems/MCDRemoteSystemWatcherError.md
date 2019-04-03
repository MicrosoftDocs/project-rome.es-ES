---
title: MCDRemoteSystemWatcherError
description: Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 3f65614396377b154b2a37493b8271ac54afb6fd
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907707"
---
# <a name="enum-mcdremotesystemwatchererror"></a>Enum `MCDRemoteSystemWatcherError` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemWatcherError)
```  
 Contiene valores que la describe un error encontrado por un objeto de Monitor de sistema remoto durante el proceso de detección.

## <a name="fields"></a>Campos

| Nombre                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemWatcherErrorUnknown | 0 | El monitor encontró un error desconocido. |
| MCDRemoteSystemWatcherErrorInternetNotAvailable | 1 | Se produjo el error porque se ha perdido la conexión a Internet. |
| MCDRemoteSystemWatcherErrorAuthenticationError | 2 | Se produjo el error porque no se pudo autenticar un ConnectedDevicesAccount que se usa para ejecutar la detección. | 
