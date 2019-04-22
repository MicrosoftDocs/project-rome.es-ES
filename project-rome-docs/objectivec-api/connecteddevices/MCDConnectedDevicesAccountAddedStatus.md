---
title: MCDConnectedDevicesAccountAddedStatus
description: Contiene los valores que describen el estado de operación de agregar la cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59801567"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="d0015-104">Enum `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="d0015-104">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="d0015-105">Contiene los valores que describen el estado de operación de agregar la cuenta.</span><span class="sxs-lookup"><span data-stu-id="d0015-105">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="d0015-106">Campos</span><span class="sxs-lookup"><span data-stu-id="d0015-106">Fields</span></span>

| <span data-ttu-id="d0015-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="d0015-107">Name</span></span>                              |   <span data-ttu-id="d0015-108">Valor</span><span class="sxs-lookup"><span data-stu-id="d0015-108">Value</span></span>     | <span data-ttu-id="d0015-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="d0015-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="d0015-110">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="d0015-110">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="d0015-111">0</span><span class="sxs-lookup"><span data-stu-id="d0015-111">0</span></span> | <span data-ttu-id="d0015-112">La cuenta se agregó correctamente a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="d0015-112">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="d0015-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="d0015-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="d0015-114">1</span><span class="sxs-lookup"><span data-stu-id="d0015-114">1</span></span> | <span data-ttu-id="d0015-115">Error en la operación de cuenta desde que Roma no detectó ningún acceso a la red.</span><span class="sxs-lookup"><span data-stu-id="d0015-115">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="d0015-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="d0015-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="d0015-117">2</span><span class="sxs-lookup"><span data-stu-id="d0015-117">2</span></span> | <span data-ttu-id="d0015-118">Error en la operación de cuenta como Roma no pudo ponerse en contacto con los servicios web.</span><span class="sxs-lookup"><span data-stu-id="d0015-118">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="d0015-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="d0015-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="d0015-120">3</span><span class="sxs-lookup"><span data-stu-id="d0015-120">3</span></span> | <span data-ttu-id="d0015-121">Error en la operación de cuenta dado que la aplicación no suscribirse al evento AccessTokenRequested.</span><span class="sxs-lookup"><span data-stu-id="d0015-121">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="d0015-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="d0015-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="d0015-123">4</span><span class="sxs-lookup"><span data-stu-id="d0015-123">4</span></span> | <span data-ttu-id="d0015-124">Error en la operación de cuenta dado que la aplicación no pudo devolver un token cuando se solicita.</span><span class="sxs-lookup"><span data-stu-id="d0015-124">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="d0015-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="d0015-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="d0015-126">5</span><span class="sxs-lookup"><span data-stu-id="d0015-126">5</span></span> | <span data-ttu-id="d0015-127">Error en la operación de cuenta por razones desconocidas.</span><span class="sxs-lookup"><span data-stu-id="d0015-127">The account operation failed for unknown reasons.</span></span> |
