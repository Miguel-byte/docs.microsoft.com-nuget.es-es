---
title: Notas de la versión de NuGet 5,3
description: Notas de la versión de NuGet 5,3, incluidas nuevas características, correcciones de errores y DCR.
author: karann-msft
ms.author: karann
ms.date: 09/06/2019
ms.topic: conceptual
ms.openlocfilehash: 683ee7d1bef30d0a7414ec1694a9735d79b2ab45
ms.sourcegitcommit: c529f5944868a0692ca8550b716a73e05df0ccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71687890"
---
# <a name="nuget-53-release-notes"></a>Notas de la versión de NuGet 5,3

Vehículos de distribución de NuGet:

| Versión de NuGet | Disponible en la versión de Visual Studio| Disponible en los SDK de .NET|
|:---|:---|:---|
| [**5.3.0**](https://nuget.org/downloads) | [Visual Studio 2019 versión 16,3](https://visualstudio.microsoft.com/downloads/) | [3.0.100](https://dotnet.microsoft.com/download/dotnet-core/3.0) <sup>1</sup> |

<sup>1</sup> Instalado con Visual Studio 2019 con la carga de trabajo de .NET Core

## <a name="summary-whats-new-in-53"></a>Resumen: Novedades de 5,3

* [El icono de paquete se puede incrustar en el paquete](../reference/msbuild-targets.md#packing-an-icon-image-file), en lugar de tener una dirección URL externa. - [#352](https://github.com/NuGet/Home/issues/352)

* Seguridad mejorada con seguimiento y cumplimiento de SHA para packages. config- [#7281](https://github.com/NuGet/Home/issues/7281)

* Habilitar la degradación de paquetes de NuGet obsoletos/heredados [#2867](https://github.com/NuGet/Home/issues/2867)[entrada de blog](https://devblogs.microsoft.com/nuget/deprecating-packages-on-nuget-org/)de  |   | [documentos](https://docs.microsoft.com/en-us/nuget/nuget-org/deprecate-packages)

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión

**Errores**

* Los usuarios de 2,2 SDK no pueden usar los paquetes de NuGet generados con el SDK de 3.0.100-preview9... en función de la zona horaria [#8603](https://github.com/NuGet/Home/issues/8603)

* Los caracteres de Comillas en la ruta de acceso causan un error de `nuget restore` caracteres no válidos en la ruta de acceso en [#8168](https://github.com/NuGet/Home/issues/8168)

* VS: los ensamblados son totalmente Ngen-Ed no parcialmente Ngen-Ed- [#8513](https://github.com/NuGet/Home/issues/8513)

* Reducir el uso de memoria (cancelar la suscripción a eventos)- [#8471](https://github.com/NuGet/Home/issues/8471)

* El mensaje "Error_UnableToFindProjectInfo" no es gramaticalmente correcto [#8441](https://github.com/NuGet/Home/issues/8441)

* Mejoras de NU1403: validar todos los paquetes, incluir los valores Sha esperados/reales- [#8424](https://github.com/NuGet/Home/issues/8424)

* Enumeración múltiple `NuGetPackageManager.PreviewUpdatePackagesAsync`en  -  [#8401](https://github.com/NuGet/Home/issues/8401)

* Revertir el cambio de "público > interno" en PluginProcess- [#8390](https://github.com/NuGet/Home/issues/8390)

* IVsPackageSourceProvider. GetSources (...) tiene un comportamiento de excepción mal definido: [#8383](https://github.com/NuGet/Home/issues/8383)

* Volver a convertir el constructor de PluginManager en público [#8379](https://github.com/NuGet/Home/issues/8379)

* Métricas para realizar el seguimiento de la frecuencia de actualización de la interfaz de usuario de PM- [#8369](https://github.com/NuGet/Home/issues/8369)

* Reducir el número de actualizaciones de la interfaz de usuario al instalar a través de la interfaz de usuario del administrador de paquetes- [#8358](https://github.com/NuGet/Home/issues/8358)

* Telemetría: los valores de fecha y hora usan formatos específicos de la referencia cultural: [#8351](https://github.com/NuGet/Home/issues/8351)

* Reducir las actualizaciones de la interfaz de usuario en la pestaña examinar de la interfaz de usuario del administrador de paquetes #6570- [#8339](https://github.com/NuGet/Home/issues/8339)

* [Error de prueba] "No se puede analizar el archivo de configuración" se preguntará dos veces [#8320](https://github.com/NuGet/Home/issues/8320)

* Generar un error NU5037 con una página de documentos buena que explique las correcciones de los clientes (el paquete no tiene el archivo nuspec necesario)- [#8291](https://github.com/NuGet/Home/issues/8291)

* Se produce un error en la restauración en modo bloqueado cuando se cambia el RuntimeIdentifier de un proyecto- [#8260](https://github.com/NuGet/Home/issues/8260)

* Hacer que la configuración sea leída en VS Lazy- [#8156](https://github.com/NuGet/Home/issues/8156)

* La regresión `Nuget sources add` en causa "el carácter ': ', el valor hexadecimal 0x3A, no se puede incluir en un nombre" Errors- [#7948](https://github.com/NuGet/Home/issues/7948)

* Proveedores de credenciales de complemento NuGet: ocultar la ventana de proceso- [#7511](https://github.com/NuGet/Home/issues/7511)

* Aplicar PackagePathResolver es una ruta de acceso absoluta [#7349](https://github.com/NuGet/Home/issues/7349)

* Reducir las actualizaciones de la interfaz de usuario en las pestañas instalar y actualizar de la interfaz de usuario del administrador de paquetes- [#6570](https://github.com/NuGet/Home/issues/6570)

**DCR:**

* Actualización de los marcos de Xamarin para asignarlos a NetStandard 2,1- [#8368](https://github.com/NuGet/Home/issues/8368)

* Habilitar la copia del contenido del administrador de paquetes "ventana de vista previa" para instalar/actualizar- [#8324](https://github.com/NuGet/Home/issues/8324)

* Habilitar restauración en archivos. proj: [#8212](https://github.com/NuGet/Home/issues/8212)

* Introducir `NUGET_NETFX_PLUGIN_PATHS` y`NUGET_NETCORE_PLUGIN_PATHS` para admitir la configuración de ambos al mismo tiempo: [#8151](https://github.com/NuGet/Home/issues/8151)

* Habilitación de varias versiones para un PackageDownload mediante el atributo de versión: [#8074](https://github.com/NuGet/Home/issues/8074)

* Opciones Add-SolutionDirectory y-PackageDirectory para el paquete Nuget. exe- [#7163](https://github.com/NuGet/Home/issues/7163)

**[Lista de todos los problemas corregidos en esta versión: 5,3](https://github.com/nuget/home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%225.3")**
