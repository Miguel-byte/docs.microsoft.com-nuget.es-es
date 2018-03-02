---
title: "Referencia de errores y advertencias de restauración de NuGet | Documentos de Microsoft"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 12/13/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
description: "Referencia completa para las advertencias y errores emitidos de NuGet durante la restauración del paquete"
keywords: "NuGet errores y advertencias de NuGet, diagnóstico"
ms.reviewer:
- anangaur
- karann-msft
- unniravindranathan
f1_keywords:
- NU1000
- NU1001
- NU1002
- NU1003
- NU1100
- NU1101
- NU1102
- NU1103
- NU1104
- NU1105
- NU1106
- NU1107
- NU1108
- NU1201
- NU1202
- NU1203
- NU1401
- NU1500
- NU1501
- NU1502
- NU1503
- NU1601
- NU1602
- NU1603
- NU1604
- NU1605
- NU1608
- NU1701
- NU1801
ms.openlocfilehash: c7d77af04744888ce8af92d617a2ffc7daef4eb0
ms.sourcegitcommit: 262d026beeffd4f3b6fc47d780a2f701451663a8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="errors-and-warnings"></a><span data-ttu-id="f60ec-104">Errores y advertencias</span><span class="sxs-lookup"><span data-stu-id="f60ec-104">Errors and warnings</span></span>

<span data-ttu-id="f60ec-105">En NuGet 4.3.0, errores y advertencias se numeran como se describe en este tema y proporcionan información detallada para ayudarle a solucionar los problemas que conlleva.</span><span class="sxs-lookup"><span data-stu-id="f60ec-105">In NuGet 4.3.0, errors and warnings are numbered as described in this topic and provide detailed information to help you address the issues involved.</span></span> 

<span data-ttu-id="f60ec-106">Los errores y advertencias que se indican aquí sólo están disponibles con [PackageReference-based](../Consume-Packages/Package-References-in-Project-Files.md) NuGet 4.3.0 y proyectos.</span><span class="sxs-lookup"><span data-stu-id="f60ec-106">The errors and warnings listed here are available only with [PackageReference-based](../Consume-Packages/Package-References-in-Project-Files.md) projects and NuGet 4.3.0.</span></span> <span data-ttu-id="f60ec-107">NuGet también respeta las propiedades de MSBuild para suprimir las advertencias o elevar los privilegios a errores.</span><span class="sxs-lookup"><span data-stu-id="f60ec-107">NuGet also honors MSBuild properties to suppress warnings or elevate them to errors.</span></span> <span data-ttu-id="f60ec-108">Para obtener más información, consulte [Cómo: Suprimir advertencias del compilador](/visualstudio/ide/how-to-suppress-compiler-warnings) en la documentación de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f60ec-108">For more information, see [How to: Suppress Compiler Warnings](/visualstudio/ide/how-to-suppress-compiler-warnings) in the Visual Studio documentation.</span></span>

<span data-ttu-id="f60ec-109">**Errors**</span><span class="sxs-lookup"><span data-stu-id="f60ec-109">**Errors**</span></span>

