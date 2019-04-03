---
title: MCDConnectedDevicesAccessTokenRequest
description: Solicitud de un token de acceso para el MCDConnectedDevicesAccount independiente que satisface los ámbitos contenidos.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: b1cd9b747e98d5e9ccf4885b33897e8c240d7673
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907617"
---
# <a name="class-mcdconnecteddevicesaccesstokenrequest"></a><span data-ttu-id="570a7-104">Clase `MCDConnectedDevicesAccessTokenRequest`</span><span class="sxs-lookup"><span data-stu-id="570a7-104">class `MCDConnectedDevicesAccessTokenRequest`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenRequest : NSObject
```  
<span data-ttu-id="570a7-105">Solicitud de un token de acceso para el MCDConnectedDevicesAccount independiente que satisface los ámbitos contenidos.</span><span class="sxs-lookup"><span data-stu-id="570a7-105">Request for an access token for the contained MCDConnectedDevicesAccount which satisfies the contained scopes.</span></span>

## <a name="properties"></a><span data-ttu-id="570a7-106">Propiedades</span><span class="sxs-lookup"><span data-stu-id="570a7-106">Properties</span></span>

### <a name="account"></a><span data-ttu-id="570a7-107">cuenta</span><span class="sxs-lookup"><span data-stu-id="570a7-107">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="570a7-108">La cuenta asociada con este MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="570a7-108">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="570a7-109">Ámbitos</span><span class="sxs-lookup"><span data-stu-id="570a7-109">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="570a7-110">La lista de ámbitos para los que debe cubrir el token cuando genera.</span><span class="sxs-lookup"><span data-stu-id="570a7-110">The list of scopes for which the token must cover when generated.</span></span>

## <a name="methods"></a><span data-ttu-id="570a7-111">Métodos</span><span class="sxs-lookup"><span data-stu-id="570a7-111">Methods</span></span>

### <a name="completewithaccesstoken"></a><span data-ttu-id="570a7-112">completeWithAccessToken</span><span class="sxs-lookup"><span data-stu-id="570a7-112">completeWithAccessToken</span></span>
`- (void) completeWithAccessToken:(NSString* _Nonnull) token;`

<span data-ttu-id="570a7-113">Si un token con los ámbitos solicitados se generó correctamente, llame a este método con el token para completar la solicitud.</span><span class="sxs-lookup"><span data-stu-id="570a7-113">If a token with the requested scopes was successfully generated, call this method with the token to complete the request.</span></span>

#### <a name="parameters"></a><span data-ttu-id="570a7-114">Parámetros</span><span class="sxs-lookup"><span data-stu-id="570a7-114">Parameters</span></span> 
* `token` 

<span data-ttu-id="570a7-115">Token generado correctamente</span><span class="sxs-lookup"><span data-stu-id="570a7-115">Successfully generated token</span></span>

### <a name="completewitherrormessage"></a><span data-ttu-id="570a7-116">completeWithErrorMessage</span><span class="sxs-lookup"><span data-stu-id="570a7-116">completeWithErrorMessage</span></span>
`- (void) completeWithErrorMessage:(NSString* _Nullable) errorMessage;`

<span data-ttu-id="570a7-117">Si un token con los ámbitos solicitados no se generó correctamente por cualquier motivo, llame a este método con un mensaje que se usará para el registro.</span><span class="sxs-lookup"><span data-stu-id="570a7-117">If a token with the requested scopes was not successfully generated for any reason, call this method with a message to be used for logging.</span></span>

#### <a name="parameters"></a><span data-ttu-id="570a7-118">Parámetros</span><span class="sxs-lookup"><span data-stu-id="570a7-118">Parameters</span></span> 
* `errorMessage`

<span data-ttu-id="570a7-119">Un mensaje que describe por qué el token no tuvo éxito.</span><span class="sxs-lookup"><span data-stu-id="570a7-119">A message describing why the token was unsuccessful.</span></span>