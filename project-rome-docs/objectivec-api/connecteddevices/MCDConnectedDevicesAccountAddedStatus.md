---
title: MCDConnectedDevicesAccountAddedStatus
description: Contiene los valores que describen el estado de operación de agregar la cuenta.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: d7fadec0c3e69eedab23df18d803ee85fd37644b
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907207"
---
# <a name="enum-mcdconnecteddevicesaccountaddedstatus"></a><span data-ttu-id="0ca27-104">Enum `MCDConnectedDevicesAccountAddedStatus`</span><span class="sxs-lookup"><span data-stu-id="0ca27-104">enum `MCDConnectedDevicesAccountAddedStatus`</span></span>

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesAccountAddedStatus)
```  
<span data-ttu-id="0ca27-105">Contiene los valores que describen el estado de operación de agregar la cuenta.</span><span class="sxs-lookup"><span data-stu-id="0ca27-105">Contains the values that describe the add account operation status.</span></span>

## <a name="fields"></a><span data-ttu-id="0ca27-106">Campos</span><span class="sxs-lookup"><span data-stu-id="0ca27-106">Fields</span></span>

| <span data-ttu-id="0ca27-107">Nombre</span><span class="sxs-lookup"><span data-stu-id="0ca27-107">Name</span></span>                              |   <span data-ttu-id="0ca27-108">Valor</span><span class="sxs-lookup"><span data-stu-id="0ca27-108">Value</span></span>     | <span data-ttu-id="0ca27-109">Descripción</span><span class="sxs-lookup"><span data-stu-id="0ca27-109">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="0ca27-110">MCDConnectedDevicesAccountAddedStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="0ca27-110">MCDConnectedDevicesAccountAddedStatusSuccess</span></span> | <span data-ttu-id="0ca27-111">0</span><span class="sxs-lookup"><span data-stu-id="0ca27-111">0</span></span> | <span data-ttu-id="0ca27-112">La cuenta se agregó correctamente a la plataforma.</span><span class="sxs-lookup"><span data-stu-id="0ca27-112">The account was successfully added to the platform.</span></span> |
| <span data-ttu-id="0ca27-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="0ca27-113">MCDConnectedDevicesAccountAddedStatusErrorNoNetwork</span></span> | <span data-ttu-id="0ca27-114">1</span><span class="sxs-lookup"><span data-stu-id="0ca27-114">1</span></span> | <span data-ttu-id="0ca27-115">Error en la operación de cuenta desde que Roma no detectó ningún acceso a la red.</span><span class="sxs-lookup"><span data-stu-id="0ca27-115">The account operation failed since Rome detected no network access.</span></span> |
| <span data-ttu-id="0ca27-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span><span class="sxs-lookup"><span data-stu-id="0ca27-116">MCDConnectedDevicesAccountAddedStatusErrorServiceFailed</span></span> | <span data-ttu-id="0ca27-117">2</span><span class="sxs-lookup"><span data-stu-id="0ca27-117">2</span></span> | <span data-ttu-id="0ca27-118">Error en la operación de cuenta como Roma no pudo ponerse en contacto con los servicios web.</span><span class="sxs-lookup"><span data-stu-id="0ca27-118">The account operation failed since Rome was unable to contact web services.</span></span> |
| <span data-ttu-id="0ca27-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="0ca27-119">MCDConnectedDevicesAccountAddedStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="0ca27-120">3</span><span class="sxs-lookup"><span data-stu-id="0ca27-120">3</span></span> | <span data-ttu-id="0ca27-121">Error en la operación de cuenta dado que la aplicación no suscribirse al evento AccessTokenRequested.</span><span class="sxs-lookup"><span data-stu-id="0ca27-121">The account operation failed since the app didn't subscribe to the AccessTokenRequested event.</span></span> |
| <span data-ttu-id="0ca27-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="0ca27-122">MCDConnectedDevicesAccountAddedStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="0ca27-123">4</span><span class="sxs-lookup"><span data-stu-id="0ca27-123">4</span></span> | <span data-ttu-id="0ca27-124">Error en la operación de cuenta dado que la aplicación no pudo devolver un token cuando se solicita.</span><span class="sxs-lookup"><span data-stu-id="0ca27-124">The account operation failed since the app failed to return a token when requested.</span></span> |
| <span data-ttu-id="0ca27-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="0ca27-125">MCDConnectedDevicesAccountAddedStatusErrorUnknown</span></span> | <span data-ttu-id="0ca27-126">5</span><span class="sxs-lookup"><span data-stu-id="0ca27-126">5</span></span> | <span data-ttu-id="0ca27-127">Error en la operación de cuenta por razones desconocidas.</span><span class="sxs-lookup"><span data-stu-id="0ca27-127">The account operation failed for unknown reasons.</span></span> |
