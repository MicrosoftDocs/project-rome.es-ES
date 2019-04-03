---
title: MCDConnectedDevicesNotificationRegistrationManager
description: Administra el registro para la notificación de Roma en la nube para todas las cuentas.
keywords: Microsoft, windows, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: d4f5f7963514795e3e296d9bdb42b1811af4f7cc
ms.sourcegitcommit: 945a0f4bda02e3b4eb9a665379c2af9bd5285a53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58909907"
---
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a><span data-ttu-id="b4543-104">Clase `MCDConnectedDevicesNotificationRegistrationManager`</span><span class="sxs-lookup"><span data-stu-id="b4543-104">class `MCDConnectedDevicesNotificationRegistrationManager`</span></span> 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
<span data-ttu-id="b4543-105">Administra el registro para la notificación de dispositivos conectados a plataforma en la nube para todas las cuentas.</span><span class="sxs-lookup"><span data-stu-id="b4543-105">Manages the registration for the Connected Devices platform cloud notification for all accounts.</span></span>

<span data-ttu-id="b4543-106">MCDConnectedDevicesNotificationRegistrationManager administra la información de notificación registrada para cada cuenta.</span><span class="sxs-lookup"><span data-stu-id="b4543-106">MCDConnectedDevicesNotificationRegistrationManager manages the notification information registered for each account.</span></span> <span data-ttu-id="b4543-107">Cualquier momento información de notificación de una aplicación cambia (por ejemplo, cuando lo APNS su token), o cuando expira la información de notificación, una aplicación debe volver a registrar su información.</span><span class="sxs-lookup"><span data-stu-id="b4543-107">Any time an app's notification information changes (for example, when APNS changes its token), or when the notification information is expiring, an app should re-register its information.</span></span> <span data-ttu-id="b4543-108">Si una aplicación solo se preocupa las respuestas a la comunicación saliente, se puede usar un registro de sondeo.</span><span class="sxs-lookup"><span data-stu-id="b4543-108">If an application only cares about responses to outgoing communication, a Polling registration may be used.</span></span>

> [!NOTE] 
> <span data-ttu-id="b4543-109">Información de notificación debe estar registrado para que muchos escenarios ConnectedDevices funcionará correctamente.</span><span class="sxs-lookup"><span data-stu-id="b4543-109">Notification information must be registered before many ConnectedDevices scenarios will work successfully.</span></span> 

## <a name="properties"></a><span data-ttu-id="b4543-110">Propiedades</span><span class="sxs-lookup"><span data-stu-id="b4543-110">Properties</span></span>

### <a name="registrationstatechanged"></a><span data-ttu-id="b4543-111">registrationStateChanged</span><span class="sxs-lookup"><span data-stu-id="b4543-111">registrationStateChanged</span></span>
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

<span data-ttu-id="b4543-112">Evento que se va a informar a la aplicación cuando cambia el estado de registro de notificación para una cuenta.</span><span class="sxs-lookup"><span data-stu-id="b4543-112">Event to let the app know when notification registration state changes for an account.</span></span> 

## <a name="methods"></a><span data-ttu-id="b4543-113">Métodos</span><span class="sxs-lookup"><span data-stu-id="b4543-113">Methods</span></span>

### <a name="registerforaccountasync"></a><span data-ttu-id="b4543-114">registerForAccountAsync</span><span class="sxs-lookup"><span data-stu-id="b4543-114">registerForAccountAsync</span></span>
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

<span data-ttu-id="b4543-115">Registrar la cuenta especificada con la información de registro de notificación determinada.</span><span class="sxs-lookup"><span data-stu-id="b4543-115">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="b4543-116">Esto crea un canal de notificación para que esta aplicación puede recibir una notificación sobre la nueva información de dispositivos conectados para esta cuenta.</span><span class="sxs-lookup"><span data-stu-id="b4543-116">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="b4543-117">Tenga en cuenta que otras aplicaciones no pueden comunicar con esta aplicación mediante este canal de notificación hasta que se publica la información de MCDRemoteSystemAppRegistration.</span><span class="sxs-lookup"><span data-stu-id="b4543-117">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

> [!WARNING]
> <span data-ttu-id="b4543-118">Esta función está en desuso.</span><span class="sxs-lookup"><span data-stu-id="b4543-118">This function is deprecated.</span></span> <span data-ttu-id="b4543-119">Use registerAsync en su lugar.</span><span class="sxs-lookup"><span data-stu-id="b4543-119">Please use registerAsync instead.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b4543-120">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b4543-120">Parameters</span></span> 
* `account` 

