---
title: Referencia de PowerShell de NuGet Find-Package | Documentos de Microsoft
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 6/1/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: Referencia de comandos de PowerShell de Find-Package en la consola de administrador de paquetes de NuGet en Visual Studio.
keywords: Consola de administrador, comandos de NuGet Powershell, referencia de NuGet Powershell, Find-Package de paquete de NuGet
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 4303421c5f11177f3e5fc051a450934df47ab117
ms.sourcegitcommit: 7969f6cd94eccfee5b62031bb404422139ccc383
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/20/2018
---
# <a name="find-package-package-manager-console-in-visual-studio"></a>Find-Package (consola de administrador de paquetes en Visual Studio)

*Versión 3.0 +; Este tema describe el comando dentro de la [NuGet Package Manager Console](package-manager-console.md) en Visual Studio en Windows. Para el comando de PowerShell Find-Package genérico, vea la [referencia de PowerShell PackageManagement](/powershell/module/packagemanagement/?view=powershell-6).*

Obtiene el conjunto de paquetes remotos con especificado Id. o palabras clave del origen del paquete.

## <a name="syntax"></a>Sintaxis

```ps
Find-Package [-Id] <keywords> -Source <string> [-AllVersions] [-First [<int>]]
    [-Skip <int>] [-IncludePrerelease] [-ExactMatch] [-StartWith] [<CommonParameters>]
```

## <a name="parameters"></a>Parámetros

| Parámetro | Descripción |
| --- | --- |
| Id. de &lt;palabras clave&gt; | (Obligatorio) Palabras clave que se usará al buscar el origen del paquete. Utilice - ExactMatch para devolver solo los paquetes cuyo Id. de paquete coincide con las palabras clave. Si no se especifica ninguna palabra clave, `Find-Package` devuelve una lista de los primeros 20 paquetes descargas o el número especificada por - primero. Tenga en cuenta que - Id. es opcional y una operación inefectiva. |
| Origen | La ruta de acceso URL o una carpeta de origen del paquete para buscar. Las rutas de acceso de la carpeta local pueden ser absoluta o relativa a la carpeta actual. Si se omite, `Find-Package` busca en el origen del paquete seleccionado. |
| AllVersions | Muestra todas las versiones disponibles de cada paquete en lugar de solo la versión más reciente. |
| First | El número de paquetes que se va a devolver desde el principio de la lista; el valor predeterminado es 20. |
| Skip | Omite la primera &lt;int&gt; paquetes en la lista mostrada.  |
| IncludePrerelease | Incluye paquetes de versión preliminar en los resultados. |
| ExactMatch | Especificado para usar &lt;palabras clave&gt; como un identificador del paquete distingue mayúsculas de minúsculas. |
| StartWith | Devuelve paquetes cuyo paquete identificador comienza con &lt;palabras clave&gt;. |

Ninguno de estos parámetros aceptan caracteres de entrada o el carácter comodín de canalización.

## <a name="common-parameters"></a>Parámetros comunes

`Find-Package` admite las siguientes [parámetros comunes de PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): depuración, acción de Error, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, detallado, WarningAction y WarningVariable.

## <a name="examples"></a>Ejemplos

```ps
# Find packages containing keywords
Find-Package elmah
Find-Package logging

# List packages whose ID begins with Elmah
Find-Package Elmah -StartWith

# By default, Get-Package returns a list of 20 packages; use -First to show more
Find-Package logging -First 100

# List all versions of the package with the ID of "jquery"
Find-Package jquery -AllVersions -ExactMatch
```