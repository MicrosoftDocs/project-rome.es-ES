---
title: MCDAppServiceClosedEventArgs
description: Devuelve MCDAppServiceConnection.serviceClosed para informar a la que se ha cerrado el MCDAppServiceConnection y proporcionar un motivo del evento de cierre.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: a115ea4cc753efac445a466dbdfbfb14bf184370
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909187"
---
# <a name="class-mcdappserviceclosedeventargs"></a>Clase `MCDAppServiceClosedEventArgs` 

```
@interface MCDAppServiceClosedEventArgs : NSObject
```  

Devuelve MCDAppServiceConnection.serviceClosed para informar a la que se ha cerrado el MCDAppServiceConnection y proporcionar un motivo del evento de cierre.

## <a name="properties"></a>Propiedades

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDAppServiceClosedStatus status;`

El estado de cómo se cerró el servicio de aplicación.