<span data-ttu-id="b4543-121">Cuenta para el que se va a registrar la información de notificación.</span><span class="sxs-lookup"><span data-stu-id="b4543-121">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="b4543-122">Información de notificación para registrarse.</span><span class="sxs-lookup"><span data-stu-id="b4543-122">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="b4543-123">La devolución de llamada como resultado de if el registro se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="b4543-123">The callback result for if the registration completed successfully.</span></span>

### <a name="registerasync"></a><span data-ttu-id="b4543-124">registerAsync</span><span class="sxs-lookup"><span data-stu-id="b4543-124">registerAsync</span></span>
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

<span data-ttu-id="b4543-125">Registrar la cuenta especificada con la información de registro de notificación determinada.</span><span class="sxs-lookup"><span data-stu-id="b4543-125">Register the given account with the given notification registration information.</span></span> <span data-ttu-id="b4543-126">Esto crea un canal de notificación para que esta aplicación puede recibir una notificación sobre la nueva información de dispositivos conectados para esta cuenta.</span><span class="sxs-lookup"><span data-stu-id="b4543-126">This creates a notification channel so that this application can be notified about new Connected Devices information for this account.</span></span> <span data-ttu-id="b4543-127">Tenga en cuenta que otras aplicaciones no pueden comunicar con esta aplicación mediante este canal de notificación hasta que se publica la información de MCDRemoteSystemAppRegistration.</span><span class="sxs-lookup"><span data-stu-id="b4543-127">Note that other applications can not communicate with this app using this notification channel until the MCDRemoteSystemAppRegistration information is published.</span></span>

#### <a name="parameters"></a><span data-ttu-id="b4543-128">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b4543-128">Parameters</span></span> 
* `account` 

<span data-ttu-id="b4543-129">Cuenta para el que se va a registrar la información de notificación.</span><span class="sxs-lookup"><span data-stu-id="b4543-129">Account for which to register notification information.</span></span>

* `notificationRegistration` 

<span data-ttu-id="b4543-130">Información de notificación para registrarse.</span><span class="sxs-lookup"><span data-stu-id="b4543-130">Notification information to register.</span></span>

* `callback` 

<span data-ttu-id="b4543-131">La devolución de llamada como resultado de if el registro se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="b4543-131">The callback result for if the registration completed successfully.</span></span>

### <a name="getnotificationregistrationstateforaccount"></a><span data-ttu-id="b4543-132">getNotificationRegistrationStateForAccount</span><span class="sxs-lookup"><span data-stu-id="b4543-132">getNotificationRegistrationStateForAccount</span></span>
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

<span data-ttu-id="b4543-133">Recuperar el estado de registro de notificación actual para la cuenta especificada.</span><span class="sxs-lookup"><span data-stu-id="b4543-133">Retrieve the current notification registration state for the given account.</span></span> <span data-ttu-id="b4543-134">La información de notificación que se ha registrado finalmente caducará (útil si la aplicación se ha desinstalado o no se ejecutan en mucho tiempo).</span><span class="sxs-lookup"><span data-stu-id="b4543-134">The notification information that is registered will eventually expire (useful if the app is uninstalled or not run in a very long time).</span></span> <span data-ttu-id="b4543-135">Una aplicación debe volver a registrar su información de notificación cuando el registro está a punto de expirar o expirada.</span><span class="sxs-lookup"><span data-stu-id="b4543-135">An app should re-register its notification information when the registration is expiring / expired.</span></span> 

#### <a name="parameters"></a><span data-ttu-id="b4543-136">Parámetros</span><span class="sxs-lookup"><span data-stu-id="b4543-136">Parameters</span></span> 
* `account`

<span data-ttu-id="b4543-137">Cuenta para el que se va a obtener el estado de registro.</span><span class="sxs-lookup"><span data-stu-id="b4543-137">Account for which to get registration state.</span></span>

#### <a name="returns"></a><span data-ttu-id="b4543-138">Devuelve</span><span class="sxs-lookup"><span data-stu-id="b4543-138">Returns</span></span>

<span data-ttu-id="b4543-139">Estado del registro de notificación.</span><span class="sxs-lookup"><span data-stu-id="b4543-139">State of the notification registration.</span></span>
