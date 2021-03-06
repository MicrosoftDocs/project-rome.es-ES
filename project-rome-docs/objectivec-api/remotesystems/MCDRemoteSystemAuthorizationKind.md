---
title: MCDRemoteSystemAuthorizationKind
description: Contiene valores que describen los posibles tipos de autorización (ámbitos de autorización basada en la cuenta de usuario) para la detección de sistema remoto.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 4f54d187282e946dd2912d1d72eacc02c7ee4077
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801327"
---
# <a name="enum-mcdremotesystemauthorizationkind"></a>Enum `MCDRemoteSystemAuthorizationKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemAuthorizationKind)
```  

Contiene valores que describen los posibles tipos de autorización (ámbitos de autorización basada en la cuenta de usuario) para la detección de sistema remoto. 

## <a name="fields"></a>Campos

| Nombre                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemAuthorizationKindSameUser   | 0     | El sistema sólo puede detectar y conectarse a dispositivos que inició sesión con la misma cuenta de usuario.   |
| MCDRemoteSystemAuthorizationKindAnonymous | 1     | El sistema puede descubrir y conectarse a dispositivos de otros usuarios, siempre que se encuentran en la proximidad y permiten la detección anónimo.  |

