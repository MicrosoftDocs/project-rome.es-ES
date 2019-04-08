---
title: MCDUserDataFeedSyncScopeFlags
description: Esta clase
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c2edbe5c45472807217c005086dfa1d9728d40b6
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907667"
---
# <a name="class-mcduserdatafeedsyncscopeflags"></a><span data-ttu-id="0c367-104">Clase `MCDUserDataFeedSyncScopeFlags`</span><span class="sxs-lookup"><span data-stu-id="0c367-104">class `MCDUserDataFeedSyncScopeFlags`</span></span>

```
@interface MCDUserDataFeedSyncScopeFlags : NSObject
```

<span data-ttu-id="0c367-105">Esta clase proporciona marcas válidas opcionales para MCDUserDataFeedSyncScope.syncScopeFlags.</span><span class="sxs-lookup"><span data-stu-id="0c367-105">This class provides optional valid flags for MCDUserDataFeedSyncScope.syncScopeFlags.</span></span>

## <a name="properties"></a><span data-ttu-id="0c367-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="0c367-106">Properties</span></span>

### <a name="excludeautogenerated"></a><span data-ttu-id="0c367-107">excludeAutoGenerated</span><span class="sxs-lookup"><span data-stu-id="0c367-107">excludeAutoGenerated</span></span>

`@property(class, nonatomic, readonly, nonnull) NSString* excludeAutoGenerated;`

<span data-ttu-id="0c367-108">Excluir las actividades que se generan automáticamente por SAM en Windows.</span><span class="sxs-lookup"><span data-stu-id="0c367-108">Exclude activities which are automatically generated by SAM on Windows.</span></span>

### <a name="includewebactionable"></a><span data-ttu-id="0c367-109">includeWebActionable</span><span class="sxs-lookup"><span data-stu-id="0c367-109">includeWebActionable</span></span>
`@property(class, nonatomic, readonly, nonnull) NSString* includeWebActionable;`

<span data-ttu-id="0c367-110">Incluya siempre las actividades que se pueden activar a través de la aplicación web.</span><span class="sxs-lookup"><span data-stu-id="0c367-110">Always include activities that can be activated via web app.</span></span>