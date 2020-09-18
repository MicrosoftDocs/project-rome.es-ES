---
title: MCDUserActivity
description: Obtenga información sobre la clase MCDUserActivity y sus propiedades. Esta clase representa una instancia de actividad de un solo usuario.
keywords: Microsoft, Windows, actividades de usuario, iOS, iPhone, objectiveC, dispositivos conectados, proyecto Roma
ms.openlocfilehash: 8bdaf553611e868a5c37a9e033e2ba3126151967
ms.sourcegitcommit: 14b4f362bc0c924dff6493490c80624273d49d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2020
ms.locfileid: "90760149"
---
# <a name="class-mcduseractivity"></a>las `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

Esta clase representa una instancia de actividad de un solo usuario. Una aplicación crea una actividad de usuario durante su ejecución para notificar al sistema de un flujo de trabajo de usuario que puede continuar en otro dispositivo o en otro momento en el mismo dispositivo. Proporciona información sobre una tarea en la que está trabajando el usuario.

>**Nota:** Las instancias de MCDUserActivity tienen un límite de tamaño de 100 KB, por encima de las cuales no se pueden publicar.

## <a name="properties"></a>Propiedades

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

IDENTIFICADOR único de esta actividad.

### <a name="state"></a>state
`@property(nonatomic, readonly) MCDUserActivityState state;`

Estado de esta actividad.

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

URI que se va a seguir cuando se active esta actividad de usuario.

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

El URI descriptivo de la Web mantenido por esta actividad que se usará si se produce un error en el URI principal.

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

El URI de contenido para esta actividad (el URI de la imagen que se usará para representar la actividad en otro dispositivo).

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

el tipo MIME (Extensiones multipropósito de correo Internet) del contenido almacenado en **contentUri**. Por ejemplo, "text/plain".

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

Información básica de contenido de esta actividad. Por ejemplo, si la actividad estaba leyendo una fuente RSS, la cadena de contenido podría incluir el nombre del artículo y su autor.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

El nombre para mostrar de la aplicación para esta actividad.

### <a name="visualelements"></a>visualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

Los elementos visuales de esta actividad (información que se puede usar para el icono de "detalles" de la actividad).

### <a name="roamable"></a>apto
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

Obtiene o establece si esta actividad se va a desplazar a otros puntos de conexión.

## <a name="constructors"></a>Constructores

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

Crea una instancia de esta clase con un identificador determinado.

#### <a name="parameters"></a>Parámetros
* `activityId` 

Identificador de esta actividad (debe ser una cadena única).

#### <a name="returns"></a>Devoluciones
Devuelve una instancia de esta clase.

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

Crea una instancia de esta clase con un identificador determinado.

#### <a name="parameters"></a>Parámetros
* `activityId`

Identificador de esta actividad (debe ser una cadena única).

#### <a name="returns"></a>Devoluciones
Devuelve una instancia de esta clase.

## <a name="methods"></a>Métodos

### <a name="createsession"></a>createSession
`- (nonnull MCDUserActivitySession*)createSession;`

Crea una sesión de actividad de usuario a la que se asociará este MCDUserActivity. Un MCDUserActivitySession asociado indica que el usuario está ocupado actualmente en la actividad.

#### <a name="returns"></a>Devoluciones
La sesión creada.

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Publica la actividad del usuario. El MCDUserActivity debe tener un URI de activación y un miembro de VisualElements con el texto para mostrar establecido antes de llamar a este método. Se debe llamar a este método siempre que la aplicación modifique una propiedad de MCDUserActivity (para publicar la actualización).

#### <a name="parameters"></a>Parámetros
* `completionBlock` Bloque de código que se va a ejecutar cuando se complete.