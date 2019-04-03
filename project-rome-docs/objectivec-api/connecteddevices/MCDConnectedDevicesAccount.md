---
title: MCDConnectedDevicesAccount
description: Esta clase representa una única cuenta de usuario conocida por una aplicación.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: e9b43bb76e46f3a027247b1d4d564c6e1571bae4
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909157"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="4b1e7-104">Clase `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="4b1e7-104">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="4b1e7-105">Esta clase representa una única cuenta de usuario conocida por una aplicación.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-105">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="4b1e7-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="4b1e7-106">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="4b1e7-107">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="4b1e7-107">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="4b1e7-108">La instancia de singleton de la cuenta anónima.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-108">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="4b1e7-109">accountId</span><span class="sxs-lookup"><span data-stu-id="4b1e7-109">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="4b1e7-110">El identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-110">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="4b1e7-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="4b1e7-111">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="4b1e7-112">Un valor MCDConnectedDevicesAccountType que describe el tipo de cuenta.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-112">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="4b1e7-113">Constructores</span><span class="sxs-lookup"><span data-stu-id="4b1e7-113">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="4b1e7-114">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="4b1e7-114">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="4b1e7-115">Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-115">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4b1e7-116">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4b1e7-116">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="4b1e7-117">Una cadena de identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-117">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="4b1e7-118">El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).</span><span class="sxs-lookup"><span data-stu-id="4b1e7-118">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="4b1e7-119">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4b1e7-119">Returns</span></span>
<span data-ttu-id="4b1e7-120">Devuelve un objeto MCDConnectedDevicesAccount con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-120">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="4b1e7-121">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="4b1e7-121">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="4b1e7-122">Una nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-122">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="4b1e7-123">Parámetros</span><span class="sxs-lookup"><span data-stu-id="4b1e7-123">Parameters</span></span> 
* `type`

<span data-ttu-id="4b1e7-124">El MCDConnectedDevicesAccountType de la cuenta (depende de qué proveedor de Id. la cuenta procede).</span><span class="sxs-lookup"><span data-stu-id="4b1e7-124">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="4b1e7-125">Devuelve</span><span class="sxs-lookup"><span data-stu-id="4b1e7-125">Returns</span></span>
<span data-ttu-id="4b1e7-126">Devuelve un objeto MCDConnectedDevicesAccount inicializado con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="4b1e7-126">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>