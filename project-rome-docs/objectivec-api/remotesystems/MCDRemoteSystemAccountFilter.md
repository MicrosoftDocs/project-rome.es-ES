---
title: MCDRemoteSystemAccountFilter
description: Obtenga información sobre cómo filtrar cuentas para detectar sistemas remotos mediante el uso de constructores como "filterwithAccount".
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 3a32c318aba49eff550ccfdf51049fd97a34e2f5
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760729"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="f0432-104">las `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="f0432-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="f0432-105">Filtre las cuentas para detectar sistemas remotos con.</span><span class="sxs-lookup"><span data-stu-id="f0432-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="f0432-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="f0432-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="f0432-107">account</span><span class="sxs-lookup"><span data-stu-id="f0432-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="f0432-108">La cuenta asociada a este MCDRemoteSystemAccountFilter.</span><span class="sxs-lookup"><span data-stu-id="f0432-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="f0432-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="f0432-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="f0432-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="f0432-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="f0432-111">Inicialice la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="f0432-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f0432-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f0432-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="f0432-113">La cuenta MCDConnectedDevicesAccount que se está usando.</span><span class="sxs-lookup"><span data-stu-id="f0432-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="f0432-114">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="f0432-114">Returns</span></span>
<span data-ttu-id="f0432-115">Devuelve un objeto MCDRemoteSystemAccountFilter filtrado con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="f0432-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="f0432-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="f0432-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="f0432-117">Inicialice la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="f0432-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="f0432-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="f0432-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="f0432-119">La cuenta MCDConnectedDevicesAccount que se está usando.</span><span class="sxs-lookup"><span data-stu-id="f0432-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="f0432-120">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="f0432-120">Returns</span></span>
<span data-ttu-id="f0432-121">Devuelve un objeto MCDRemoteSystemAccountFilter inicializado con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="f0432-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>