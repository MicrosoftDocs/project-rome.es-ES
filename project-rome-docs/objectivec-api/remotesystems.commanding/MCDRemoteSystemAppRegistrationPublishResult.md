---
title: MCDRemoteSystemAppRegistrationPublishResult
description: Una clase comunica el resultado asincrónico de publicar información de la aplicación de sistema remoto para una cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 5e28e2533d14839384bcd2cfac2db3fc368a6207
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909927"
---
# <a name="class-mcdremotesystemappregistrationpublishresult"></a>Clase `MCDRemoteSystemAppRegistrationPublishResult` 

```
@interface MCDRemoteSystemAppRegistrationPublishResult : NSObject
```  

Esta clase comunica el resultado asincrónico de publicar información de la aplicación de sistema remoto para una cuenta. Los Estados de error que se comunica a través de este resultado se deben usar la aplicación para volver a intentar la publicación en el caso de ciertas condiciones transitorias como la red que no está disponible.

## <a name="properties"></a>Propiedades

### <a name="status"></a>status
`@property(nonatomic, readonly) MCDRemoteSystemAppRegistrationPublishStatus status;`

Enumeración de estado de la operación de publicación.