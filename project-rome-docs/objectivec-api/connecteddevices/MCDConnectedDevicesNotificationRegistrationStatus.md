---
title: MCDConnectedDevicesNotificationRegistrationStatus
description: Valores que se usa para comunicar el estado de registro en la nube.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: c7d770c73479afb949a4917b5457b12e23b78698
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909137"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationstatus"></a><span data-ttu-id="d82dd-104">Clase `MCDConnectedDevicesNotificationRegistrationStatus`</span><span class="sxs-lookup"><span data-stu-id="d82dd-104">class `MCDConnectedDevicesNotificationRegistrationStatus`</span></span> 

```
typedef NS_ENUM(NSInteger, MCDConnectedDevicesNotificationRegistrationStatus)
```  
<span data-ttu-id="d82dd-105">Enumeración que indica el estado de la operación de registro.</span><span class="sxs-lookup"><span data-stu-id="d82dd-105">Enumeration indicating the status of the registration operation.</span></span>
<span data-ttu-id="d82dd-106">Los Estados de error indican condiciones transitorias, donde el desarrollador puede querer vuelva a intentar el registro.</span><span class="sxs-lookup"><span data-stu-id="d82dd-106">The error statuses indicate transient conditions where the app developer may want to retry registration.</span></span>

## <a name="fields"></a><span data-ttu-id="d82dd-107">Campos</span><span class="sxs-lookup"><span data-stu-id="d82dd-107">Fields</span></span>

| <span data-ttu-id="d82dd-108">Nombre</span><span class="sxs-lookup"><span data-stu-id="d82dd-108">Name</span></span>                              |   <span data-ttu-id="d82dd-109">Valor</span><span class="sxs-lookup"><span data-stu-id="d82dd-109">Value</span></span>     | <span data-ttu-id="d82dd-110">Descripción</span><span class="sxs-lookup"><span data-stu-id="d82dd-110">Description</span></span> |
|:----------------------------------|:------|:-------------------------------|
| <span data-ttu-id="d82dd-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span><span class="sxs-lookup"><span data-stu-id="d82dd-111">MCDConnectedDevicesNotificationRegistrationStatusSuccess</span></span> | <span data-ttu-id="d82dd-112">0</span><span class="sxs-lookup"><span data-stu-id="d82dd-112">0</span></span> | <span data-ttu-id="d82dd-113">Operación se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="d82dd-113">Operation completed successfully.</span></span>
| <span data-ttu-id="d82dd-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span><span class="sxs-lookup"><span data-stu-id="d82dd-114">MCDConnectedDevicesNotificationRegistrationStatusErrorNoNetwork</span></span> | <span data-ttu-id="d82dd-115">1</span><span class="sxs-lookup"><span data-stu-id="d82dd-115">1</span></span> | <span data-ttu-id="d82dd-116">Red no estaba disponible.</span><span class="sxs-lookup"><span data-stu-id="d82dd-116">Network was unavailable.</span></span> |
| <span data-ttu-id="d82dd-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span><span class="sxs-lookup"><span data-stu-id="d82dd-117">MCDConnectedDevicesNotificationRegistrationStatusErrorWebFailure</span></span> | <span data-ttu-id="d82dd-118">2</span><span class="sxs-lookup"><span data-stu-id="d82dd-118">2</span></span> | <span data-ttu-id="d82dd-119">Error en un servicio web.</span><span class="sxs-lookup"><span data-stu-id="d82dd-119">A web service failed.</span></span> |
| <span data-ttu-id="d82dd-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span><span class="sxs-lookup"><span data-stu-id="d82dd-120">MCDConnectedDevicesNotificationRegistrationStatusErrorNoTokenRequestSubscriber</span></span> | <span data-ttu-id="d82dd-121">3</span><span class="sxs-lookup"><span data-stu-id="d82dd-121">3</span></span> | <span data-ttu-id="d82dd-122">No hay ningún suscriptor de la solicitud de token respondió.</span><span class="sxs-lookup"><span data-stu-id="d82dd-122">No token request subscribers responded.</span></span> |
| <span data-ttu-id="d82dd-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span><span class="sxs-lookup"><span data-stu-id="d82dd-123">MCDConnectedDevicesNotificationRegistrationStatusErrorTokenRequestFailed</span></span> | <span data-ttu-id="d82dd-124">4</span><span class="sxs-lookup"><span data-stu-id="d82dd-124">4</span></span> | <span data-ttu-id="d82dd-125">Error en la solicitud de token.</span><span class="sxs-lookup"><span data-stu-id="d82dd-125">The token request failed.</span></span> |
| <span data-ttu-id="d82dd-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span><span class="sxs-lookup"><span data-stu-id="d82dd-126">MCDConnectedDevicesNotificationRegistrationStatusErrorAccountNotFound</span></span> | <span data-ttu-id="d82dd-127">5</span><span class="sxs-lookup"><span data-stu-id="d82dd-127">5</span></span> | <span data-ttu-id="d82dd-128">No se encontró la cuenta para registrar la información de.</span><span class="sxs-lookup"><span data-stu-id="d82dd-128">Account to register information for was not found.</span></span> |
| <span data-ttu-id="d82dd-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span><span class="sxs-lookup"><span data-stu-id="d82dd-129">MCDConnectedDevicesNotificationRegistrationStatusErrorUnknown</span></span> | <span data-ttu-id="d82dd-130">6</span><span class="sxs-lookup"><span data-stu-id="d82dd-130">6</span></span> | <span data-ttu-id="d82dd-131">Operación encontró un error desconocido.</span><span class="sxs-lookup"><span data-stu-id="d82dd-131">Operation encountered an unknown error.</span></span> |