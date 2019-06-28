---
title: Comando de actualización de la CLI de NuGet
description: Referencia del comando de actualización de nuget.exe
author: karann-msft
ms.author: karann
ms.date: 12/07/2017
ms.topic: reference
ms.openlocfilehash: a242d02a54fd86899cbe274ab63538b53307c1bb
ms.sourcegitcommit: b6810860b77b2d50aab031040b047c20a333aca3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425914"
---
# <a name="update-command-nuget-cli"></a>Comando update (CLI de NuGet)

**Se aplica a:** consumo de paquetes &bullet; **versiones compatibles:** todas

Actualiza todos los paquetes en un proyecto (mediante `packages.config`) a sus versiones más recientes. Se recomienda ejecutar ['restore'](cli-ref-restore.md) antes de ejecutar el `update`. (Para actualizar un paquete individual, use [ `nuget install` ](cli-ref-install.md) sin especificar un número de versión, en el que caso NuGet instala la versión más reciente.)

Nota: `update` no funciona con la CLI que se ejecuta en Mono (Mac OSX o Linux) o cuando se usa el formato PackageReference.

El `update` comando también actualiza las referencias de ensamblado en el archivo de proyecto, siempre que los que hace referencia ya existe. Si un paquete actualizado tiene un ensamblado se ha agregado, es una nueva referencia *no* agregado. También nuevas dependencias de paquete no tienen sus referencias de ensamblado agregados. Para incluir estas operaciones como parte de una actualización, actualice el paquete en Visual Studio mediante la UI de administrador de paquetes o la consola de administrador de paquetes.

Este comando también se puede usar para actualizar nuget.exe propio mediante el *-self* marca.

## <a name="usage"></a>Uso

```cli
nuget update <configPath> [options]
```

donde `<configPath>` identifica ya sea un `packages.config` o archivo de solución que se enumera las dependencias del proyecto.

## <a name="options"></a>Opciones

| Opción | Descripción |
| --- | --- |
| ConfigFile | El archivo de configuración para aplicar. Si no se especifica, `%AppData%\NuGet\NuGet.Config` (Windows) o `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) se utiliza.|
| FileConflictAction | Especifica la acción que se realizará cuando se le pida sobrescribir u omitir los archivos existentes que se hace referencia el proyecto. Los valores son *sobrescribir, omitir ninguno*. |
| ForceEnglishOutput | *(3.5 y versiones posteriores)*  Fuerza nuget.exe se ejecute con una referencia cultural invariable, en inglés. |
| Help | Muestra información de ayuda para el comando. |
| Id. | Especifica una lista de identificadores para la actualización del paquete. |
| MSBuildPath | *(4.0 y versiones posteriores)*  Especifica la ruta de acceso de MSBuild que use con el comando, tiene prioridad sobre `-MSBuildVersion`. |
| MSBuildVersion | *(3.2 y versiones posteriores)*  Especifica la versión de MSBuild que se usará con este comando. Los valores admitidos son 4, 12, 14, 15.1, versión 15.3, 15.4, 15.5, versión 15.6, versión 15.7, 15,8, 15.9. De forma predeterminada que se selecciona la versión de MSBuild en su ruta de acceso, en caso contrario, el valor predeterminado es la última versión instalada de MSBuild. |
| NonInteractive | Suprime los mensajes para confirmaciones o intervención del usuario. |
| Versión preliminar | Permite la actualización a las versiones preliminares. Esta marca no es necesaria al actualizar paquetes de versión preliminar que ya están instalados. |
| RepositoryPath | Especifica la carpeta local donde están instalados los paquetes. |
| Safe | Especifica que sólo actualiza con la versión más alta disponible dentro de la misma versión principal y secundaria que se instalará el paquete instalado. |
| Self | Nuget.exe actualizaciones a la versión más reciente; todos los demás argumentos se pasan por alto. |
| Source | Especifica la lista de orígenes de paquetes (como las direcciones URL) para las actualizaciones. Si se omite, el comando usa los orígenes proporcionados en los archivos de configuración, consulte [configuraciones comunes NuGet](../consume-packages/configuring-nuget-behavior.md). |
| Verbosity | Especifica la cantidad de detalle que se muestra en la salida: *normal*, *quiet*, *detallada*. |
| Versión | Cuando se usa con un Id. de paquete, especifica la versión del paquete para actualizar. |

Consulte también [variables de entorno](cli-ref-environment-variables.md)

## <a name="examples"></a>Ejemplos

```cli
nuget update

# update packages installed in solution.sln, using MSBuild version 14.0 to load the solution and its project(s).
nuget update solution.sln -MSBuildVersion 14

nuget update -safe

nuget update -self
```
