---
title: MCDRemoteSystemLocalVisibilityKind
description: Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 0596b7fa3381a06e6f0cf63b86f9382214564ee8
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58908867"
---
# <a name="enum-mcdremotesystemlocalvisibilitykind"></a>Enum `MCDRemoteSystemLocalVisibilityKind` 

```
typedef NS_ENUM(NSInteger, MCDRemoteSystemLocalVisibilityKind)
```  
Contiene valores que describen la preferencia de visibilidad de la aplicación local durante la detección de sistemas remotos.

## <a name="fields"></a>Campos

| Nombre                              | Valor | Descripción                    |
|:----------------------------------|:------|:-------------------------------|
| MCDRemoteSystemLocalVisibilityKindShowAll | 0 | Mostrar todas las aplicaciones reconocibles, incluida la aplicación que realiza la llamada.
| MCDRemoteSystemLocalVisibilityKindHideLocalApp | 1 | Ocultar la aplicación que realiza la llamada.