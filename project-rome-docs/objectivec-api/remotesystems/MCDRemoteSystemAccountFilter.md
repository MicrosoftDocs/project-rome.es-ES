---
title: MCDRemoteSystemAccountFilter
description: Filtro para las cuentas descubrir los sistemas remotos con.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801557"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="a6e21-104">Clase `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="a6e21-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="a6e21-105">Filtro para las cuentas descubrir los sistemas remotos con.</span><span class="sxs-lookup"><span data-stu-id="a6e21-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="a6e21-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="a6e21-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="a6e21-107">cuenta</span><span class="sxs-lookup"><span data-stu-id="a6e21-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="a6e21-108">La cuenta asociada con este MCDRemoteSystemAccountFilter.</span><span class="sxs-lookup"><span data-stu-id="a6e21-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="a6e21-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="a6e21-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="a6e21-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="a6e21-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="a6e21-111">Inicializar la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="a6e21-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a6e21-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a6e21-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="a6e21-113">La cuenta MCDConnectedDevicesAccount utilizada.</span><span class="sxs-lookup"><span data-stu-id="a6e21-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="a6e21-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a6e21-114">Returns</span></span>
<span data-ttu-id="a6e21-115">Devuelve un objeto MCDRemoteSystemAccountFilter filtrado con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="a6e21-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="a6e21-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="a6e21-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="a6e21-117">Inicializar la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="a6e21-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="a6e21-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="a6e21-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="a6e21-119">La cuenta MCDConnectedDevicesAccount utilizada.</span><span class="sxs-lookup"><span data-stu-id="a6e21-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="a6e21-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="a6e21-120">Returns</span></span>
<span data-ttu-id="a6e21-121">Devuelve un objeto MCDRemoteSystemAccountFilter inicializa filtradas con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="a6e21-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>