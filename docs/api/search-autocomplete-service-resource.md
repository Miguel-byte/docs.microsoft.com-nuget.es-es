---
title: Autocompletar, API de NuGet
description: El servicio de búsqueda de Autocompletar es compatible con las versiones y la detección interactiva de los identificadores de paquete.
author: joelverhagen
ms.author: jver
ms.date: 10/26/2017
ms.topic: reference
ms.reviewer: kraigb
ms.openlocfilehash: fdc3ad8aa239a42d8a4c169a757715e856bdcb41
ms.sourcegitcommit: 573af6133a39601136181c1d98c09303f51a1ab2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "58911054"
---
# <a name="autocomplete"></a>Autocompletar

Es posible crear una experiencia paquete ID y version Autocompletar mediante la API de V3. El recurso que se usa para realizar consultas de Autocompletar es el `SearchAutocompleteService` encontrar el recurso en el [índice de servicio](service-index.md).

## <a name="versioning"></a>Control de versiones

La siguiente `@type` se usan los valores:

Valor de@type                           | Notas
------------------------------------ | -----
SearchAutocompleteService            | La versión inicial
SearchAutocompleteService/3.0.0-beta | Alias de `SearchAutocompleteService`
SearchAutocompleteService/3.0.0-rc   | Alias de `SearchAutocompleteService`

## <a name="base-url"></a>Dirección URL base

La dirección URL base para las siguientes API es el valor de la `@id` propiedad asociada con uno de los recursos mencionados anteriormente `@type` valores. En el siguiente documento, la dirección URL base del marcador de posición `{@id}` se usará.

## <a name="http-methods"></a>Métodos HTTP

Todas las direcciones URL se encuentra en la compatibilidad con recursos de registro de los métodos HTTP `GET` y `HEAD`.

## <a name="search-for-package-ids"></a>Busque los identificadores de paquete

La primera API de Autocompletar admite la búsqueda de la parte de una cadena de identificador de paquete. Esto es fantástico cuando desee proporcionar una característica de escritura anticipada del paquete en una interfaz de usuario integrada con un origen del paquete NuGet.

Un paquete con solo las versiones no enumeradas no aparecerán en los resultados.

    GET {@id}?q={QUERY}&skip={SKIP}&take={TAKE}&prerelease={PRERELEASE}&semVerLevel={SEMVERLEVEL}

### <a name="request-parameters"></a>Parámetros de solicitud

Name        | En     | Tipo    | Obligatorio | Notas
----------- | ------ | ------- | -------- | -----
q           | Resolución    | cadena  | No       | La cadena para comparar los identificadores de paquete
skip        | Resolución    | enteros | No       | El número de resultados que se omitirán para la paginación
Take        | Resolución    | enteros | No       | El número de resultados que se va a devolver para la paginación
versión preliminar  | Resolución    | booleano | No       | `true` o `false` determinar si se debe incluir [paquetes de versión preliminar](../create-packages/prerelease-packages.md)
semVerLevel | Resolución    | cadena  | No       | Una cadena de versión 1.0.0 de SemVer 

La consulta de Autocompletar `q` se analiza de manera que se define mediante la implementación del servidor. NuGet.org admite las consultas para el prefijo de los tokens de identificador de paquete, que son partes de identificador generados por división original por caracteres camel de caso y símbolos.

El `skip` parámetro el valor predeterminado es 0.

El `take` parámetro debe ser un entero mayor que cero. La implementación del servidor puede imponer un valor máximo.

Si `prerelease` no es siempre se excluyen los paquetes de versión preliminar.

El `semVerLevel` parámetro de consulta se utiliza para participar en [SemVer 2.0.0 paquetes](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29#identifying-semver-v200-packages).
Si se excluye de este parámetro de consulta, se devolverán solo los identificadores de paquete con las versiones compatibles de SemVer 1.0.0 (con el [control de versiones de NuGet estándar](../reference/package-versioning.md) advertencias, tales como las cadenas de versión con 4 partes entero).
Si `semVerLevel=2.0.0` es siempre se devolverá SemVer 1.0.0 y 2.0.0 de SemVer compatibles paquetes. Consulte la [compatibilidad con SemVer 2.0.0 nuget.org](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29) para obtener más información.

### <a name="response"></a>Respuesta

La respuesta es un documento JSON que contiene hasta `take` Autocompletar resultados.

El objeto JSON de raíz tiene las siguientes propiedades:

Name      | Tipo             | Obligatorio | Notas
--------- | ---------------- | -------- | -----
totalHits | enteros          | sí      | El número total de coincidencias, omitiendo `skip` y `take`
datos      | matriz de cadenas | sí      | El paquete de identificadores que coinciden con la solicitud

### <a name="sample-request"></a>Solicitud de ejemplo

    GET https://api-v2v3search-0.nuget.org/autocomplete?q=storage&prerelease=true

### <a name="sample-response"></a>Respuesta de ejemplo

[!code-JSON [autocomplete-id-result.json](./_data/autocomplete-id-result.json)]

## <a name="enumerate-package-versions"></a>Enumerar versiones de paquetes

Una vez que se detecta un identificador de paquete mediante la API anterior, un cliente puede utilizar la API de Autocompletar para enumerar las versiones del paquete para un identificador de paquete proporcionado.

No aparecerá en los resultados de una versión del paquete que se da de baja.

    GET {@id}?id={ID}&prerelease={PRERELEASE}&semVerLevel={SEMVERLEVEL}

### <a name="request-parameters"></a>Parámetros de solicitud

Name        | En     | Tipo    | Obligatorio | Notas
----------- | ------ | ------- | -------- | -----
id          | Resolución    | cadena  | sí      | El identificador del paquete para capturar las versiones de
versión preliminar  | Resolución    | booleano | No       | `true` o `false` determinar si se debe incluir [paquetes de versión preliminar](../create-packages/prerelease-packages.md)
semVerLevel | Resolución    | cadena  | No       | Una cadena de versión 2.0.0 de SemVer 

Si `prerelease` no es siempre se excluyen los paquetes de versión preliminar.

El `semVerLevel` parámetro de consulta se utiliza para participar en los paquetes de SemVer 2.0.0. Si se excluye de este parámetro de consulta, se devolverá solo las versiones de SemVer 1.0.0. Si `semVerLevel=2.0.0` es siempre SemVer 1.0.0 y 2.0.0 de SemVer versiones se devolverá. Consulte la [compatibilidad con SemVer 2.0.0 nuget.org](https://github.com/NuGet/Home/wiki/SemVer2-support-for-nuget.org-%28server-side%29) para obtener más información.

### <a name="response"></a>Respuesta

La respuesta es el documento JSON que contiene todas las versiones de paquete del identificador del paquete proporcionado, filtrado por los parámetros de consulta determinada.

El objeto JSON de raíz tiene la siguiente propiedad:

Name      | Tipo             | Obligatorio | Notas
--------- | ---------------- | -------- | -----
datos      | matriz de cadenas | sí      | Las versiones del paquete coincide con la solicitud

Las versiones del paquete en el `data` matriz puede contener metadatos de la compilación de SemVer 2.0.0 (por ejemplo, `1.0.0+metadata`) si el `semVerLevel=2.0.0` se proporciona en la cadena de consulta.

### <a name="sample-request"></a>Solicitud de ejemplo

    GET https://api-v2v3search-0.nuget.org/autocomplete?id=nuget.protocol&prerelease=true

### <a name="sample-response"></a>Respuesta de ejemplo

[!code-JSON [autocomplete-version-result.json](./_data/autocomplete-version-result.json)]
