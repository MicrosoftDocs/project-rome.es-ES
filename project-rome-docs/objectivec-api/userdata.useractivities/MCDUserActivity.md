---
title: MCDUserActivity
description: Esta clase representa una instancia de la actividad de usuario único.
keywords: Microsoft, windows, las actividades del usuario, iOS, iPhone, objectiveC, conectado los dispositivos, proyecto Roma
ms.openlocfilehash: f01889f5e41c761fe359ed1fa90befee4a8aca46
ms.sourcegitcommit: 75680b384946e11257bb2a33044a3172dec5220e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58907427"
---
# <a name="class-mcduseractivity"></a>Clase `MCDUserActivity`

```
@interface MCDUserActivity : NSObject
```

Esta clase representa una instancia de la actividad de usuario único. Se crea una actividad de usuario por una aplicación durante su ejecución para notificar al sistema de un flujo de trabajo de usuario que se puede continuar en otro dispositivo o en otro momento en el mismo dispositivo. Proporciona información acerca de una tarea que el usuario está ocupado en.

>**Nota:** Las instancias de MCDUserActivity tienen un límite de tamaño de 100KB, por encima del cual no se pueden publicar.

## <a name="properties"></a>Propiedades

### <a name="activityid"></a>activityId
`@property(nonatomic, readonly, nonnull) NSString* activityId;`

El identificador único para esta actividad.

### <a name="state"></a>Estado
`@property(nonatomic, readonly) MCDUserActivityState state;`

El estado de esta actividad.

### <a name="activationuri"></a>activationUri
`@property(nonatomic, copy, nonnull) NSString* activationUri;`

El URI que seguir cuando se activa esta actividad de usuario.

### <a name="fallbackuri"></a>fallbackUri
`@property(nonatomic, copy, nullable) NSString* fallbackUri;`

El URI de aptos para la web mantenido por esta actividad, que se utilizará si se produce un error en el URI de la principal.

### <a name="contenturi"></a>contentUri
`@property(nonatomic, copy, nullable) NSString* contentUri;`

El URI de contenido para esta actividad (el URI de la imagen que se usará para representar la actividad en otro dispositivo).

### <a name="contenttype"></a>contentType
`@property(nonatomic, copy, nullable) NSString* contentType;`

el tipo MIME (Multipurpose Internet Mail Extensions) del contenido almacenado en **contentUri**. Por ejemplo, "text/plain".

### <a name="contentinfojson"></a>contentInfoJson
`@property(nonatomic, copy, nullable) NSString* contentInfoJson;`

La información básica de contenido para esta actividad. Por ejemplo, si su actividad estaba leyendo una fuente RSS, la cadena de contenido puede incluir el nombre del artículo y su autor.

### <a name="appdisplayname"></a>appDisplayName
`@property(nonatomic, readonly, nullable) NSString* appDisplayName;`

El nombre para mostrar aplicaciones para esta actividad.

### <a name="visualelements"></a>visualElements
`@property(nonatomic, retain, nonnull) MCDUserActivityVisualElements* visualElements`

Los elementos visuales de esta actividad (información que se puede usar para el icono "Detalles" de la actividad).

### <a name="roamable"></a>apto
`@property(nonatomic, assign, getter = isRoamable) BOOL roamable;`

Obtiene o establece si esta actividad se ha movido a otros puntos de conexión.

## <a name="constructors"></a>Constructores

### <a name="activitywithactivityid"></a>activityWithActivityId
`+ (nullable instancetype)activityWithActivityId:(nonnull NSString*)activityId;`

Crea una instancia de esta clase con un identificador especificado.

#### <a name="parameters"></a>Parámetros
* `activityId` 

El identificador para esta actividad (debe ser una cadena única).

#### <a name="returns"></a>Devuelve
Devuelve una instancia de esta clase.

### <a name="initwithactivityid"></a>initWithActivityId
`- (nullable instancetype)initWithActivityId:(nonnull NSString*)activityId;`

Crea una instancia de esta clase con un identificador especificado.

#### <a name="parameters"></a>Parámetros
* `activityId`

El identificador para esta actividad (debe ser una cadena única).

#### <a name="returns"></a>Devuelve
Devuelve una instancia de esta clase.

## <a name="methods"></a>Métodos

### <a name="createsession"></a>createSession
`- (nonnull MCDUserActivitySession*)createSession;`

Crea una sesión de la actividad de usuario que se asociará este MCDUserActivity. Un asociado MCDUserActivitySession indica que el usuario esté implicado actualmente en la actividad.

#### <a name="returns"></a>Devuelve
La sesión creada.

### <a name="saveasync"></a>saveAsync
`- (void)saveAsync:(nonnull void (^)(NSError* _Nullable))completionBlock;`

Publica la actividad del usuario. El MCDUserActivity debe tener una identificador URI de la activación y un miembro VisualElements con conjunto de texto para mostrar antes de llama a este método. Este método debe llamarse siempre que la aplicación modifica una propiedad de la MCDUserActivity (con el fin de publicar la actualización).

#### <a name="parameters"></a>Parámetros
* `completionBlock` El bloque de código para ejecutar la finalización.