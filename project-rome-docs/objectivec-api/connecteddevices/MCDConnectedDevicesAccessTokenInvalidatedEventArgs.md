---
title: MCDConnectedDevicesAccessTokenInvalidatedEventArgs
description: Informar a ese token asociado ConnectedDevicesAccount informó de un error de token.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: 46a21b534e2b3a5fb588e40af2dbc4eb47143873
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801777"
---
# <a name="class-mcdconnecteddevicesaccesstokeninvalidatedeventargs"></a><span data-ttu-id="d7fd0-104">Clase `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span><span class="sxs-lookup"><span data-stu-id="d7fd0-104">class `MCDConnectedDevicesAccessTokenInvalidatedEventArgs`</span></span> 

```
@interface MCDConnectedDevicesAccessTokenInvalidatedEventArgs : NSObject 
```  
<span data-ttu-id="d7fd0-105">Devuelve MCDConnectedDevicesAccount para informar a la que el token asociado MCDConnectedDevicesAccount informó de error de token para los ámbitos contenidos.</span><span class="sxs-lookup"><span data-stu-id="d7fd0-105">Returned by MCDConnectedDevicesAccount to inform that the token associated with MCDConnectedDevicesAccount reported token error for the contained scopes.</span></span> <span data-ttu-id="d7fd0-106">Proveedor de tokens se necesita para actualizar su caché de tokens o potencialmente emergente de la interfaz de usuario para pedir al usuario iniciar sesión con el fin de corregir la configuración de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="d7fd0-106">Token provider needs to either refresh their token cache or potentially pop up UI to ask user to sign in in order to fix their account setup.</span></span>

## <a name="properties"></a><span data-ttu-id="d7fd0-107">Propiedades</span><span class="sxs-lookup"><span data-stu-id="d7fd0-107">Properties</span></span>

### <a name="account"></a><span data-ttu-id="d7fd0-108">cuenta</span><span class="sxs-lookup"><span data-stu-id="d7fd0-108">account</span></span>
`@property (nonatomic, readonly, nonnull) MCDConnectedDevicesAccount* account;`

<span data-ttu-id="d7fd0-109">La cuenta asociada con este MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="d7fd0-109">The Account associated with this MCDConnectedDevicesAccessTokenInvalidatedEventArgs.</span></span>

### <a name="scopes"></a><span data-ttu-id="d7fd0-110">Ámbitos</span><span class="sxs-lookup"><span data-stu-id="d7fd0-110">scopes</span></span>
`@property (nonatomic, readonly, nonnull) NSArray<NSString*>* scopes;`

<span data-ttu-id="d7fd0-111">La lista de ámbitos para los que debe cubrir el token cuando genera.</span><span class="sxs-lookup"><span data-stu-id="d7fd0-111">The list of scopes for which the token must cover when generated.</span></span>