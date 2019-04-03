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
# <a name="class-mcdconnecteddevicesnotificationregistrationmanager"></a>Clase `MCDConnectedDevicesNotificationRegistrationManager` 

```
@interface MCDConnectedDevicesNotificationRegistrationManager : NSObject
```  
Administra el registro para la notificación de dispositivos conectados a plataforma en la nube para todas las cuentas.

MCDConnectedDevicesNotificationRegistrationManager administra la información de notificación registrada para cada cuenta. Cualquier momento información de notificación de una aplicación cambia (por ejemplo, cuando lo APNS su token), o cuando expira la información de notificación, una aplicación debe volver a registrar su información. Si una aplicación solo se preocupa las respuestas a la comunicación saliente, se puede usar un registro de sondeo.

> [!NOTE] 
> Información de notificación debe estar registrado para que muchos escenarios ConnectedDevices funcionará correctamente. 

## <a name="properties"></a>Propiedades

### <a name="registrationstatechanged"></a>registrationStateChanged
`@property(nonatomic, readonly, nonnull) MCDEvent<MCDConnectedDevicesNotificationRegistrationManager*, MCDConnectedDevicesNotificationRegistrationStateChangedEventArgs*>* registrationStateChanged;`

Evento que se va a informar a la aplicación cuando cambia el estado de registro de notificación para una cuenta. 

## <a name="methods"></a>Métodos

### <a name="registerforaccountasync"></a>registerForAccountAsync
`- (void) registerForAccountAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration callback:(nonnull void (^)(BOOL, NSError* _Nullable))callback __attribute__((deprecated("Use registerAsync instead")));`

Registrar la cuenta especificada con la información de registro de notificación determinada. Esto crea un canal de notificación para que esta aplicación puede recibir una notificación sobre la nueva información de dispositivos conectados para esta cuenta. Tenga en cuenta que otras aplicaciones no pueden comunicar con esta aplicación mediante este canal de notificación hasta que se publica la información de MCDRemoteSystemAppRegistration.

> [!WARNING]
> Esta función está en desuso. Use registerAsync en su lugar.

#### <a name="parameters"></a>Parámetros 
* `account` 

Cuenta para el que se va a registrar la información de notificación.

* `notificationRegistration` 

Información de notificación para registrarse.

* `callback` 

La devolución de llamada como resultado de if el registro se completó correctamente.

### <a name="registerasync"></a>registerAsync
`- (void) registerAsync:(MCDConnectedDevicesAccount* _Nonnull)account registration:(MCDConnectedDevicesNotificationRegistration* _Nonnull)notificationRegistration completion:(nonnull void (^)(MCDConnectedDevicesNotificationRegistrationResult* _Nonnull, NSError* _Nullable))callback;`

Registrar la cuenta especificada con la información de registro de notificación determinada. Esto crea un canal de notificación para que esta aplicación puede recibir una notificación sobre la nueva información de dispositivos conectados para esta cuenta. Tenga en cuenta que otras aplicaciones no pueden comunicar con esta aplicación mediante este canal de notificación hasta que se publica la información de MCDRemoteSystemAppRegistration.

#### <a name="parameters"></a>Parámetros 
* `account` 

Cuenta para el que se va a registrar la información de notificación.

* `notificationRegistration` 

Información de notificación para registrarse.

* `callback` 

La devolución de llamada como resultado de if el registro se completó correctamente.

### <a name="getnotificationregistrationstateforaccount"></a>getNotificationRegistrationStateForAccount
`- (MCDConnectedDevicesNotificationRegistrationState) getNotificationRegistrationStateForAccount:(MCDConnectedDevicesAccount* _Nonnull)account;`

Recuperar el estado de registro de notificación actual para la cuenta especificada. La información de notificación que se ha registrado finalmente caducará (útil si la aplicación se ha desinstalado o no se ejecutan en mucho tiempo). Una aplicación debe volver a registrar su información de notificación cuando el registro está a punto de expirar o expirada. 

#### <a name="parameters"></a>Parámetros 
* `account`

Cuenta para el que se va a obtener el estado de registro.

#### <a name="returns"></a>Devuelve

Estado del registro de notificación.
