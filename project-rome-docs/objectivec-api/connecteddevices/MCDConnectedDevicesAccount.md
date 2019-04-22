---
title: MCDConnectedDevicesAccount
description: Esta clase representa una única cuenta de usuario conocida por una aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59800937"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="bc920-104">Clase `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="bc920-104">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="bc920-105">Esta clase representa una única cuenta de usuario conocida por una aplicación.</span><span class="sxs-lookup"><span data-stu-id="bc920-105">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="bc920-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="bc920-106">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="bc920-107">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="bc920-107">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="bc920-108">La instancia de singleton de la cuenta anónima.</span><span class="sxs-lookup"><span data-stu-id="bc920-108">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="bc920-109">accountId</span><span class="sxs-lookup"><span data-stu-id="bc920-109">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="bc920-110">El identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="bc920-110">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="bc920-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="bc920-111">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="bc920-112">Un valor MCDConnectedDevicesAccountType que describe el tipo de cuenta.</span><span class="sxs-lookup"><span data-stu-id="bc920-112">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="bc920-113">Constructores</span><span class="sxs-lookup"><span data-stu-id="bc920-113">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="bc920-114">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="bc920-114">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="bc920-115">Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="bc920-115">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="bc920-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc920-116">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="bc920-117">Una cadena de identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="bc920-117">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="bc920-118">El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).</span><span class="sxs-lookup"><span data-stu-id="bc920-118">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="bc920-119">Devuelve</span><span class="sxs-lookup"><span data-stu-id="bc920-119">Returns</span></span>
<span data-ttu-id="bc920-120">Devuelve un objeto MCDConnectedDevicesAccount con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="bc920-120">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="bc920-121">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="bc920-121">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="bc920-122">Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="bc920-122">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="bc920-123">Parámetros</span><span class="sxs-lookup"><span data-stu-id="bc920-123">Parameters</span></span> 
* `type`

<span data-ttu-id="bc920-124">El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).</span><span class="sxs-lookup"><span data-stu-id="bc920-124">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="bc920-125">Devuelve</span><span class="sxs-lookup"><span data-stu-id="bc920-125">Returns</span></span>
<span data-ttu-id="bc920-126">Devuelve un objeto MCDConnectedDevicesAccount inicializado con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="bc920-126">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>