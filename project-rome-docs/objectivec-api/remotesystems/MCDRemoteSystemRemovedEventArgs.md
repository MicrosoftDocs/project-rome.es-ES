---
title: MCDRemoteSystemRemovedEventArgs
description: Argumentos de evento para el evento RemoteSystemWatcher RemoteSystemRemoved.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 652107473e7b716493483057b090f558d82425a2
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907047"
---
# <a name="class-mcdremotesystemremovedeventargs"></a>Clase `MCDRemoteSystemRemovedEventArgs` 

```
@interface MCDRemoteSystemRemovedEventArgs : NSObject
```  

Argumentos de evento para el evento MCDRemoteSystemWatcher.remoteSystemRemoved.

## <a name="properties"></a>Propiedades

### <a name="remotesystem"></a>remoteSystem
`@property(nonatomic, readonly, nonnull) MCDRemoteSystem* remoteSystem;`

El sistema remoto MCDRemoteSystem que se ha quitado. Este sistema remoto no debe utilizarse después de este evento.