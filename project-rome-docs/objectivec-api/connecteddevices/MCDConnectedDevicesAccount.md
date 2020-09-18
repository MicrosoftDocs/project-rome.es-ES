---
title: MCDConnectedDevicesAccount
description: Obtenga información sobre la clase MCDConnectedDevicesAccount. Esta clase representa una cuenta de usuario única conocida por una aplicación.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: b3004681c2bcbb0ad9d5b1dcb15fe8a711773767
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761049"
---
# <a name="class-mcdconnecteddevicesaccount"></a><span data-ttu-id="6abb4-105">las `MCDConnectedDevicesAccount`</span><span class="sxs-lookup"><span data-stu-id="6abb4-105">class `MCDConnectedDevicesAccount`</span></span>

```
@interface MCDConnectedDevicesAccount : NSObject
```  

<span data-ttu-id="6abb4-106">Esta clase representa una cuenta de usuario única conocida por una aplicación.</span><span class="sxs-lookup"><span data-stu-id="6abb4-106">This class represents a single user account known by an app.</span></span>

## <a name="properties"></a><span data-ttu-id="6abb4-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="6abb4-107">Properties</span></span>

### <a name="anonymousaccount"></a><span data-ttu-id="6abb4-108">anonymousAccount</span><span class="sxs-lookup"><span data-stu-id="6abb4-108">anonymousAccount</span></span>
`+ (nullable instancetype)anonymousAccount;`

<span data-ttu-id="6abb4-109">Instancia singleton de la cuenta anónima.</span><span class="sxs-lookup"><span data-stu-id="6abb4-109">The singleton instance of the Anonymous account.</span></span>

### <a name="accountid"></a><span data-ttu-id="6abb4-110">accountId</span><span class="sxs-lookup"><span data-stu-id="6abb4-110">accountId</span></span>
`@property(nonatomic, readonly, copy, nonnull) NSString* accountId;`

<span data-ttu-id="6abb4-111">Identificador único de esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="6abb4-111">The unique identifier for this user account.</span></span>

### <a name="type"></a><span data-ttu-id="6abb4-112">type</span><span class="sxs-lookup"><span data-stu-id="6abb4-112">type</span></span>
`@property(nonatomic, readonly) MCDConnectedDevicesAccountType type;`

<span data-ttu-id="6abb4-113">Un valor de MCDConnectedDevicesAccountType que describe el tipo de cuenta.</span><span class="sxs-lookup"><span data-stu-id="6abb4-113">A MCDConnectedDevicesAccountType value describing the type of account.</span></span>

## <a name="constructors"></a><span data-ttu-id="6abb4-114">Constructores</span><span class="sxs-lookup"><span data-stu-id="6abb4-114">Constructors</span></span>

### <a name="accountwithaccountid"></a><span data-ttu-id="6abb4-115">accountWithAccountId</span><span class="sxs-lookup"><span data-stu-id="6abb4-115">accountWithAccountId</span></span>
`+ (nullable instancetype)accountWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="6abb4-116">Nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="6abb4-116">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6abb4-117">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6abb4-117">Parameters</span></span> 

* `accountId` 

<span data-ttu-id="6abb4-118">Una cadena de identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="6abb4-118">A unique identifier string for this user account.</span></span>

`type` 

<span data-ttu-id="6abb4-119">El MCDConnectedDevicesAccountType de la cuenta (depende del proveedor de IDENTIFICADOres de la cuenta).</span><span class="sxs-lookup"><span data-stu-id="6abb4-119">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="6abb4-120">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="6abb4-120">Returns</span></span>
<span data-ttu-id="6abb4-121">Devuelve un objeto MCDConnectedDevicesAccount con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="6abb4-121">Returns an MCDConnectedDevicesAccount object with the account identifier.</span></span>

### <a name="initwithaccountid"></a><span data-ttu-id="6abb4-122">initWithAccountId</span><span class="sxs-lookup"><span data-stu-id="6abb4-122">initWithAccountId</span></span>
`- (nullable instancetype)initWithAccountId:(nullable NSString*)accountId type:(MCDConnectedDevicesAccountType)type;`

<span data-ttu-id="6abb4-123">Nueva instancia de esta clase con el identificador único para esta cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="6abb4-123">A new instance of this class with the unique identifier for this user account.</span></span>

#### <a name="parameters"></a><span data-ttu-id="6abb4-124">Parámetros</span><span class="sxs-lookup"><span data-stu-id="6abb4-124">Parameters</span></span> 
* `type`

<span data-ttu-id="6abb4-125">El MCDConnectedDevicesAccountType de la cuenta (depende del proveedor de IDENTIFICADOres de la cuenta).</span><span class="sxs-lookup"><span data-stu-id="6abb4-125">The MCDConnectedDevicesAccountType of the account (depends on which ID provider the account is from).</span></span>

#### <a name="returns"></a><span data-ttu-id="6abb4-126">Devoluciones</span><span class="sxs-lookup"><span data-stu-id="6abb4-126">Returns</span></span>
<span data-ttu-id="6abb4-127">Devuelve un objeto MCDConnectedDevicesAccount inicializado con el identificador de cuenta.</span><span class="sxs-lookup"><span data-stu-id="6abb4-127">Returns an MCDConnectedDevicesAccount object initialized with the account identifier.</span></span>