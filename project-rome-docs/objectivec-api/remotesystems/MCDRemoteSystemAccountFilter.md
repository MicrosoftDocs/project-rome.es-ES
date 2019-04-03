---
title: MCDRemoteSystemAccountFilter
description: Filtro para las cuentas descubrir los sistemas remotos con.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 34721c2dee89adc380b721a027382f81c2ecb751
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907327"
---
# <a name="class-mcdremotesystemaccountfilter"></a><span data-ttu-id="1189c-104">Clase `MCDRemoteSystemAccountFilter`</span><span class="sxs-lookup"><span data-stu-id="1189c-104">class `MCDRemoteSystemAccountFilter`</span></span> 

```
@interface MCDRemoteSystemAccountFilter : NSObject<MCDRemoteSystemFilter>
```  

<span data-ttu-id="1189c-105">Filtro para las cuentas descubrir los sistemas remotos con.</span><span class="sxs-lookup"><span data-stu-id="1189c-105">Filter for the accounts to discover remote systems with.</span></span>

## <a name="properties"></a><span data-ttu-id="1189c-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="1189c-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="1189c-107">cuenta</span><span class="sxs-lookup"><span data-stu-id="1189c-107">account</span></span>
`@property(nonatomic, readonly, strong, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="1189c-108">La cuenta asociada con este MCDRemoteSystemAccountFilter.</span><span class="sxs-lookup"><span data-stu-id="1189c-108">The Account associated with this MCDRemoteSystemAccountFilter.</span></span>

## <a name="constructors"></a><span data-ttu-id="1189c-109">Constructores</span><span class="sxs-lookup"><span data-stu-id="1189c-109">Constructors</span></span>

### <a name="filterwithaccount"></a><span data-ttu-id="1189c-110">filterWithAccount</span><span class="sxs-lookup"><span data-stu-id="1189c-110">filterWithAccount</span></span>
`+ (nullable instancetype)filterWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="1189c-111">Inicializar la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="1189c-111">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1189c-112">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1189c-112">Parameters</span></span> 
* `account` 

<span data-ttu-id="1189c-113">La cuenta MCDConnectedDevicesAccount utilizada.</span><span class="sxs-lookup"><span data-stu-id="1189c-113">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="1189c-114">Devuelve</span><span class="sxs-lookup"><span data-stu-id="1189c-114">Returns</span></span>
<span data-ttu-id="1189c-115">Devuelve un objeto MCDRemoteSystemAccountFilter filtrado con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="1189c-115">Returns a MCDRemoteSystemAccountFilter object filtered with the Account.</span></span>

### <a name="initwithaccount"></a><span data-ttu-id="1189c-116">initWithAccount</span><span class="sxs-lookup"><span data-stu-id="1189c-116">initWithAccount</span></span>
`- (nullable instancetype)initWithAccount:(nonnull MCDConnectedDevicesAccount*)account;`

<span data-ttu-id="1189c-117">Inicializar la clase con la cuenta MCDConnectedDevicesAccount.</span><span class="sxs-lookup"><span data-stu-id="1189c-117">Initialize the class with the MCDConnectedDevicesAccount account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1189c-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1189c-118">Parameters</span></span> 
* `account` 

<span data-ttu-id="1189c-119">La cuenta MCDConnectedDevicesAccount utilizada.</span><span class="sxs-lookup"><span data-stu-id="1189c-119">The MCDConnectedDevicesAccount account being used.</span></span>

#### <a name="returns"></a><span data-ttu-id="1189c-120">Devuelve</span><span class="sxs-lookup"><span data-stu-id="1189c-120">Returns</span></span>
<span data-ttu-id="1189c-121">Devuelve un objeto MCDRemoteSystemAccountFilter inicializa filtradas con la cuenta.</span><span class="sxs-lookup"><span data-stu-id="1189c-121">Returns an MCDRemoteSystemAccountFilter object initialized filtered with the Account.</span></span>