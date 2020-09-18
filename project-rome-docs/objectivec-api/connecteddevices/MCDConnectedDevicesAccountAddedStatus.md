---
title: MCDConnectedDevicesAccountAddedStatus
description: Obtenga información sobre la enumeración MCDConnectedDevicesAccountAddedStatus. Esta enumeración contiene valores que describen el estado de la operación de agregar cuenta.
keywords: Microsoft, Windows, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: f7ea80735a8df2138f2557ff2e7ab4db0b4a9800
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90761039"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="d7b5b-105">enumeración `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="d7b5b-105">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="d7b5b-106">Contiene los valores que describen el estado de la operación de agregar cuenta.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-106">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="d7b5b-107">Campos</span><span class="sxs-lookup"><span data-stu-id="d7b5b-107">Fields</span></span>

| <span data-ttu-id="d7b5b-108">NOMBRE</span><span class="sxs-lookup"><span data-stu-id="d7b5b-108">Name</span></span>                              |   <span data-ttu-id="d7b5b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b5b-109">Value</span></span>     | <span data-ttu-id="d7b5b-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="d7b5b-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="d7b5b-111">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="d7b5b-111">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="d7b5b-112">0</span><span class="sxs-lookup"><span data-stu-id="d7b5b-112">0</span></span> | <span data-ttu-id="d7b5b-113">La cuenta se ha agregado correctamente a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-113">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="d7b5b-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="d7b5b-114">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="d7b5b-115">1</span><span class="sxs-lookup"><span data-stu-id="d7b5b-115">1</span></span> | <span data-ttu-id="d7b5b-116">No se pudo realizar la operación de cuenta porque Roma no detectó acceso a la red.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-116">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="d7b5b-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="d7b5b-117">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="d7b5b-118">2</span><span class="sxs-lookup"><span data-stu-id="d7b5b-118">2</span></span> | <span data-ttu-id="d7b5b-119">No se pudo realizar la operación de cuenta porque Roma no pudo ponerse en contacto con los servicios Web.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-119">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="d7b5b-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="d7b5b-120">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="d7b5b-121">3</span><span class="sxs-lookup"><span data-stu-id="d7b5b-121">3</span></span> | <span data-ttu-id="d7b5b-122">No se pudo realizar la operación de cuenta porque la aplicación no se suscribió al evento AccessTokenRequested.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-122">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="d7b5b-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="d7b5b-123">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="d7b5b-124">4</span><span class="sxs-lookup"><span data-stu-id="d7b5b-124">4</span></span> | <span data-ttu-id="d7b5b-125">No se pudo realizar la operación de cuenta porque la aplicación no pudo devolver un token cuando se solicitó.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-125">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="d7b5b-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="d7b5b-126">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="d7b5b-127">5</span><span class="sxs-lookup"><span data-stu-id="d7b5b-127">5</span></span> | <span data-ttu-id="d7b5b-128">No se pudo realizar la operación de cuenta por motivos desconocidos.</span><span class="sxs-lookup"><span data-stu-id="d7b5b-128">The account operation failed for unknown reasons.</span></span> |
