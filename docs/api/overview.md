---
title: Información general de la API de NuGet
description: La API de NuGet es un conjunto de puntos de conexión HTTP que puede usarse para descargar los paquetes, capturar metadatos, publicar nuevos paquetes, etcetera.
author: joelverhagen
ms.author: jver
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: bb15b4decef104f1aefe37fd18f3358181a848af
ms.sourcegitcommit: 2af17c8bb452a538977794bf559cdd78d58f2790
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "58637667"
---
# <a name="nuget-api"></a>API NuGet

La API de NuGet es un conjunto de puntos de conexión HTTP que puede usarse para descargar los paquetes, capturar metadatos, publicar nuevos paquetes y realizar otras operaciones disponibles en los clientes de NuGet oficiales.

Esta API se usa por el cliente de NuGet en Visual Studio, nuget.exe y la CLI de .NET para realizar operaciones de NuGet como [ `dotnet restore` ](/dotnet/core/tools/dotnet-restore?tabs=netcore2x), búsqueda en la IU de Visual Studio, y [ `nuget.exe push` ](../tools/cli-ref-push.md).

Tenga en cuenta que en algunos casos, nuget.org tiene requisitos adicionales que no se aplican por otros orígenes de paquetes. Estas diferencias se documentan por la [protocolos de nuget.org](nuget-protocols.md).

Para una enumeración sencilla y descarga de versiones de nuget.exe disponibles, consulte el [tools.json](tools-json.md) punto de conexión.

## <a name="service-index"></a>Índice de servicio

El punto de entrada para la API es un documento JSON en una ubicación conocida. Se llama a este documento el **índice de servicio**. La ubicación del índice de servicio de nuget.org es `https://api.nuget.org/v3/index.json`.

Este documento JSON que contiene una lista de *recursos* que ofrecen una funcionalidad diferente y satisfacer los distintos casos de uso.

Los clientes compatibles con la API deben aceptar una o varias de estas direcciones URL de índice de servicio como la forma de conectarse a los orígenes del paquete correspondiente.

Para obtener más información sobre el índice de servicio, consulte [su referencia de API](service-index.md).

## <a name="versioning"></a>Control de versiones

La API es la versión 3 del protocolo HTTP de NuGet. Este protocolo se conoce a veces como "la API de V3". Estos documentos de referencia se hará referencia a esta versión del protocolo simplemente como "la API".

La versión de esquema de índice de servicio se indica mediante el `version` propiedad en el índice de servicio. La API exige que la cadena de versión tiene un número de versión principal `3`. Cuando se realizan cambios no importantes en el esquema de índice de servicio, aumentará la versión secundaria de la cadena de versión.

Los clientes más antiguos (por ejemplo, nuget.exe 2.x) no admiten la API de V3 y solo admiten la API V2 anterior, que no se documenta aquí.

La API de NuGet V3 se denomina así porque es el sucesor de la API V2, que era el protocolo basado en OData, implementado por la versión 2.x del cliente NuGet oficial. La API de V3 primero era compatible con la versión 3.0 del cliente NuGet oficial y es todavía la versión de protocolo principal más reciente compatible con el cliente de NuGet 4.0 y en. 

Se realizaron cambios en los protocolos que no son importantes a la API desde el lanzamiento en primer lugar.

## <a name="resources-and-schema"></a>Los recursos y el esquema

El **índice de servicio** describe una variedad de recursos. El conjunto actual de los recursos admitidos son los siguientes:

Nombre del recurso                                                        | Obligatorio | Descripción
-------------------------------------------------------------------- | -------- | -----------
[Catálogo](catalog-resource.md)                                       | No       | Registro completo de todos los eventos de paquete.
[PackageBaseAddress](package-base-address-resource.md)               | sí      | Obtener contenido del paquete (archivo .nupkg).
[PackageDetailsUriTemplate](package-details-template-resource.md)    | No       | Construir una dirección URL para tener acceso a una página web de detalles de paquete.
[PackagePublish](package-publish-resource.md)                        | sí      | Insertar y eliminar (o quitar de la lista) paquetes.
[RegistrationsBaseUrl](registration-base-url-resource.md)            | sí      | Obtener metadatos del paquete.
[ReportAbuseUriTemplate](report-abuse-resource.md)                   | No       | Construir una dirección URL para tener acceso a una página web de abuso de informe.
[RepositorySignatures](repository-signatures-resource.md)            | No       | Obtener certificados usados para firmar el repositorio.
[SearchAutocompleteService](search-autocomplete-service-resource.md) | No       | Detectar el Id. de paquete y las versiones por la subcadena.
[SearchQueryService](search-query-service-resource.md)               | sí      | Filtrar y buscar paquetes mediante la palabra clave.
[SymbolPackagePublish](symbol-package-publish-resource.md)           | No       | Insertar paquetes de símbolos.

En general, todos los datos no binarios devueltos por un recurso de API se serializan mediante JSON. El esquema de respuesta devuelto por cada recurso en el índice de servicio se define por separado para ese recurso. Para obtener más información acerca de cada recurso, vea los temas enumerados anteriormente.

En el futuro, a medida que evoluciona el protocolo, se pueden agregar nuevas propiedades a las respuestas JSON. El cliente esté preparada para el futuro, la implementación no debe suponer que el esquema de respuesta es final y no puede incluir datos adicionales. Se deben omitir todas las propiedades que no entiende la implementación.

