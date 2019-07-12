---
title: Referencia de PowerShell de NuGet Uninstall-Package
description: Referencia de comandos de PowerShell Uninstall-Package en la consola de administrador de paquetes de NuGet en Visual Studio.
author: karann-msft
ms.author: karann
ms.date: 06/01/2017
ms.topic: reference
ms.openlocfilehash: c95479103be2cba3b4eb6964ea761870477863bd
ms.sourcegitcommit: 0dea3b153ef823230a9d5f38351b7cef057cb299
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "67842475"
---
# <a name="uninstall-package-package-manager-console-in-visual-studio"></a><span data-ttu-id="ef7f0-103">Uninstall-Package (Consola del Administrador de paquetes en Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="ef7f0-103">Uninstall-Package (Package Manager Console in Visual Studio)</span></span>

<span data-ttu-id="ef7f0-104">*Este tema describe el comando dentro de la [Package Manager Console](package-manager-console.md) en Visual Studio en Windows. El comando de PowerShell Uninstall-Package genérico, vea el [referencia de PowerShell PackageManagement](/powershell/module/packagemanagement/?view=powershell-6).*</span><span class="sxs-lookup"><span data-stu-id="ef7f0-104">*This topic describes the command within the [Package Manager Console](package-manager-console.md) in Visual Studio on Windows. For the generic PowerShell Uninstall-Package command, see the [PowerShell PackageManagement reference](/powershell/module/packagemanagement/?view=powershell-6).*</span></span>

<span data-ttu-id="ef7f0-105">Quita un paquete desde un proyecto, quitar, opcionalmente, sus dependencias.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-105">Removes a package from a project, optionally removing its dependencies.</span></span> <span data-ttu-id="ef7f0-106">Si otros paquetes dependen de este paquete, el comando fallará a menos que – Force se especifica la opción.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-106">If other packages depend on this package, the command will fail unless the –Force option is specified.</span></span>

## <a name="syntax"></a><span data-ttu-id="ef7f0-107">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="ef7f0-107">Syntax</span></span>

```ps
Uninstall-Package [-Id] <string> [-RemoveDependencies] [-ProjectName <string>] [-Force]
    [-Version <string>] [-WhatIf] [<CommonParameters>]
```

<span data-ttu-id="ef7f0-108">Si otros paquetes dependen de este paquete, el comando fallará a menos que – Force se especifica la opción.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-108">If other packages depend on this package, the command will fail unless the –Force option is specified.</span></span>

## <a name="parameters"></a><span data-ttu-id="ef7f0-109">Parámetros</span><span class="sxs-lookup"><span data-stu-id="ef7f0-109">Parameters</span></span>

| <span data-ttu-id="ef7f0-110">Parámetro</span><span class="sxs-lookup"><span data-stu-id="ef7f0-110">Parameter</span></span> | <span data-ttu-id="ef7f0-111">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="ef7f0-111">Description</span></span> |
| --- | --- |
| <span data-ttu-id="ef7f0-112">Id</span><span class="sxs-lookup"><span data-stu-id="ef7f0-112">Id</span></span> | <span data-ttu-id="ef7f0-113">(Obligatorio) El identificador del paquete para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-113">(Required) The identifier of the package to uninstall.</span></span> <span data-ttu-id="ef7f0-114">-Identificador propio conmutador es opcional.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-114">The -Id switch itself is optional.</span></span> |
| <span data-ttu-id="ef7f0-115">`Version`</span><span class="sxs-lookup"><span data-stu-id="ef7f0-115">Version</span></span> | <span data-ttu-id="ef7f0-116">La versión del paquete para desinstalar, la versión actualmente instalada de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-116">The version of the package to uninstall, defaulting to the currently installed version.</span></span> |
| <span data-ttu-id="ef7f0-117">RemoveDependencies</span><span class="sxs-lookup"><span data-stu-id="ef7f0-117">RemoveDependencies</span></span> | <span data-ttu-id="ef7f0-118">Desinstale el paquete y sus dependencias no usadas.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-118">Uninstall the package and its unused dependencies.</span></span> <span data-ttu-id="ef7f0-119">Es decir, si una dependencia tiene otro paquete que depende de él, se omitirá.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-119">That is, if any dependency has another package that depends on it, it's skipped.</span></span> |
| <span data-ttu-id="ef7f0-120">NombreDelProyecto</span><span class="sxs-lookup"><span data-stu-id="ef7f0-120">ProjectName</span></span> | <span data-ttu-id="ef7f0-121">El proyecto desde el que se va a desinstalar el paquete, de forma predeterminada el proyecto predeterminado.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-121">The project from which to uninstall the package, defaulting to the default project.</span></span> |
| <span data-ttu-id="ef7f0-122">Force</span><span class="sxs-lookup"><span data-stu-id="ef7f0-122">Force</span></span> | <span data-ttu-id="ef7f0-123">Fuerza un paquete que se desinstalara, incluso si otros paquetes dependen de él.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-123">Forces a package to be uninstalled, even if other packages depend on it.</span></span> |
| <span data-ttu-id="ef7f0-124">WhatIf</span><span class="sxs-lookup"><span data-stu-id="ef7f0-124">WhatIf</span></span> | <span data-ttu-id="ef7f0-125">Muestra lo que sucedería cuando ejecute el comando sin tener que realizar la desinstalación.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-125">Shows what would happen when running the command without actually performing the uninstall.</span></span> |

<span data-ttu-id="ef7f0-126">Ninguno de estos parámetros aceptan caracteres comodín o de entrada de canalización.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-126">None of these parameters accept pipeline input or wildcard characters.</span></span>

## <a name="common-parameters"></a><span data-ttu-id="ef7f0-127">Parámetros comunes</span><span class="sxs-lookup"><span data-stu-id="ef7f0-127">Common Parameters</span></span>

<span data-ttu-id="ef7f0-128">`Uninstall-Package` admite las siguientes [parámetros comunes de PowerShell](http://go.microsoft.com/fwlink/?LinkID=113216): Depuración, acción del Error, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, detallado, WarningAction y WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ef7f0-128">`Uninstall-Package` supports the following [common PowerShell parameters](http://go.microsoft.com/fwlink/?LinkID=113216): Debug, Error Action, ErrorVariable, OutBuffer, OutVariable, PipelineVariable, Verbose, WarningAction, and WarningVariable.</span></span>

## <a name="examples"></a><span data-ttu-id="ef7f0-129">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="ef7f0-129">Examples</span></span>

```ps
# Uninstalls the Elmah package from the default project
Uninstall-Package Elmah

# Uninstalls the Elmah package and all its unused dependencies
Uninstall-Package Elmah -RemoveDependencies 

# Uninstalls the Elmah package even if another package depends on it
Uninstall-Package Elmah -Force
```