| <span data-ttu-id="f60ec-110">Agrupar</span><span class="sxs-lookup"><span data-stu-id="f60ec-110">Group</span></span> | <span data-ttu-id="f60ec-111">Números de error</span><span class="sxs-lookup"><span data-stu-id="f60ec-111">Error Numbers</span></span> |
| --- | --- |
| [<span data-ttu-id="f60ec-112">Errores de entrada no válidos</span><span class="sxs-lookup"><span data-stu-id="f60ec-112">Invalid input errors</span></span>](#invalid-input-errors) | <span data-ttu-id="f60ec-113">[NU1001](#nu1001), [NU1002](#nu1002), [NU1003](#nu1003)</span><span class="sxs-lookup"><span data-stu-id="f60ec-113">[NU1001](#nu1001), [NU1002](#nu1002), [NU1003](#nu1003)</span></span> |
| [<span data-ttu-id="f60ec-114">Errores de paquete y proyecto ausente</span><span class="sxs-lookup"><span data-stu-id="f60ec-114">Missing package and project errors</span></span>](#missing-package-and-project-errors) | <span data-ttu-id="f60ec-115">[NU1100](#nu1100), [NU1101](#nu1101), [NU1102](#nu1102), [NU1103](#nu1103), [NU1104](#nu1104), [NU1105](#nu1105), [ NU1106](#nu1106), [NU1107](#nu1107) (anteriormente NU1607), [NU1108](#nu1108) (anteriormente NU1606)</span><span class="sxs-lookup"><span data-stu-id="f60ec-115">[NU1100](#nu1100), [NU1101](#nu1101), [NU1102](#nu1102), [NU1103](#nu1103), [NU1104](#nu1104), [NU1105](#nu1105), [NU1106](#nu1106), [NU1107](#nu1107) (previously NU1607), [NU1108](#nu1108) (previously NU1606)</span></span> |
| [<span data-ttu-id="f60ec-116">Errores de compatibilidad</span><span class="sxs-lookup"><span data-stu-id="f60ec-116">Compatibility errors</span></span>](#compatibility-errors) | <span data-ttu-id="f60ec-117">[NU1201](#nu1201), [NU1202](#nu1202), [NU1203](#nu1203), [NU1401](#nu1401)</span><span class="sxs-lookup"><span data-stu-id="f60ec-117">[NU1201](#nu1201), [NU1202](#nu1202), [NU1203](#nu1203), [NU1401](#nu1401)</span></span> |

<span data-ttu-id="f60ec-118">**Advertencias**</span><span class="sxs-lookup"><span data-stu-id="f60ec-118">**Warnings**</span></span>

| <span data-ttu-id="f60ec-119">Agrupar</span><span class="sxs-lookup"><span data-stu-id="f60ec-119">Group</span></span> | <span data-ttu-id="f60ec-120">Números de advertencia</span><span class="sxs-lookup"><span data-stu-id="f60ec-120">Warning numbers</span></span> |
| --- | --- |
| [<span data-ttu-id="f60ec-121">Advertencias de entrada no válidas</span><span class="sxs-lookup"><span data-stu-id="f60ec-121">Invalid input warnings</span></span>](#invalid-input-warnings) | <span data-ttu-id="f60ec-122">[NU1501](#nu1501), [NU1502](#nu1502), [NU1503](#nu1503)</span><span class="sxs-lookup"><span data-stu-id="f60ec-122">[NU1501](#nu1501), [NU1502](#nu1502), [NU1503](#nu1503)</span></span> |
| [<span data-ttu-id="f60ec-123">Advertencias de la versión de paquete inesperado</span><span class="sxs-lookup"><span data-stu-id="f60ec-123">Unexpected package version warnings</span></span>](#unexpected-package-version-warnings) | <span data-ttu-id="f60ec-124">[NU1601](#nu1601), [NU1602](#nu1602), [NU1603](#nu1603), [NU1604](#nu1604), [NU1605](#nu1605)</span><span class="sxs-lookup"><span data-stu-id="f60ec-124">[NU1601](#nu1601), [NU1602](#nu1602), [NU1603](#nu1603), [NU1604](#nu1604), [NU1605](#nu1605)</span></span> |
| [<span data-ttu-id="f60ec-125">Advertencias de conflicto de resolución</span><span class="sxs-lookup"><span data-stu-id="f60ec-125">Resolver conflict warnings</span></span>](#resolver-conflict-warnings) | [<span data-ttu-id="f60ec-126">NU1608</span><span class="sxs-lookup"><span data-stu-id="f60ec-126">NU1608</span></span>](#nu1608) |
| [<span data-ttu-id="f60ec-127">Advertencias de reserva de paquete</span><span class="sxs-lookup"><span data-stu-id="f60ec-127">Package fallback warnings</span></span>](#package-fallback-warnings) | [<span data-ttu-id="f60ec-128">NU1701</span><span class="sxs-lookup"><span data-stu-id="f60ec-128">NU1701</span></span>](#nu1701) |
| [<span data-ttu-id="f60ec-129">Advertencias de fuentes</span><span class="sxs-lookup"><span data-stu-id="f60ec-129">Feed warnings</span></span>](#feed-warnings) | [<span data-ttu-id="f60ec-130">NU1801</span><span class="sxs-lookup"><span data-stu-id="f60ec-130">NU1801</span></span>](#nu1801) |
| [<span data-ttu-id="f60ec-131">Las advertencias y errores internos de NuGet</span><span class="sxs-lookup"><span data-stu-id="f60ec-131">NuGet internal errors and warnings</span></span>](#nuget-internal-errors-and-warnings) | <span data-ttu-id="f60ec-132">[NU1000](#nu1000), [NU1500](#nu1500)</span><span class="sxs-lookup"><span data-stu-id="f60ec-132">[NU1000](#nu1000), [NU1500](#nu1500)</span></span> |

## <a name="invalid-input-errors"></a><span data-ttu-id="f60ec-133">Errores de entrada no válidos</span><span class="sxs-lookup"><span data-stu-id="f60ec-133">Invalid input errors</span></span>

<span data-ttu-id="f60ec-134">[NU1001](#nu1001) | [NU1002](#nu1002) | [NU1003](#nu1003)</span><span class="sxs-lookup"><span data-stu-id="f60ec-134">[NU1001](#nu1001) | [NU1002](#nu1002) | [NU1003](#nu1003)</span></span>

### <a name="nu1001"></a><span data-ttu-id="f60ec-135">NU1001</span><span class="sxs-lookup"><span data-stu-id="f60ec-135">NU1001</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-136">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-136">**Issue**</span></span> | <span data-ttu-id="f60ec-137">El proyecto no contiene uno o varios marcos de trabajo.</span><span class="sxs-lookup"><span data-stu-id="f60ec-137">The project doesn't contain one or more frameworks.</span></span> |
| <span data-ttu-id="f60ec-138">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-138">**Common causes**</span></span> | <span data-ttu-id="f60ec-139">El proyecto no contiene un `TargetFramework` o `TargetFrameworks` propiedad.</span><span class="sxs-lookup"><span data-stu-id="f60ec-139">The project doesn't contain a `TargetFramework` or `TargetFrameworks` property.</span></span> |
| <span data-ttu-id="f60ec-140">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-140">**Example message**</span></span> | <span data-ttu-id="f60ec-141">*El proyecto projA no especifica ningún marco de destino en c:\tmp\projA.csproj*</span><span class="sxs-lookup"><span data-stu-id="f60ec-141">*The project projA does not specify any target frameworks in c:\tmp\projA.csproj*</span></span> |

### <a name="nu1002"></a><span data-ttu-id="f60ec-142">NU1002</span><span class="sxs-lookup"><span data-stu-id="f60ec-142">NU1002</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-143">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-143">**Issue**</span></span> | <span data-ttu-id="f60ec-144">Combinación no válida de entradas junto con una palabra clave clara.</span><span class="sxs-lookup"><span data-stu-id="f60ec-144">Invalid combination of inputs along with a CLEAR keyword.</span></span> |
| <span data-ttu-id="f60ec-145">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-145">**Common causes**</span></span> | <span data-ttu-id="f60ec-146">CLEAR no puede combinarse con otras entradas.</span><span class="sxs-lookup"><span data-stu-id="f60ec-146">CLEAR may not be combined with other inputs.</span></span> |
| <span data-ttu-id="f60ec-147">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-147">**Example message**</span></span> | <span data-ttu-id="f60ec-148">*'CLEAR' no se puede usar junto con otros valores*</span><span class="sxs-lookup"><span data-stu-id="f60ec-148">*'CLEAR' cannot be used in conjunction with other values*</span></span> |

### <a name="nu1003"></a><span data-ttu-id="f60ec-149">NU1003</span><span class="sxs-lookup"><span data-stu-id="f60ec-149">NU1003</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-150">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-150">**Issue**</span></span> | <span data-ttu-id="f60ec-151">`PackageTargetFallback`y `AssetTargetFallback` proporcionar un comportamiento diferente para la selección de activos y no pueden usarse juntos.</span><span class="sxs-lookup"><span data-stu-id="f60ec-151">`PackageTargetFallback` and `AssetTargetFallback` provide different behavior for selecting assets and cannot be used together.</span></span> |
| <span data-ttu-id="f60ec-152">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-152">**Common causes**</span></span> | <span data-ttu-id="f60ec-153">Ambos `PackageTargetFallback` y `AssetTargetFallback` existe en el proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-153">Both `PackageTargetFallback` and `AssetTargetFallback` exist in the project.</span></span> |
| <span data-ttu-id="f60ec-154">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-154">**Example message**</span></span> | <span data-ttu-id="f60ec-155">*PackageTargetFallback y AssetTargetFallback no pueden usarse juntos. Quite las referencias de PackageTargetFallback(deprecated) desde el entorno del proyecto.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-155">*PackageTargetFallback and AssetTargetFallback cannot be used together. Remove PackageTargetFallback(deprecated) references from the project environment.*</span></span> |

## <a name="missing-package-and-project-errors"></a><span data-ttu-id="f60ec-156">Errores de paquete y proyecto ausente</span><span class="sxs-lookup"><span data-stu-id="f60ec-156">Missing package and project errors</span></span>

<span data-ttu-id="f60ec-157">[NU1100](#nu1100) | [NU1101](#nu1101) | [NU1102](#nu1102) | [NU1103](#nu1103) | [NU1104](#nu1104) | [NU1105](#nu1105) | [NU1106](#nu1106)</span><span class="sxs-lookup"><span data-stu-id="f60ec-157">[NU1100](#nu1100) | [NU1101](#nu1101) | [NU1102](#nu1102) | [NU1103](#nu1103) | [NU1104](#nu1104) | [NU1105](#nu1105) | [NU1106](#nu1106)</span></span>

### <a name="nu1100"></a><span data-ttu-id="f60ec-158">NU1100</span><span class="sxs-lookup"><span data-stu-id="f60ec-158">NU1100</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-159">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-159">**Issue**</span></span> | <span data-ttu-id="f60ec-160">Un grupo de dependencia no puede resolver.</span><span class="sxs-lookup"><span data-stu-id="f60ec-160">A dependency group not be resolved.</span></span> <span data-ttu-id="f60ec-161">Se trata de un problema genérico para los tipos que no son paquetes o proyectos.</span><span class="sxs-lookup"><span data-stu-id="f60ec-161">This is a generic issue for types that are not packages or projects.</span></span> |
| <span data-ttu-id="f60ec-162">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-162">**Common causes**</span></span> | <span data-ttu-id="f60ec-163">El proyecto contiene una dependencia en un elemento que no existe.</span><span class="sxs-lookup"><span data-stu-id="f60ec-163">The project contains a dependency on an item that doesn't exist.</span></span> |
| <span data-ttu-id="f60ec-164">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-164">**Example message**</span></span> | <span data-ttu-id="f60ec-165">*No se puede resolver System.Missing para net45*</span><span class="sxs-lookup"><span data-stu-id="f60ec-165">*Unable to resolve System.Missing for net45*</span></span> |

### <a name="nu1101"></a><span data-ttu-id="f60ec-166">NU1101</span><span class="sxs-lookup"><span data-stu-id="f60ec-166">NU1101</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-167">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-167">**Issue**</span></span> | <span data-ttu-id="f60ec-168">El paquete no se encuentra en los orígenes.</span><span class="sxs-lookup"><span data-stu-id="f60ec-168">The package cannot be found on any sources.</span></span> |
| <span data-ttu-id="f60ec-169">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-169">**Common causes**</span></span> | <span data-ttu-id="f60ec-170">Falta el origen del paquete correcto o el identificador del paquete es incorrecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-170">The correct package source is missing or the package identifier is incorrect.</span></span> |
| <span data-ttu-id="f60ec-171">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-171">**Example message**</span></span> | <span data-ttu-id="f60ec-172">*No se puede encontrar el paquete System.Missing. Ningún paquete existe con este identificador en orígenes: core dotnet, dotnet roslyn, nuget.org*</span><span class="sxs-lookup"><span data-stu-id="f60ec-172">*Unable to find package System.Missing. No packages exist with this id in source(s): dotnet-core, dotnet-roslyn, nuget.org*</span></span> |

### <a name="nu1102"></a><span data-ttu-id="f60ec-173">NU1102</span><span class="sxs-lookup"><span data-stu-id="f60ec-173">NU1102</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-174">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-174">**Issue**</span></span> | <span data-ttu-id="f60ec-175">Se encontró el identificador de paquete pero no se encuentra una versión dentro del intervalo de dependencia especificado en cualquiera de los orígenes.</span><span class="sxs-lookup"><span data-stu-id="f60ec-175">The package identifier is found but a version within the specified dependency range cannot be found on any of the sources.</span></span> |
| <span data-ttu-id="f60ec-176">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-176">**Common causes**</span></span> | <span data-ttu-id="f60ec-177">Falta el origen del paquete correcto o el intervalo de dependencia es incorrecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-177">The correct package source is missing or the dependency range is incorrect.</span></span> <span data-ttu-id="f60ec-178">El intervalo puede especificarse mediante un paquete y no el usuario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-178">The range might be specified by a package and not the user.</span></span> <span data-ttu-id="f60ec-179">El usuario que necesite cambiar a una versión disponible si este paquete hace referencia directamente al proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-179">The user may need to switch to an available version if this package is referenced by the project directly.</span></span> |
| <span data-ttu-id="f60ec-180">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-180">**Example message**</span></span> | <span data-ttu-id="f60ec-181">*No se puede encontrar el paquete NuGet.Versioning con la versión (> = 9.0.1)<br/> -30 encontrar versiones en nuget.org [más cercano de la versión: 4.0.0]<br/> -10 encuentra versiones en dotnet buildtools [más cercano de la versión: 4.0.0-rc-2129]<br/> -encuentra 9 versiones en NuGetVolatile [más cercano de la versión: 3.0.0-beta-00032]<br/> -encontrar versiones 0 en dotnet core<br/> -encontrar versiones 0 en roslyn de dotnet.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-181">*Unable to find package NuGet.Versioning with version (>= 9.0.1)<br/>  - Found 30 version(s) in nuget.org [ Nearest version: 4.0.0 ]<br/>  - Found 10 version(s) in dotnet-buildtools [ Nearest version: 4.0.0-rc-2129 ]<br/>  - Found 9 version(s) in NuGetVolatile [ Nearest version: 3.0.0-beta-00032 ]<br/>  - Found 0 version(s) in dotnet-core<br/>  - Found 0 version(s) in dotnet-roslyn*</span></span> |

### <a name="nu1103"></a><span data-ttu-id="f60ec-182">NU1103</span><span class="sxs-lookup"><span data-stu-id="f60ec-182">NU1103</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-183">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-183">**Issue**</span></span> | <span data-ttu-id="f60ec-184">Se encontraron ninguna versión estable en el intervalo de dependencia.</span><span class="sxs-lookup"><span data-stu-id="f60ec-184">No stable versions were found in the dependency range.</span></span> <span data-ttu-id="f60ec-185">Se encontraron versiones preliminares, pero no se permiten.</span><span class="sxs-lookup"><span data-stu-id="f60ec-185">Pre-release versions were found but are not allowed.</span></span> |
| <span data-ttu-id="f60ec-186">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-186">**Common causes**</span></span> | <span data-ttu-id="f60ec-187">El proyecto especifica una versión estable para el intervalo de dependencia.</span><span class="sxs-lookup"><span data-stu-id="f60ec-187">The project specified a stable version for the dependency range.</span></span> <span data-ttu-id="f60ec-188">Los usuarios deben cambiar el intervalo de versiones para incluir versiones preliminares.</span><span class="sxs-lookup"><span data-stu-id="f60ec-188">Users need to change the version range to include pre-release versions.</span></span> |
| <span data-ttu-id="f60ec-189">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-189">**Example message**</span></span> | <span data-ttu-id="f60ec-190">*No se puede encontrar un paquete estable NuGet.Versioning con la versión (> = 3.0.0)<br/> -10 encuentra versiones en dotnet buildtools [más cercano de versión: 4.0.0-rc-2129]<br/> -versiones 9 se encuentra en NuGetVolatile [más cercano de versión: 3.0.0-beta-00032] <br/> -Encontrar versiones 0 en dotnet core<br/> -encontrar versiones 0 en roslyn de dotnet.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-190">*Unable to find a stable package NuGet.Versioning with version (>= 3.0.0)<br/>  - Found 10 version(s) in dotnet-buildtools [ Nearest version: 4.0.0-rc-2129 ]<br/>  - Found 9 version(s) in NuGetVolatile [ Nearest version: 3.0.0-beta-00032 ]<br/>  - Found 0 version(s) in dotnet-core<br/>  - Found 0 version(s) in dotnet-roslyn*</span></span> |

### <a name="nu1104"></a><span data-ttu-id="f60ec-191">NU1104</span><span class="sxs-lookup"><span data-stu-id="f60ec-191">NU1104</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-192">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-192">**Issue**</span></span> | <span data-ttu-id="f60ec-193">Un ProjectReference apunta a un archivo que no existe.</span><span class="sxs-lookup"><span data-stu-id="f60ec-193">A ProjectReference points to a file that doesn't exist.</span></span> |
| <span data-ttu-id="f60ec-194">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-194">**Common causes**</span></span> | <span data-ttu-id="f60ec-195">El archivo de proyecto está presente en el disco o la referencia es incorrecta.</span><span class="sxs-lookup"><span data-stu-id="f60ec-195">The project file is missing from disk or the reference is incorrect.</span></span> |
| <span data-ttu-id="f60ec-196">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-196">**Example message**</span></span> | <span data-ttu-id="f60ec-197">*Referencia de proyecto no existe 'c:\a.csproj'. Compruebe que la referencia al proyecto es válida y que existe el archivo de proyecto.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-197">*Project reference does not exist 'c:\a.csproj'. Check that the project reference is valid and that the project file exists.*</span></span> |

### <a name="nu1105"></a><span data-ttu-id="f60ec-198">NU1105</span><span class="sxs-lookup"><span data-stu-id="f60ec-198">NU1105</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-199">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-199">**Issue**</span></span> | <span data-ttu-id="f60ec-200">El archivo de proyecto existe pero no se proporcionó ninguna información de restauración para él.</span><span class="sxs-lookup"><span data-stu-id="f60ec-200">The project file exists but no restore information was provided for it.</span></span> |
| <span data-ttu-id="f60ec-201">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-201">**Common causes**</span></span> | <span data-ttu-id="f60ec-202">En Visual Studio, esto podría significar que el proyecto está cargado.</span><span class="sxs-lookup"><span data-stu-id="f60ec-202">In Visual Studio this could mean that the project is unloaded.</span></span> <span data-ttu-id="f60ec-203">Desde la línea de comandos, esto podría significar que el archivo está dañado o que no contiene la personalizada después de destino de las importaciones que necesita para que la restauración leer el proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-203">From the command line this could mean that the file is corrupt or that it doesn't contain the custom after imports target needed for restore to read the project.</span></span> |
| <span data-ttu-id="f60ec-204">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-204">**Example message**</span></span> | <span data-ttu-id="f60ec-205">*No se puede leer la información de proyecto de 'c:\a.csproj'. El archivo de proyecto puede ser destinos no válidos o que faltan necesarios para la restauración.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-205">*Unable to read project information for 'c:\a.csproj'. The project file may be invalid or missing targets required for restore.*</span></span> |

### <a name="nu1106"></a><span data-ttu-id="f60ec-206">NU1106</span><span class="sxs-lookup"><span data-stu-id="f60ec-206">NU1106</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-207">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-207">**Issue**</span></span> | <span data-ttu-id="f60ec-208">Las restricciones de dependencia no se pueden resolver.</span><span class="sxs-lookup"><span data-stu-id="f60ec-208">Dependency constraints cannot be resolved.</span></span> |
| <span data-ttu-id="f60ec-209">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-209">**Common causes**</span></span> | <span data-ttu-id="f60ec-210">Los paquetes contienen depende de las versiones exactas de un paquete en lugar de los intervalos.</span><span class="sxs-lookup"><span data-stu-id="f60ec-210">Packages contain dependency on exact versions of a package instead of open-ended ranges.</span></span> |
| <span data-ttu-id="f60ec-211">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-211">**Example message**</span></span> | <span data-ttu-id="f60ec-212">*No se pueden satisfacer las solicitudes en conflicto para {id}: {ruta de acceso de conflicto} Framework: {gráfico de destino}*</span><span class="sxs-lookup"><span data-stu-id="f60ec-212">*Unable to satisfy conflicting requests for {id}: {conflict path} Framework: {target graph}*</span></span> |

<a name="nu1107"></a> 

### <a name="nu1107-previously-nu1607"></a><span data-ttu-id="f60ec-213">NU1107 (anteriormente NU1607)</span><span class="sxs-lookup"><span data-stu-id="f60ec-213">NU1107 (Previously NU1607)</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-214">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-214">**Issue**</span></span> | <span data-ttu-id="f60ec-215">No se puede resolver las restricciones de dependencia entre paquetes.</span><span class="sxs-lookup"><span data-stu-id="f60ec-215">Unable to resolve dependency constraints between packages.</span></span> |
| <span data-ttu-id="f60ec-216">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-216">**Common causes**</span></span> | <span data-ttu-id="f60ec-217">Paquetes con las restricciones de dependencia en versiones exactas no permitir que los otros paquetes aumentar la versión, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-217">Packages with dependency constraints on exact versions do not allow other packages to increase the version if needed.</span></span> |
| <span data-ttu-id="f60ec-218">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-218">**Example message**</span></span> | <span data-ttu-id="f60ec-219">*Ha detectado para NuGet.Versioning un conflicto de versión. Hacen referencia al paquete directamente desde el proyecto para resolver este problema.<br/>  NuGet.Packaging 3.5.0 -> NuGet.Versioning (= 3.5.0)<br/> NuGet.Configuration 4.0.0 -> NuGet.Versioning (= 4.0.0)*</span><span class="sxs-lookup"><span data-stu-id="f60ec-219">*Version conflict detected for NuGet.Versioning. Reference the package directly from the project to resolve this issue.<br/>  NuGet.Packaging 3.5.0 -> NuGet.Versioning (= 3.5.0)<br/>  NuGet.Configuration 4.0.0 -> NuGet.Versioning (= 4.0.0)*</span></span> |

<a name="nu1108"></a>

### <a name="nu1108-previously-nu1606"></a><span data-ttu-id="f60ec-220">NU1108 (anteriormente NU1606)</span><span class="sxs-lookup"><span data-stu-id="f60ec-220">NU1108 (Previously NU1606)</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-221">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-221">**Issue**</span></span> | <span data-ttu-id="f60ec-222">Se detectó una dependencia circular.</span><span class="sxs-lookup"><span data-stu-id="f60ec-222">A circular dependency was detected.</span></span> |
| <span data-ttu-id="f60ec-223">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-223">**Common causes**</span></span> | <span data-ttu-id="f60ec-224">Un paquete se creó correctamente.</span><span class="sxs-lookup"><span data-stu-id="f60ec-224">A package is authored incorrectly.</span></span> |
| <span data-ttu-id="f60ec-225">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-225">**Example message**</span></span> | <span data-ttu-id="f60ec-226">*Se detectó un ciclo: A -> B -> A*</span><span class="sxs-lookup"><span data-stu-id="f60ec-226">*Cycle detected: A -> B -> A*</span></span> |

## <a name="compatibility-errors"></a><span data-ttu-id="f60ec-227">Errores de compatibilidad</span><span class="sxs-lookup"><span data-stu-id="f60ec-227">Compatibility errors</span></span>

<span data-ttu-id="f60ec-228">[NU1201](#nu1201) | [NU1202](#nu1202) | [NU1203](#nu1203) | [NU1401](#nu1401)</span><span class="sxs-lookup"><span data-stu-id="f60ec-228">[NU1201](#nu1201) | [NU1202](#nu1202) | [NU1203](#nu1203) | [NU1401](#nu1401)</span></span>

### <a name="nu1201"></a><span data-ttu-id="f60ec-229">NU1201</span><span class="sxs-lookup"><span data-stu-id="f60ec-229">NU1201</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-230">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-230">**Issue**</span></span> | <span data-ttu-id="f60ec-231">Un proyecto de dependencia no contiene un marco de trabajo compatible con el proyecto actual.</span><span class="sxs-lookup"><span data-stu-id="f60ec-231">A dependency project doesn't contain a framework compatible with the current project.</span></span> |
| <span data-ttu-id="f60ec-232">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-232">**Common causes**</span></span> | <span data-ttu-id="f60ec-233">.NET framework de destino del proyecto es una versión posterior a del proyecto usada.</span><span class="sxs-lookup"><span data-stu-id="f60ec-233">The project's target framework is a higher version than the consuming project.</span></span> |
| <span data-ttu-id="f60ec-234">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-234">**Example message**</span></span> | <span data-ttu-id="f60ec-235">*WAN de proyecto no es compatible con netstandard1.3 (. NETStandard, Version = v1.3). Project admite de WAN:<br/> -netstandard1.6 (. NETStandard, Version = v1.6)<br/> -netcoreapp1.0 (. NETCoreApp, Version = v1.0)*</span><span class="sxs-lookup"><span data-stu-id="f60ec-235">*Project ServerWeb is not compatible with netstandard1.3 (.NETStandard,Version=v1.3). Project ServerWeb supports:<br/>  - netstandard1.6 (.NETStandard,Version=v1.6)<br/>  - netcoreapp1.0 (.NETCoreApp,Version=v1.0)*</span></span> |

### <a name="nu1202"></a><span data-ttu-id="f60ec-236">NU1202</span><span class="sxs-lookup"><span data-stu-id="f60ec-236">NU1202</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-237">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-237">**Issue**</span></span> | <span data-ttu-id="f60ec-238">Un paquete de dependencia no contiene ningún activos compatibles con el proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-238">A dependency package doesn't contain any assets compatible with the project.</span></span> |
| <span data-ttu-id="f60ec-239">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-239">**Common causes**</span></span> | <span data-ttu-id="f60ec-240">El paquete no es compatible con .NET framework de destino del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-240">The package doesn't support the project's target framework.</span></span> |
| <span data-ttu-id="f60ec-241">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-241">**Example message**</span></span> | <span data-ttu-id="f60ec-242">*Paquete System.ComponentModel.EventBasedAsync 4.0.11 no es compatible con netstandard1.3 (. NETStandard, Version = v1.3). Package System.ComponentModel.EventBasedAsync 4.0.11 supports:<br/>  - monoandroid10 (MonoAndroid,Version=v1.0)<br/>  - monotouch10 (MonoTouch,Version=v1.0)<br/>  - net45 (.NETFramework,Version=v4.5)<br/>  - netcore50 (.NETCore,Version=v5.0)<br/>  - netstandard1.0 (.NETStandard,Version=v1.0)<br/>  - portable-net45+win8+wp8+wpa81 (.NETPortable,Version=v0.0,Profile=Profile259)<br/>  - win8 (Windows,Version=v8.0)<br/>  - wp8 (WindowsPhone,Version=v8.0)<br/>  - wpa81 (WindowsPhoneApp,Version=v8.1)<br/>  - xamarinios10 (Xamarin.iOS,Version=v1.0)<br/>  - xamarinmac20 (Xamarin.Mac,Version=v2.0)<br/>  - xamarintvos10 (Xamarin.TVOS,Version=v1.0)<br/>  - xamarinwatchos10 (Xamarin.WatchOS,Version=v1.0)*</span><span class="sxs-lookup"><span data-stu-id="f60ec-242">*Package System.ComponentModel.EventBasedAsync 4.0.11 is not compatible with netstandard1.3 (.NETStandard,Version=v1.3). Package System.ComponentModel.EventBasedAsync 4.0.11 supports:<br/>  - monoandroid10 (MonoAndroid,Version=v1.0)<br/>  - monotouch10 (MonoTouch,Version=v1.0)<br/>  - net45 (.NETFramework,Version=v4.5)<br/>  - netcore50 (.NETCore,Version=v5.0)<br/>  - netstandard1.0 (.NETStandard,Version=v1.0)<br/>  - portable-net45+win8+wp8+wpa81 (.NETPortable,Version=v0.0,Profile=Profile259)<br/>  - win8 (Windows,Version=v8.0)<br/>  - wp8 (WindowsPhone,Version=v8.0)<br/>  - wpa81 (WindowsPhoneApp,Version=v8.1)<br/>  - xamarinios10 (Xamarin.iOS,Version=v1.0)<br/>  - xamarinmac20 (Xamarin.Mac,Version=v2.0)<br/>  - xamarintvos10 (Xamarin.TVOS,Version=v1.0)<br/>  - xamarinwatchos10 (Xamarin.WatchOS,Version=v1.0)*</span></span>|

### <a name="nu1203"></a><span data-ttu-id="f60ec-243">NU1203</span><span class="sxs-lookup"><span data-stu-id="f60ec-243">NU1203</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-244">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-244">**Issue**</span></span> | <span data-ttu-id="f60ec-245">El paquete no es compatible con el proyecto `RuntimeIdentifier`.</span><span class="sxs-lookup"><span data-stu-id="f60ec-245">The package doesn't support the project's `RuntimeIdentifier`.</span></span> |
| <span data-ttu-id="f60ec-246">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-246">**Common causes**</span></span> | <span data-ttu-id="f60ec-247">El paquete no es compatible con la actual `RuntimeIdentifier`.</span><span class="sxs-lookup"><span data-stu-id="f60ec-247">The package doesn't support the current `RuntimeIdentifier`.</span></span> <span data-ttu-id="f60ec-248">Cambiar el `RuntimeIdentifier` valores utilizados en el proyecto, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-248">Change the `RuntimeIdentifier` values used in the project if needed.</span></span> |
| <span data-ttu-id="f60ec-249">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-249">**Example message**</span></span> | <span data-ttu-id="f60ec-250">*System.Example 1.0.0 proporciona un ensamblado de referencia en tiempo de compilación para.dll en net461, pero no hay ningún ensamblado en tiempo de ejecución compatible.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-250">*System.Example 1.0.0 provides a compile-time reference assembly for a.dll on net461, but there is no compatible run-time assembly.*</span></span> |

### <a name="nu1401"></a><span data-ttu-id="f60ec-251">NU1401</span><span class="sxs-lookup"><span data-stu-id="f60ec-251">NU1401</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-252">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-252">**Issue**</span></span> | <span data-ttu-id="f60ec-253">El paquete requiere características o marcos de trabajo no admitidas actualmente por la versión instalada de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f60ec-253">The package requires features or frameworks not currently supported by the installed version of NuGet.</span></span> |
| <span data-ttu-id="f60ec-254">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-254">**Common causes**</span></span> | <span data-ttu-id="f60ec-255">Actualizar NuGet para corregir el problema.</span><span class="sxs-lookup"><span data-stu-id="f60ec-255">Upgrade NuGet to fix the issue.</span></span> |
| <span data-ttu-id="f60ec-256">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-256">**Example message**</span></span> | <span data-ttu-id="f60ec-257">*El paquete 'NuGet.Versioning' requiere NuGet versión de cliente '5.0.0' o superior, pero la versión de NuGet actual es '4.3.0'. Para actualizar NuGet, vaya a http://docs.nuget.org/consume/installing-nuget.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-257">*The 'NuGet.Versioning' package requires NuGet client version '5.0.0' or above, but the current NuGet version is '4.3.0'. To upgrade NuGet, please go to http://docs.nuget.org/consume/installing-nuget.*</span></span> |

## <a name="invalid-input-warnings"></a><span data-ttu-id="f60ec-258">Advertencias de entrada no válidas</span><span class="sxs-lookup"><span data-stu-id="f60ec-258">Invalid input warnings</span></span>

<span data-ttu-id="f60ec-259">[NU1501](#nu1501) | [NU1502](#nu1502) | [NU1503](#nu1503)</span><span class="sxs-lookup"><span data-stu-id="f60ec-259">[NU1501](#nu1501) | [NU1502](#nu1502) | [NU1503](#nu1503)</span></span>

### <a name="nu1501"></a><span data-ttu-id="f60ec-260">NU1501</span><span class="sxs-lookup"><span data-stu-id="f60ec-260">NU1501</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-261">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-261">**Issue**</span></span> | <span data-ttu-id="f60ec-262">La restauración de proyecto está intentando operar en no se encontró.</span><span class="sxs-lookup"><span data-stu-id="f60ec-262">The project restore is attempting to operate on was not found.</span></span> |
| <span data-ttu-id="f60ec-263">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-263">**Common causes**</span></span> | <span data-ttu-id="f60ec-264">El proyecto es que faltan.</span><span class="sxs-lookup"><span data-stu-id="f60ec-264">The project is missing.</span></span> |
| <span data-ttu-id="f60ec-265">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-265">**Example message**</span></span> | <span data-ttu-id="f60ec-266">*La carpeta 'c:\projects\a' no contiene ningún proyecto para restaurar.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-266">*The folder 'c:\projects\a' does not contain a project to restore.*</span></span> |

### <a name="nu1502"></a><span data-ttu-id="f60ec-267">NU1502</span><span class="sxs-lookup"><span data-stu-id="f60ec-267">NU1502</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-268">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-268">**Issue**</span></span> | <span data-ttu-id="f60ec-269">`RuntimeSupports`contiene un perfil no válido.</span><span class="sxs-lookup"><span data-stu-id="f60ec-269">`RuntimeSupports` contains an invalid profile.</span></span> |
| <span data-ttu-id="f60ec-270">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-270">**Common causes**</span></span> | <span data-ttu-id="f60ec-271">No se encontró el perfil de admite en un `runtime.json` archivos de los paquetes de dependencia actual.</span><span class="sxs-lookup"><span data-stu-id="f60ec-271">The supports profile was not found in a `runtime.json` file from the current dependency packages.</span></span> |
| <span data-ttu-id="f60ec-272">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-272">**Example message**</span></span> | <span data-ttu-id="f60ec-273">*Perfil de compatibilidad desconocido: aaa*</span><span class="sxs-lookup"><span data-stu-id="f60ec-273">*Unknown Compatibility Profile: aaa*</span></span> |

### <a name="nu1503"></a><span data-ttu-id="f60ec-274">NU1503</span><span class="sxs-lookup"><span data-stu-id="f60ec-274">NU1503</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-275">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-275">**Issue**</span></span> | <span data-ttu-id="f60ec-276">Un proyecto de dependencia no importa los destinos de restauración de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f60ec-276">A dependency project doesn't import NuGet's restore targets.</span></span> <span data-ttu-id="f60ec-277">Esto es similar a NU1105, pero aquí se omite el proyecto y pasa por alto en lugar de producir todos de restauración a un error.</span><span class="sxs-lookup"><span data-stu-id="f60ec-277">This is similar to NU1105 but here the project is skipped and ignored instead of causing all of restore to fail.</span></span> <span data-ttu-id="f60ec-278">En soluciones complejas a menudo hay otros tipos de proyectos que pueden no admitir la restauración.</span><span class="sxs-lookup"><span data-stu-id="f60ec-278">In complex solutions there are often other types of projects that may not support restore.</span></span> |
| <span data-ttu-id="f60ec-279">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-279">**Common causes**</span></span> | <span data-ttu-id="f60ec-280">Esto puede ocurrir por proyectos que importen props/destinos comunes que se importan automáticamente la restauración.</span><span class="sxs-lookup"><span data-stu-id="f60ec-280">This can happen for projects that do not import common props/targets which automatically import restore.</span></span> <span data-ttu-id="f60ec-281">Si el proyecto no tiene que restaurarse Esto puede hacer caso omiso.</span><span class="sxs-lookup"><span data-stu-id="f60ec-281">If the project doesn't need to be restored this can be ignored.</span></span> |
| <span data-ttu-id="f60ec-282">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-282">**Example message**</span></span> | <span data-ttu-id="f60ec-283">*Se omitirá la restauración para el proyecto 'c:\a.csproj'. El archivo de proyecto puede ser destinos no válidos o que faltan necesarios para la restauración.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-283">*Skipping restore for project 'c:\a.csproj'. The project file may be invalid or missing targets required for restore.*</span></span> |

## <a name="unexpected-package-version-warnings"></a><span data-ttu-id="f60ec-284">Advertencias de la versión de paquete inesperado</span><span class="sxs-lookup"><span data-stu-id="f60ec-284">Unexpected package version warnings</span></span>

<span data-ttu-id="f60ec-285">[NU1601](#nu1601) | [NU1602](#nu1602) | [NU1603](#nu1603) | [NU1604](#nu1604) | [NU1605](#nu1605)</span><span class="sxs-lookup"><span data-stu-id="f60ec-285">[NU1601](#nu1601) | [NU1602](#nu1602) | [NU1603](#nu1603) | [NU1604](#nu1604) | [NU1605](#nu1605)</span></span>

### <a name="nu1601"></a><span data-ttu-id="f60ec-286">NU1601</span><span class="sxs-lookup"><span data-stu-id="f60ec-286">NU1601</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-287">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-287">**Issue**</span></span> | <span data-ttu-id="f60ec-288">Se incrementará en una dependencia de proyecto directa a una versión más reciente que el proyecto especificado.</span><span class="sxs-lookup"><span data-stu-id="f60ec-288">A direct project dependency was bumped to a higher version than the project specified.</span></span> |
| <span data-ttu-id="f60ec-289">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-289">**Common causes**</span></span> | <span data-ttu-id="f60ec-290">Otro paquete de dependencia requiere una versión posterior e incrementará en el paquete.</span><span class="sxs-lookup"><span data-stu-id="f60ec-290">Another dependency package required a higher version and bumped the package up.</span></span> |
| <span data-ttu-id="f60ec-291">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-291">**Example message**</span></span> | <span data-ttu-id="f60ec-292">*Dependencia especificada era NuGet.Versioning (> = 3.5.0) pero terminaba con NuGet.Versioning 4.0.0.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-292">*Dependency specified was NuGet.Versioning (>= 3.5.0) but ended up with NuGet.Versioning 4.0.0.*</span></span> |

### <a name="nu1602"></a><span data-ttu-id="f60ec-293">NU1602</span><span class="sxs-lookup"><span data-stu-id="f60ec-293">NU1602</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-294">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-294">**Issue**</span></span> | <span data-ttu-id="f60ec-295">Una dependencia del paquete falta un límite inferior.</span><span class="sxs-lookup"><span data-stu-id="f60ec-295">A package dependency is missing a lower bound.</span></span> <span data-ttu-id="f60ec-296">Esto no permite la restauración buscar el *mejor coincidencia*.</span><span class="sxs-lookup"><span data-stu-id="f60ec-296">This doesn't allow restore to find the *best match*.</span></span> <span data-ttu-id="f60ec-297">Cada restauración va a desplazarse hacia abajo y tratar de buscar una versión anterior que se puede usar.</span><span class="sxs-lookup"><span data-stu-id="f60ec-297">Each restore will float downwards trying to find a lower version that can be used.</span></span> <span data-ttu-id="f60ec-298">Esto significa que la restauración se queda en línea para comprobar todos los orígenes de cada vez en lugar de usar los paquetes que ya existen en la carpeta de paquete de usuario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-298">This means that restore goes online to check all sources each time instead of using the packages that already exist in the user package folder.</span></span> |
| <span data-ttu-id="f60ec-299">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-299">**Common causes**</span></span> | <span data-ttu-id="f60ec-300">Esto suele ser un error de creación de paquete.</span><span class="sxs-lookup"><span data-stu-id="f60ec-300">This is usually a package authoring error.</span></span> |
| <span data-ttu-id="f60ec-301">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-301">**Example message**</span></span> | <span data-ttu-id="f60ec-302">*NuGet.Packaging 4.0.0 no proporciona un límite inferior inclusivo de dependencia NuGet.Versioning (3.5.0 >). Una mejor coincidencia aproximada de 3.6.0 se resolvió.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-302">*NuGet.Packaging 4.0.0 does not provide an inclusive lower bound for dependency NuGet.Versioning (> 3.5.0). An approximate best match of 3.6.0 was resolved.*</span></span> |

### <a name="nu1603"></a><span data-ttu-id="f60ec-303">NU1603</span><span class="sxs-lookup"><span data-stu-id="f60ec-303">NU1603</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-304">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-304">**Issue**</span></span> | <span data-ttu-id="f60ec-305">Una dependencia del paquete especifica una versión que no se pudo encontrar.</span><span class="sxs-lookup"><span data-stu-id="f60ec-305">A package dependency specified a version that could not be found.</span></span> <span data-ttu-id="f60ec-306">Una versión posterior se usó en su lugar, que es distinto de lo que se creó el paquete en.</span><span class="sxs-lookup"><span data-stu-id="f60ec-306">A higher version was used instead, which differs from what the package was authored against.</span></span><br/><br/><span data-ttu-id="f60ec-307">Esto significa que la restauración no se encontró el *mejor coincidencia*.</span><span class="sxs-lookup"><span data-stu-id="f60ec-307">This means that restore did not find the *best match*.</span></span> <span data-ttu-id="f60ec-308">Cada restauración va a desplazarse hacia abajo y tratar de buscar una versión anterior que se puede usar.</span><span class="sxs-lookup"><span data-stu-id="f60ec-308">Each restore will float downwards trying to find a lower version that can be used.</span></span> <span data-ttu-id="f60ec-309">Esto significa que la restauración se queda en línea para comprobar todos los orígenes de cada vez en lugar de usar los paquetes que ya existen en la carpeta de paquete de usuario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-309">This means that restore goes online to check all sources each time instead of using the packages that already exist in the user package folder.</span></span> |
| <span data-ttu-id="f60ec-310">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-310">**Common causes**</span></span> | <span data-ttu-id="f60ec-311">Los orígenes del paquete no contienen la versión de límite inferior esperado.</span><span class="sxs-lookup"><span data-stu-id="f60ec-311">The package sources do not contain the expected lower bound version.</span></span> <span data-ttu-id="f60ec-312">Si no se ha liberado el paquete que esperaba, a continuación, puede tratarse de un error de creación de paquete.</span><span class="sxs-lookup"><span data-stu-id="f60ec-312">If the package expected has not been released then this may be a package authoring error.</span></span> |
| <span data-ttu-id="f60ec-313">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-313">**Example message**</span></span> | <span data-ttu-id="f60ec-314">NuGet.Packaging 4.0.0 depende NuGet.Versioning (> = 4.0.0) pero no se encontró 4.0.0.</span><span class="sxs-lookup"><span data-stu-id="f60ec-314">NuGet.Packaging 4.0.0 depends on NuGet.Versioning (>= 4.0.0) but 4.0.0 was not found.</span></span> <span data-ttu-id="f60ec-315">Una mejor coincidencia aproximada de 5.0.0 se resolvió.</span><span class="sxs-lookup"><span data-stu-id="f60ec-315">An approximate best match of 5.0.0 was resolved.</span></span> |

### <a name="nu1604"></a><span data-ttu-id="f60ec-316">NU1604</span><span class="sxs-lookup"><span data-stu-id="f60ec-316">NU1604</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-317">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-317">**Issue**</span></span> | <span data-ttu-id="f60ec-318">Una dependencia de proyecto no define un límite inferior.</span><span class="sxs-lookup"><span data-stu-id="f60ec-318">A project dependency doesn't define a lower bound.</span></span><br/><br/><span data-ttu-id="f60ec-319">Esto significa que la restauración no se encontró el *mejor coincidencia*.</span><span class="sxs-lookup"><span data-stu-id="f60ec-319">This means that restore did not find the *best match*.</span></span> <span data-ttu-id="f60ec-320">Cada restauración va a desplazarse hacia abajo y tratar de buscar una versión anterior que se puede usar.</span><span class="sxs-lookup"><span data-stu-id="f60ec-320">Each restore will float downwards trying to find a lower version that can be used.</span></span> <span data-ttu-id="f60ec-321">Esto significa que la restauración se queda en línea para comprobar todos los orígenes de cada vez en lugar de usar los paquetes que ya existen en la carpeta de paquete de usuario.</span><span class="sxs-lookup"><span data-stu-id="f60ec-321">This means that restore goes online to check all sources each time instead of using the packages that already exist in the user package folder.</span></span> |
| <span data-ttu-id="f60ec-322">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-322">**Common causes**</span></span> | <span data-ttu-id="f60ec-323">El proyecto *PackageReference* *versión* atributo debe actualizarse para incluir un límite inferior.</span><span class="sxs-lookup"><span data-stu-id="f60ec-323">The project's *PackageReference* *Version* attribute should be updated to include a lower bound.</span></span> |
| <span data-ttu-id="f60ec-324">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-324">**Example message**</span></span> | <span data-ttu-id="f60ec-325">*Proyecto dependencia NuGet.Versioning (< = 9.0.0) doe no contiene un límite inferior inclusivo. Incluir un límite inferior en la versión de dependencia para garantizar que los resultados de restauración coherentes.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-325">*Project dependency NuGet.Versioning (<= 9.0.0) doe not contain an inclusive lower bound. Include a lower bound in the dependency version to ensure consistent restore results.*</span></span> |

### <a name="nu1605"></a><span data-ttu-id="f60ec-326">NU1605</span><span class="sxs-lookup"><span data-stu-id="f60ec-326">NU1605</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-327">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-327">**Issue**</span></span> | <span data-ttu-id="f60ec-328">Un paquete de dependencia especificó una restricción de versión en una versión posterior de un paquete que la restauración que se resuelven en última instancia.</span><span class="sxs-lookup"><span data-stu-id="f60ec-328">A dependency package specified a version constraint on a higher version of a package than restore ultimately resolved.</span></span> |
| <span data-ttu-id="f60ec-329">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-329">**Common causes**</span></span> | <span data-ttu-id="f60ec-330">Wins más cercano al resolver los paquetes.</span><span class="sxs-lookup"><span data-stu-id="f60ec-330">Nearest wins when resolving packages.</span></span> <span data-ttu-id="f60ec-331">Un paquete en el gráfico de cuanto más cerca posible ha reemplazado un paquete lejano.</span><span class="sxs-lookup"><span data-stu-id="f60ec-331">A nearer package in the graph may have overridden a distant package.</span></span> |
| <span data-ttu-id="f60ec-332">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-332">**Example message**</span></span> | <span data-ttu-id="f60ec-333">*Detecta la degradación de paquete: NuGet.Versioning de 4.0.0 3.5.0. Hacen referencia al paquete directamente desde el proyecto para seleccionar una versión diferente.<br/>  NuGet.Packaging 3.5.0 -> NuGet.Versioning 3.5.0<br/> NuGet.Commands 4.0.0 -> NuGet.Configuration 4.0.0 -> NuGet.Versioning 4.0.0*</span><span class="sxs-lookup"><span data-stu-id="f60ec-333">*Detected package downgrade: NuGet.Versioning from 4.0.0 to 3.5.0. Reference the package directly from the project to select a different version.<br/>  NuGet.Packaging 3.5.0 -> NuGet.Versioning 3.5.0<br/>  NuGet.Commands 4.0.0 -> NuGet.Configuration 4.0.0 -> NuGet.Versioning 4.0.0*</span></span> |

## <a name="resolver-conflict-warnings"></a><span data-ttu-id="f60ec-334">Advertencias de conflicto de resolución</span><span class="sxs-lookup"><span data-stu-id="f60ec-334">Resolver conflict warnings</span></span>

### <a name="nu1608"></a><span data-ttu-id="f60ec-335">NU1608</span><span class="sxs-lookup"><span data-stu-id="f60ec-335">NU1608</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-336">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-336">**Issue**</span></span> | <span data-ttu-id="f60ec-337">Un paquete de resolución es mayor que permite que una restricción de dependencia.</span><span class="sxs-lookup"><span data-stu-id="f60ec-337">A resolve package is higher than a dependency constraint allows.</span></span> <span data-ttu-id="f60ec-338">En algunos casos esto tiene su porqué y se puede suprimir la advertencia.</span><span class="sxs-lookup"><span data-stu-id="f60ec-338">In some cases this is intentional and the warning can be suppressed.</span></span> |
| <span data-ttu-id="f60ec-339">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-339">**Common causes**</span></span> | <span data-ttu-id="f60ec-340">Un paquete al que hace referencia directamente un proyecto invalidará las restricciones de dependencia de otros paquetes.</span><span class="sxs-lookup"><span data-stu-id="f60ec-340">A package referenced directly by a project will override dependency constraints from other packages.</span></span>   |
| <span data-ttu-id="f60ec-341">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-341">**Example message**</span></span> | <span data-ttu-id="f60ec-342">*Versión del paquete detectado fuera de restricción de dependencia: x 1.0.0 requiere y (= 1.0.0) pero la versión y 2.0.0 se resolvió.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-342">*Detected package version outside of dependency constraint: x 1.0.0 requires y (= 1.0.0) but version y 2.0.0 was resolved.*</span></span> |

## <a name="package-fallback-warnings"></a><span data-ttu-id="f60ec-343">Advertencias de reserva de paquete</span><span class="sxs-lookup"><span data-stu-id="f60ec-343">Package fallback warnings</span></span>

### <a name="nu1701"></a><span data-ttu-id="f60ec-344">NU1701</span><span class="sxs-lookup"><span data-stu-id="f60ec-344">NU1701</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-345">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-345">**Issue**</span></span> | <span data-ttu-id="f60ec-346">*PackageTargetFallback/AssetTargetFallback* se utiliza para seleccionar los activos en un paquete.</span><span class="sxs-lookup"><span data-stu-id="f60ec-346">*PackageTargetFallback/AssetTargetFallback* was used to select assets from a package.</span></span> <span data-ttu-id="f60ec-347">Se trata de una advertencia para que el usuario sepa que los activos pueden no ser compatible al 100%.</span><span class="sxs-lookup"><span data-stu-id="f60ec-347">This is a warning to let the user know that the assets may not be 100% compatible.</span></span> |
| <span data-ttu-id="f60ec-348">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-348">**Common causes**</span></span> | <span data-ttu-id="f60ec-349">El paquete no es compatible con el marco de trabajo del proyecto.</span><span class="sxs-lookup"><span data-stu-id="f60ec-349">The package doesn't support the project framework.</span></span> |
| <span data-ttu-id="f60ec-350">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-350">**Example message**</span></span> | <span data-ttu-id="f60ec-351">*Paquete 'NuGet.Versioning' se restauró usando 'portable net45 + win8' en su lugar, la plataforma de destino del proyecto 'netstandard1.5'. Este paquete no puede ser totalmente compatible con el proyecto.*</span><span class="sxs-lookup"><span data-stu-id="f60ec-351">*Package 'NuGet.Versioning' was restored using 'portable-net45+win8' instead the project target framework 'netstandard1.5'. This package may not be fully compatible with your project.*</span></span> |

## <a name="feed-warnings"></a><span data-ttu-id="f60ec-352">Advertencias de fuentes</span><span class="sxs-lookup"><span data-stu-id="f60ec-352">Feed warnings</span></span>

### <a name="nu1801"></a><span data-ttu-id="f60ec-353">NU1801</span><span class="sxs-lookup"><span data-stu-id="f60ec-353">NU1801</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-354">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-354">**Issue**</span></span> | <span data-ttu-id="f60ec-355">Se produjo un error al leer la fuente cuando `IgnoreFailedSources` se establece en true, se convierte en una advertencia no es grave.</span><span class="sxs-lookup"><span data-stu-id="f60ec-355">An error occurred when reading the feed when `IgnoreFailedSources` is set to true, converting it to a non-fatal warning.</span></span> <span data-ttu-id="f60ec-356">Esto podría contener todos los mensajes y es genérico.</span><span class="sxs-lookup"><span data-stu-id="f60ec-356">This could contain any message and is generic.</span></span> |
| <span data-ttu-id="f60ec-357">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-357">**Common causes**</span></span> | <span data-ttu-id="f60ec-358">El origen no es válido.</span><span class="sxs-lookup"><span data-stu-id="f60ec-358">The source is invalid.</span></span> |
| <span data-ttu-id="f60ec-359">**Mensaje de ejemplo**</span><span class="sxs-lookup"><span data-stu-id="f60ec-359">**Example message**</span></span> | <span data-ttu-id="f60ec-360">N/D</span><span class="sxs-lookup"><span data-stu-id="f60ec-360">n/a</span></span> |

## <a name="nuget-internal-errors-and-warnings"></a><span data-ttu-id="f60ec-361">Las advertencias y errores internos de NuGet</span><span class="sxs-lookup"><span data-stu-id="f60ec-361">NuGet internal errors and warnings</span></span>

<span data-ttu-id="f60ec-362">[NU1000](#nu1000) | [NU1500](#nu1500)</span><span class="sxs-lookup"><span data-stu-id="f60ec-362">[NU1000](#nu1000) | [NU1500](#nu1500)</span></span>

### <a name="nu1000"></a><span data-ttu-id="f60ec-363">NU1000</span><span class="sxs-lookup"><span data-stu-id="f60ec-363">NU1000</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-364">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-364">**Issue**</span></span> | <span data-ttu-id="f60ec-365">Un error interno no es específico de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f60ec-365">A non specific internal error from NuGet.</span></span> |
| <span data-ttu-id="f60ec-366">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-366">**Common causes**</span></span> | <span data-ttu-id="f60ec-367">Compruebe los registros para obtener más información</span><span class="sxs-lookup"><span data-stu-id="f60ec-367">Check the logs for more information</span></span> |

### <a name="nu1500"></a><span data-ttu-id="f60ec-368">NU1500</span><span class="sxs-lookup"><span data-stu-id="f60ec-368">NU1500</span></span>

| | |
| --- | --- |
| <span data-ttu-id="f60ec-369">**Problema**</span><span class="sxs-lookup"><span data-stu-id="f60ec-369">**Issue**</span></span> | <span data-ttu-id="f60ec-370">Advertencias interno no es específico de NuGet.</span><span class="sxs-lookup"><span data-stu-id="f60ec-370">A non specific internal warning from NuGet.</span></span> |
| <span data-ttu-id="f60ec-371">**Causas comunes**</span><span class="sxs-lookup"><span data-stu-id="f60ec-371">**Common causes**</span></span> | <span data-ttu-id="f60ec-372">Compruebe los registros para obtener más información</span><span class="sxs-lookup"><span data-stu-id="f60ec-372">Check the logs for more information</span></span> |