> [!Note]
> Cuando un origen no implementa `SearchAutocompleteService` cualquier comportamiento de Autocompletar debe deshabilitarse de forma correcta. Cuando `ReportAbuseUriTemplate` no está implementado, la vuelve de cliente de NuGet oficial de nuget.org a la dirección URL de abuso de informes (sometidas a seguimiento por [NuGet/Home #4924](https://github.com/NuGet/Home/issues/4924)). Pueden optar por otros clientes simplemente no se muestra una dirección URL de abuso de informe al usuario.

### <a name="undocumented-resources-on-nugetorg"></a>Recursos no documentados en nuget.org

El índice de servicio V3 en nuget.org tiene algunos recursos que no se han documentado anteriormente. Hay varias razones para no documentar un recurso.

En primer lugar, se no documenta los recursos que se utiliza como un detalle de implementación de nuget.org. El `SearchGalleryQueryService` se encuentra en esta categoría. [NuGetGallery](https://github.com/NuGet/NuGetGallery) usa este recurso para delegar algunas V2 consultas (OData) en nuestro índice de búsqueda en lugar de usar la base de datos. Este recurso se introdujo por motivos de escalabilidad y no está pensado para uso externo.

En segundo lugar, se no documenta los recursos que nunca se distribuye con una versión RTM del cliente oficial.
`PackageDisplayMetadataUriTemplate` y `PackageVersionDisplayMetadataUriTemplate` entran en esta categoría.

En tercer lugar, documentamos no los recursos que están estrechamente junto con el protocolo de V2, que a su vez está documentado deliberadamente. El `LegacyGallery` recurso se encuentra en esta categoría. Este recurso permite un índice de servicio V3 para que apunte a una dirección URL del origen de V2 correspondiente. Este recurso es compatible con la `nuget.exe list`.

Si un recurso no está documentado aquí, hemos *fuertemente* recomendamos que no tome una dependencia en ellos. Podemos quitar o cambiar el comportamiento de estos recursos no documentados que podría afectar a su implementación de manera inesperada.

## <a name="timestamps"></a>Marcas de tiempo

Todas las marcas de tiempo devueltos por la API son UTC o si no se especifican utilizando [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html) representación. 

## <a name="http-methods"></a>Métodos HTTP

Verb   | Usar
------ | -----------
GET    | Realiza una operación de solo lectura, normalmente, recuperación de datos.
HEAD   | Obtiene los encabezados de respuesta correspondiente `GET` solicitud.
PUT    | Crea un recurso que no existe o, si existe, lo actualiza. Algunos recursos pueden no admitir la actualización.
SUPRIMIR | Elimina o quita un recurso de la lista.

## <a name="http-status-codes"></a>Códigos de estado HTTP

Código | Descripción
---- | -----
200  | Caso de éxito, y hay un cuerpo de respuesta.
201  | Se creó correctamente y el recurso.
202  | Caso de éxito, la solicitud se ha aceptado pero algún trabajo pueden incompleta y completados asincrónicamente.
204  | Correcto, pero no hay ningún cuerpo de respuesta.
301  | Una redirección permanente.
302  | Una redirección temporal.
400  | Los parámetros en la dirección URL o en el cuerpo de solicitud no son válidos.
401  | Las credenciales proporcionadas no son válidas.
403  | No se permite la acción dada las credenciales proporcionadas.
404  | El recurso solicitado no existe.
409  | La solicitud entra en conflicto con un recurso existente.
500  | El servicio ha encontrado un error inesperado.
503  | El servicio no está disponible temporalmente.

Cualquier `GET` solicitud realizada a un punto de conexión de API puede devolver una redirección de HTTP (301 o 302). Los clientes deben controlar correctamente estas redirecciones observando el `Location` encabezado y emitir un posteriores `GET`. Documentación relativa a los puntos de conexión concretos no llamará a explícitamente horizontal donde se pueden utilizar las redirecciones.

En el caso de un código de estado de nivel 500, el cliente puede implementar un mecanismo de reintento razonable. El oficial NuGet cliente lo intenta tres veces al encontrar cualquier código de estado del nivel 500 o error DNS o TCP.

## <a name="http-request-headers"></a>Encabezados de solicitud HTTP

Name                     | Descripción
------------------------ | -----------
X-NuGet-ApiKey           | Es necesario para la inserción y eliminación, consulte [ `PackagePublish` recursos](package-publish-resource.md)
X-NuGet-Client-Version   | **En desuso** y reemplazado por `X-NuGet-Protocol-Version`
X-NuGet-Protocol-Version | Necesario en algunos casos solo en nuget.org, vea [protocolos de nuget.org](NuGet-Protocols.md)
X-NuGet-Session-Id       | *Opcional*. NuGet clientes v4.7 + identificar las solicitudes HTTP que forman parte de la misma sesión de cliente de NuGet.

El `X-NuGet-Session-Id` tiene un valor único para todas las operaciones relacionadas con una sola restauración en `PackageReference`. Para otros escenarios como Autocompletar y `packages.config` identificadores puede haber varios otra sesión de restauración debido a cómo el código se divide.

## <a name="authentication"></a>Autenticación

La autenticación se deja a la implementación de origen del paquete para definir. Para nuget.org, sólo el `PackagePublish` recurso requiere autenticación a través de un encabezado especial de clave de API. Consulte [ `PackagePublish` recursos](package-publish-resource.md) para obtener más información.
