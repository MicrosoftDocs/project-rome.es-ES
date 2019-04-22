---
title: MCDConnectedDevicesAccountManager
description: Proporciona un punto de entrada único para todas las características relacionadas con la cuenta en el SDK.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c265a0c7114704ea6f9ae9818eb9abdb39b5437f
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801647"
---
# <a name="class-mcdconnecteddevicesaccountmanager"></a><span data-ttu-id="1bb67-104">Clase `MCDConnectedDevicesAccountManager`</span><span class="sxs-lookup"><span data-stu-id="1bb67-104">class `MCDConnectedDevicesAccountManager`</span></span> 

```
@interface MCDConnectedDevicesAccountManager : NSObject
```  
<span data-ttu-id="1bb67-105">Proporciona un punto de entrada único para todas las características relacionadas con la cuenta en el SDK.</span><span class="sxs-lookup"><span data-stu-id="1bb67-105">Provides a single entrypoint for all account-related features in the SDK.</span></span>

## <a name="properties"></a><span data-ttu-id="1bb67-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="1bb67-106">Properties</span></span>

### <a name="accesstokenrequested"></a><span data-ttu-id="1bb67-107">accessTokenRequested</span><span class="sxs-lookup"><span data-stu-id="1bb67-107">accessTokenRequested</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenRequestedEventArgs*>* accessTokenRequested;`

<span data-ttu-id="1bb67-108">Este evento se desencadena cuando hay una necesidad de solicitar un token.</span><span class="sxs-lookup"><span data-stu-id="1bb67-108">This event is fired when there is a need to request a token.</span></span> <span data-ttu-id="1bb67-109">Este evento debe ser suscrito y listo para responder antes de que se envía ninguna solicitud.</span><span class="sxs-lookup"><span data-stu-id="1bb67-109">This event should be subscribed and ready to respond before any request is sent out.</span></span>

### <a name="accesstokeninvalidated"></a><span data-ttu-id="1bb67-110">accessTokenInvalidated</span><span class="sxs-lookup"><span data-stu-id="1bb67-110">accessTokenInvalidated</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesAccountManager*, MCDConnectedDevicesAccessTokenInvalidatedEventArgs*>* accessTokenInvalidated;`

<span data-ttu-id="1bb67-111">Este evento se desencadena cuando un consumidor de token notifica un error de token.</span><span class="sxs-lookup"><span data-stu-id="1bb67-111">This event is fired when a token consumer reports a token error.</span></span> <span data-ttu-id="1bb67-112">El proveedor de tokens se necesita para actualizar su caché de tokens o solicitar un nuevo inicio de sesión de usuario para corregir su configuración de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="1bb67-112">The token provider needs to either refresh their token cache or request a new user login to fix their account setup.</span></span>

### <a name="allaccounts"></a><span data-ttu-id="1bb67-113">allAccounts</span><span class="sxs-lookup"><span data-stu-id="1bb67-113">allAccounts</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<MCDConnectedDevicesAccount*>* allAccounts;`

<span data-ttu-id="1bb67-114">MCDConnectedDevicesAccount todos los que se realiza un seguimiento actualmente por este administrador.</span><span class="sxs-lookup"><span data-stu-id="1bb67-114">All MCDConnectedDevicesAccount which are currently tracked by this manager.</span></span>

## <a name="methods"></a><span data-ttu-id="1bb67-115">Métodos</span><span class="sxs-lookup"><span data-stu-id="1bb67-115">Methods</span></span>

### <a name="addaccountasync"></a><span data-ttu-id="1bb67-116">addAccountAsync</span><span class="sxs-lookup"><span data-stu-id="1bb67-116">addAccountAsync</span></span>
`- (void) addAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesAddAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="1bb67-117">Agregar un administrador de cuenta para cuentas, se invocará la devolución de llamada cuando se complete.</span><span class="sxs-lookup"><span data-stu-id="1bb67-117">Add an account to account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1bb67-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1bb67-118">Parameters</span></span> 
* `callback`

<span data-ttu-id="1bb67-119">El resultado de la devolución de llamada indica si la suma de la cuenta es correcta o no.</span><span class="sxs-lookup"><span data-stu-id="1bb67-119">The callback result indicates if Account addition is successful or not.</span></span> 

### <a name="removeaccountasync"></a><span data-ttu-id="1bb67-120">removeAccountAsync</span><span class="sxs-lookup"><span data-stu-id="1bb67-120">removeAccountAsync</span></span>
`- (void) removeAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account callback:(nonnull void (^)(MCDConnectedDevicesRemoveAccountResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="1bb67-121">Quitar una cuenta de administrador de cuentas, se invocará la devolución de llamada cuando se complete.</span><span class="sxs-lookup"><span data-stu-id="1bb67-121">Remove an account from account manager, callback will be invoked when it completes.</span></span>

#### <a name="parameters"></a><span data-ttu-id="1bb67-122">Parámetros</span><span class="sxs-lookup"><span data-stu-id="1bb67-122">Parameters</span></span> 
* `callback` 

 <span data-ttu-id="1bb67-123">El resultado de la devolución de llamada indica si la eliminación de la cuenta es correcta o no.</span><span class="sxs-lookup"><span data-stu-id="1bb67-123">The callback result indicates if Account removal is successful or not.</span></span> 