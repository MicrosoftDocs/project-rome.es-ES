---
title: MCDRemoteSystemLocalVisibilityKind
description: Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801107"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a>Enum `MCDRemoteSystemLocalVisibilityKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.

## <a name="fields"></a>Campos

| Name                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemLocalVisibilityKindShowAll | 0 | Mostrar todas las aplicaciones reconocibles, incluida la aplicación que realiza la llamada.
| MCDRemoteSystemLocalVisibilityKindHideLocalApp | 1 | Ocultar la aplicación que realiza la llamada.