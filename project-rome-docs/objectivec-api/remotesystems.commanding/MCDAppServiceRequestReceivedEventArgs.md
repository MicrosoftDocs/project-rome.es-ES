---
title: MCDAppServiceRequestReceivedEventArgs
description: Obtenga información sobre la clase MCDAppServiceRequestReceivedEventArgs. Esta clase contiene datos asociados a un evento de solicitud recibida.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 9a4a64ae163a0cc553196914da2f42d8d32e6ade
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760769"
---
# <a name="class-mcdappservicerequestreceivedeventargs"></a>las `MCDAppServiceRequestReceivedEventArgs` 

```
@interface MCDAppServiceRequestReceivedEventArgs : NSObject
```  
Contiene datos asociados a un evento de "solicitud recibida".

## <a name="properties"></a>Propiedades

### <a name="request"></a>request
`@property(nonatomic, readonly, nonnull) MCDAppServiceRequest* request;`

La solicitud enviada por el dispositivo remoto.