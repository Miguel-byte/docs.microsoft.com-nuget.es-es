---
title: "Restauración de paquetes NuGet | Microsoft Docs"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 02/12/2018
ms.topic: article
ms.prod: nuget
ms.technology: 
ms.assetid: a7bf21da-86ae-4c2d-8750-04ff53f41967
description: "Una descripción de cómo NuGet restaura paquetes de los que depende un proyecto, incluido cómo deshabilitar la restauración y la restricción de versiones."
keywords: "Restauración de paquetes NuGet, instalación de paquetes NuGet, instalación del paquete, restauración de paquetes, versiones de dependencia, deshabilitar la restauración automática, restricción de versiones de paquetes"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 761ef86a70e0a681449dc9fe86d6a52ac2b19bb1
ms.sourcegitcommit: 74c21b406302288c158e8ae26057132b12960be8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="package-restore"></a><span data-ttu-id="03603-104">Restauración de paquetes</span><span class="sxs-lookup"><span data-stu-id="03603-104">Package Restore</span></span>

<span data-ttu-id="03603-105">Para promover un entorno de desarrollo más limpio y reducir el tamaño del repositorio, **Restauración de paquetes** de NuGet instala todos los paquetes a los que se hace referencia antes de compilar un proyecto.</span><span class="sxs-lookup"><span data-stu-id="03603-105">To promote a cleaner development environment and to reduce repository size, NuGet **Package Restore** installs all referenced packages before a project is built.</span></span> <span data-ttu-id="03603-106">Esta característica de uso frecuente (disponible en Visual Studio, .NET Core 2.0 y versiones posteriores y xbuild en Mono) garantiza que todas las dependencias están disponibles en un proyecto sin necesidad de almacenar esos paquetes en el control de código fuente (vea [Paquetes y control de código fuente](../consume-packages/packages-and-source-control.md) para obtener información sobre cómo configurar el repositorio para excluir archivos binarios de paquete).</span><span class="sxs-lookup"><span data-stu-id="03603-106">This widely-used feature&mdash;available in Visual Studio, .NET Core 2.0+, and xbuild on Mono&mdash;ensures that all dependencies are available in a project without requiring those packages to be stored in source control (see [Packages and Source Control](../consume-packages/packages-and-source-control.md) on how to configure your repository to exclude package binaries).</span></span> <span data-ttu-id="03603-107">También puede restaurar paquetes manualmente en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="03603-107">You can also manually restore packages at any time.</span></span>

<span data-ttu-id="03603-108">Para obtener más detalles sobre la restauración de paquetes en servidores de compilación, vea [Restauración de paquetes con TFBuild](../consume-packages/team-foundation-build.md).</span><span class="sxs-lookup"><span data-stu-id="03603-108">For additional details on package restore on build servers, see [Package restore with TFBuild](../consume-packages/team-foundation-build.md).</span></span>

## <a name="package-restore-overview"></a><span data-ttu-id="03603-109">Información general sobre restauración de paquetes</span><span class="sxs-lookup"><span data-stu-id="03603-109">Package restore overview</span></span>

<span data-ttu-id="03603-110">Al restaurar paquetes, se instalan primero las dependencias directas de un proyecto según sea necesario y, luego, se instalarán todas las dependencias de los paquetes a lo largo del gráfico de dependencias completo.</span><span class="sxs-lookup"><span data-stu-id="03603-110">Restoring packages first installs the direct dependencies of a project as needed, then installing any dependencies of those packages throughout the entire dependency graph.</span></span>

<span data-ttu-id="03603-111">Si un paquete no está ya instalado, NuGet primero intenta recuperarlo desde la [caché](../consume-packages/managing-the-nuget-cache.md).</span><span class="sxs-lookup"><span data-stu-id="03603-111">If a package is not already installed, NuGet first attempts to retrieve it from the [cache](../consume-packages/managing-the-nuget-cache.md).</span></span> <span data-ttu-id="03603-112">Si el paquete no está en la memoria caché, NuGet intenta descargar el paquete (y almacenarlo en caché) desde todos los orígenes habilitados (vea [Configuración del comportamiento de NuGet](Configuring-NuGet-Behavior.md)); los orígenes también aparecen en la lista **Herramientas > Opciones > Administrador de paquetes NuGet > Orígenes del paquete** en Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="03603-112">If the package is not in the cache, NuGet then attempts to download (and cache) the package from all enabled sources (see [Configuring NuGet behavior](Configuring-NuGet-Behavior.md)); sources also appear in the  **Tools > Options > NuGet Package Manager > Package Sources** list in Visual Studio).</span></span> <span data-ttu-id="03603-113">NuGet omite el orden de los orígenes del paquete, usando el paquete del origen que primero responda a las solicitudes.</span><span class="sxs-lookup"><span data-stu-id="03603-113">NuGet ignores the order of package sources, using the package from whichever source is first to respond to requests.</span></span>

> [!Note]
> <span data-ttu-id="03603-114">NuGet no indica un error al restaurar un paquete hasta que se han comprobado todos los orígenes.</span><span class="sxs-lookup"><span data-stu-id="03603-114">NuGet does not indicate a failure to restore a package until all the sources have been checked.</span></span> <span data-ttu-id="03603-115">En ese momento, NuGet informa del error solo para el último origen de la lista.</span><span class="sxs-lookup"><span data-stu-id="03603-115">At that time, NuGet reports the failure for only the last source in the list.</span></span> <span data-ttu-id="03603-116">El error implica que el paquete no estaba presente en *ninguno* de los otros orígenes, aunque los errores no se muestran para cada uno de esos orígenes de forma individual.</span><span class="sxs-lookup"><span data-stu-id="03603-116">The error implies that the package wasn't present on *any* of the other sources, even though errors are not shown for each of those sources individually.</span></span>

<span data-ttu-id="03603-117">La restauración de paquetes se activa de las maneras siguientes:</span><span class="sxs-lookup"><span data-stu-id="03603-117">Package restore is triggered in the following ways:</span></span>

- <span data-ttu-id="03603-118">**CLI de dotnet**: use el comando [dotnet restore](/dotnet/core/tools/dotnet-restore?tabs=netcore2x), que restaura los paquetes incluidos en el archivo de proyecto (vea [PackageReference](../consume-packages/package-references-in-project-files.md)).</span><span class="sxs-lookup"><span data-stu-id="03603-118">**dotnet CLI**: use the [dotnet restore](/dotnet/core/tools/dotnet-restore?tabs=netcore2x) command, which restores packages listed in the project file (see [PackageReference](../consume-packages/package-references-in-project-files.md)).</span></span> <span data-ttu-id="03603-119">Con .NET Core 2.0 y versiones posteriores, la restauración se realiza automáticamente con `dotnet build` y `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="03603-119">With .NET Core 2.0 and later, restore is done automatically with `dotnet build` and `dotnet run`.</span></span>

- <span data-ttu-id="03603-120">**Interfaz de usuario del Administrador de paquetes (Visual Studio en Windows)**: los paquetes se restauran automáticamente al crear un proyecto a partir de una plantilla y al compilar un proyecto (sujeto a la opción descrita en [Habilitar y deshabilitar la restauración de paquetes](#enabling-and-disabling-package-restore)).</span><span class="sxs-lookup"><span data-stu-id="03603-120">**Package Manager UI (Visual Studio on Windows)**: Packages are restored automatically when creating a project from a template and when building a project (subject to the option described in [Enabling and disabling package restore](#enabling-and-disabling-package-restore)).</span></span> <span data-ttu-id="03603-121">En NuGet 4.0 y versiones posteriores, la restauración también se produce automáticamente al realizar cambios en un proyecto basado en el SDK de .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03603-121">In NuGet 4.0+, restore also happens automatically when changes are made to a .NET Core SDK-based project.</span></span>

    <span data-ttu-id="03603-122">Para la restauración manual, haga clic con el botón derecho en la solución en el Explorador de soluciones y seleccione **Restaurar paquetes NuGet**.</span><span class="sxs-lookup"><span data-stu-id="03603-122">To restore manually, right-click the solution in Solution Explorer and select **Restore NuGet Packages**.</span></span> <span data-ttu-id="03603-123">Si uno o varios paquetes siguen sin estar instalados correctamente (lo que significa que el Explorador de soluciones muestra un icono de error), use la interfaz de usuario del Administrador de paquetes para desinstalar y reinstalar los paquetes afectados.</span><span class="sxs-lookup"><span data-stu-id="03603-123">If one or more individual packages are still not installed properly (meaning that Solution Explorer shows an error icon), then use the Package Manager UI to uninstall and reinstall the affected packages.</span></span> <span data-ttu-id="03603-124">Vea [Reinstalación y actualización de paquetes](../consume-packages/reinstalling-and-updating-packages.md)</span><span class="sxs-lookup"><span data-stu-id="03603-124">See [Reinstalling and updating packages](../consume-packages/reinstalling-and-updating-packages.md)</span></span>

    <span data-ttu-id="03603-125">Si ve el error "Este proyecto hace referencia a los paquetes NuGet que faltan en este equipo" o "Uno o varios paquetes de NuGet se deben restaurar, pero no pudieron restaurarse porque no se ha concedido el consentimiento", active la restauración automática mediante las instrucciones descritas en [Habilitar y deshabilitar la restauración de paquetes](#enabling-and-disabling-package-restore).</span><span class="sxs-lookup"><span data-stu-id="03603-125">If you see the error "This project references NuGet package(s) that are missing on this computer" or "One or more NuGet packages need to be restored but couldn't be because consent has not been granted," turn on automatic restore by following the instructions under [Enabling and disabling package restore](#enabling-and-disabling-package-restore).</span></span>

- <span data-ttu-id="03603-126">**CLI de NuGet**: use el comando [nuget restore](../tools/cli-ref-restore.md), que restaura los paquetes incluidos en el archivo de proyecto (vea [PackageReference](../consume-packages/package-references-in-project-files.md)) o en un archivo [packages.config](../reference/packages-config.md).</span><span class="sxs-lookup"><span data-stu-id="03603-126">**NuGet CLI**: use the [nuget restore](../tools/cli-ref-restore.md) command, which restores packages listed in the project file (see [PackageReference](../consume-packages/package-references-in-project-files.md)) or in a [packages.config](../reference/packages-config.md) file.</span></span> <span data-ttu-id="03603-127">También puede especificar un archivo de solución.</span><span class="sxs-lookup"><span data-stu-id="03603-127">You can also specify a solution file.</span></span>

- <span data-ttu-id="03603-128">**MSBuild**: use el comando [msbuild /t:restore](../reference/msbuild-targets.md#restore-target), que restaura los paquetes incluidos en el archivo de proyecto (vea [PackageReference](../consume-packages/package-references-in-project-files.md)).</span><span class="sxs-lookup"><span data-stu-id="03603-128">**MSBuild**: use the [msbuild /t:restore](../reference/msbuild-targets.md#restore-target) command, which restores packages packages listed in the project file (see [PackageReference](../consume-packages/package-references-in-project-files.md)).</span></span> <span data-ttu-id="03603-129">Disponible solo en 4.x y versiones posteriores y MSBuild 15.1 y versiones posteriores, que se incluyen con Visual Studio de 2017.</span><span class="sxs-lookup"><span data-stu-id="03603-129">Available only in NuGet 4.x+ and MSBuild 15.1+, which are included with Visual Studio 2017.</span></span> <span data-ttu-id="03603-130">`nuget restore` y `dotnet restore` usan este comando para los proyectos aplicables.</span><span class="sxs-lookup"><span data-stu-id="03603-130">`nuget restore` and `dotnet restore` both use this command for applicable projects.</span></span>

- <span data-ttu-id="03603-131">**Visual Studio Team Services**: al crear una definición de compilación en Team Services, incluya la tarea [Restaurar NuGet](/vsts/build-release/tasks/package/nuget#restore-nuget-packages) o [.NET Core Restore](/vsts/build-release/tasks/build/dotnet-core#restore-nuget-packages) (Restaurar .NET Core) en la definición antes de cualquier tarea de compilación.</span><span class="sxs-lookup"><span data-stu-id="03603-131">**Visual Studio Team Services**: When creating a build definition on Team Services, include the [NuGet restore](/vsts/build-release/tasks/package/nuget#restore-nuget-packages) or [.NET Core Restore](/vsts/build-release/tasks/build/dotnet-core#restore-nuget-packages) task in the definition before any build task.</span></span> <span data-ttu-id="03603-132">Esta tarea se incluye de forma predeterminada en una serie de plantillas de compilación.</span><span class="sxs-lookup"><span data-stu-id="03603-132">This task is included by default in a number of build templates.</span></span>

- <span data-ttu-id="03603-133">**Team Foundation Server**: TFS 2013 con TFS 2013 y versiones posteriores, los paquetes se restauran automáticamente de forma predeterminada durante la compilación, siempre que se use una plantilla de Team Build para TFS 2013 o posterior.</span><span class="sxs-lookup"><span data-stu-id="03603-133">**Team Foundation Server**: TFS 2013 and later automatically restores packages during build, provided that you're using a Team Build Template for TFS 2013 or later.</span></span> <span data-ttu-id="03603-134">Para la versión anterior de TFS, puede incluir un paso de compilación que invoque una de las opciones de restauración de línea de comandos anteriores.</span><span class="sxs-lookup"><span data-stu-id="03603-134">For earlier version of TFS, you can include a build step to invoke one of the command-line restore options above.</span></span> <span data-ttu-id="03603-135">También tiene la posibilidad de migrar la plantilla de compilación a TFS 2013.</span><span class="sxs-lookup"><span data-stu-id="03603-135">You can optionally migrate the build template to TFS 2013.</span></span> <span data-ttu-id="03603-136">Para obtener más información, vea el [tutorial sobre restauración de paquetes con Team Foundation Build](../consume-packages/team-foundation-build.md).</span><span class="sxs-lookup"><span data-stu-id="03603-136">For more information, see the [Walkthrough of package restore with Team Foundation Build](../consume-packages/team-foundation-build.md).</span></span>

## <a name="enabling-and-disabling-package-restore"></a><span data-ttu-id="03603-137">Habilitar y deshabilitar la restauración de paquetes</span><span class="sxs-lookup"><span data-stu-id="03603-137">Enabling and disabling package restore</span></span>

<span data-ttu-id="03603-138">La restauración de paquetes se habilita principalmente a través de **Herramientas > Opciones > Administrador de paquetes NuGet** en Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="03603-138">Package restore is primarily enabled through **Tools > Options > NuGet Package Manager** in Visual Studio:</span></span>

![Control de los comportamientos de restauración de paquetes a través de las opciones del Administrador de paquetes NuGet](media/Restore-01-AutoRestoreOptions.png)

- <span data-ttu-id="03603-140">**Permitir a NuGet descargar los paquetes que falten**: controla todas las formas de restauración de paquetes cambiando la opción `packageRestore/enabled` en el archivo `NuGet.Config` como se muestra aquí (`%AppData%\NuGet\NuGet.Config` en Windows, `~/.nuget/NuGet/NuGet.Config` en Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="03603-140">**Allow NuGet to download missing packages**: controls all forms of package restore by changing the `packageRestore/enabled` setting in the `NuGet.Config` file as shown below (`%AppData%\NuGet\NuGet.Config` on Windows, `~/.nuget/NuGet/NuGet.Config` on Mac/Linux).</span></span> <span data-ttu-id="03603-141">En Visual Studio, este valor permite que funcione el comando **Restaurar paquetes NuGet** en el menú contextual de la solución.</span><span class="sxs-lookup"><span data-stu-id="03603-141">In Visual Studio, this setting allows the **Restore NuGet Packages** command on the solution's context menu to work.</span></span>

    ```xml
    <configuration>
        <packageRestore>
            <!-- The 'enabled' key is True when the "Allow NuGet to download missing packages" checkbox is set.
                 Clearing the box sets this to False, disabling command-line, automatic, and MSBuild-Integrated restore. -->
            <add key="enabled" value="True" />
        </packageRestore>
    </configuration>
    ```
    <br/>
    > [!Note]
    >  <span data-ttu-id="03603-142">La opción `packageRestore/enabled` se puede invalidar de forma global estableciendo una variable de entorno denominada **EnableNuGetPackageRestore** con un valor de TRUE o FALSE antes de iniciar Visual Studio o una compilación.</span><span class="sxs-lookup"><span data-stu-id="03603-142">The `packageRestore/enabled` setting can be overridden globally by setting an environment variable called **EnableNuGetPackageRestore** with a value of TRUE or FALSE before launching Visual Studio or starting a build.</span></span>

- <span data-ttu-id="03603-143">**Comprobar automáticamente los paquetes que falten durante la compilación en Visual Studio**: controla la restauración automática cambiando el ajuste `packageRestore/automatic` en el archivo `NuGet.Config` tal y como se muestra aquí (`%AppData%\NuGet\NuGet.Config` en Windows, `~/.nuget/NuGet/NuGet.Config` en Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="03603-143">**Automatically check for missing packages during build in Visual Studio**: controls automatic restore by changing the `packageRestore/automatic` setting in the `NuGet.Config` file as shown below (`%AppData%\NuGet\NuGet.Config` on Windows, `~/.nuget/NuGet/NuGet.Config` on Mac/Linux).</span></span> <span data-ttu-id="03603-144">Cuando se establece esta opción, al ejecutar una compilación de Visual Studio se restauran automáticamente todos los paquetes que falten.</span><span class="sxs-lookup"><span data-stu-id="03603-144">When this option is set, running a build from Visual Studio automatically restores any missing packages.</span></span> <span data-ttu-id="03603-145">La opción no afecta a las compilaciones que se ejecutan desde la línea de comandos con MSBuild.</span><span class="sxs-lookup"><span data-stu-id="03603-145">The option does not affect builds run from the command line using MSBuild.</span></span>

    ```xml
    ...
    <configuration>
        <packageRestore>
            <!-- The 'automatic' key is set to True when the "Automatically check for missing packages during
                 build in Visual Studio" checkbox is set. Clearing the box sets this to False and disables
                 automatic restore. -->
            <add key="automatic" value="True" />
        </packageRestore>
    </configuration>
    ```

<span data-ttu-id="03603-146">Como referencia, vea el [archivo de configuración de NuGet: sección packageRestore](../reference/nuget-config-file.md#packagerestore-section).</span><span class="sxs-lookup"><span data-stu-id="03603-146">For reference, see the [NuGet config file - packageRestore section](../reference/nuget-config-file.md#packagerestore-section).</span></span>

<span data-ttu-id="03603-147">En algunos casos, es posible que un desarrollador o una empresa quiera habilitar o deshabilitar la restauración de paquetes para todos los usuarios de un equipo.</span><span class="sxs-lookup"><span data-stu-id="03603-147">In some cases, a developer or company might want to enable or disable package restore for all users on a computer.</span></span> <span data-ttu-id="03603-148">Para ello, agregue la misma configuración anterior al archivo de configuración global de NuGet que se encuentra en `%ProgramData%\NuGet\Config[\{IDE}[\{Version}[\{SKU}]]]`.</span><span class="sxs-lookup"><span data-stu-id="03603-148">This is done by adding the same settings above to the global NuGet configuration file located in `%ProgramData%\NuGet\Config[\{IDE}[\{Version}[\{SKU}]]]`.</span></span> <span data-ttu-id="03603-149">Después, los usuarios individuales pueden habilitar la restauración de forma selectiva cuando sea necesario en un nivel de proyecto.</span><span class="sxs-lookup"><span data-stu-id="03603-149">Individual users can then selectively enable restore as needed on a project level.</span></span> <span data-ttu-id="03603-150">Vea [Configuración del comportamiento de NuGet](../consume-packages/configuring-nuget-behavior.md#how-settings-are-applied) para obtener información exacta sobre cómo prioriza NuGet varios archivos de configuración.</span><span class="sxs-lookup"><span data-stu-id="03603-150">See [Configuring NuGet behavior](../consume-packages/configuring-nuget-behavior.md#how-settings-are-applied) for exact details on how NuGet prioritizes multiple config files.</span></span>

## <a name="constraining-package-versions-with-restore"></a><span data-ttu-id="03603-151">Restricción de versiones de paquetes con la restauración</span><span class="sxs-lookup"><span data-stu-id="03603-151">Constraining package versions with restore</span></span>

<span data-ttu-id="03603-152">Cuando NuGet restaure paquetes por cualquier método, respetará las restricciones especificadas en `packages.config` o el archivo de proyecto:</span><span class="sxs-lookup"><span data-stu-id="03603-152">When restoring packages through any method, NuGet honors any constraints specified in `packages.config` or the project file:</span></span>

- <span data-ttu-id="03603-153">`packages.config`: especifique un intervalo de versiones en la propiedad `allowedVersion` de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="03603-153">`packages.config`: Specify a version range in the `allowedVersion` property of the dependency.</span></span> <span data-ttu-id="03603-154">Vea [Reinstalación y actualización de paquetes](../consume-packages/reinstalling-and-updating-packages.md#constraining-upgrade-versions).</span><span class="sxs-lookup"><span data-stu-id="03603-154">See [Reinstalling and updating packages](../consume-packages/reinstalling-and-updating-packages.md#constraining-upgrade-versions).</span></span> <span data-ttu-id="03603-155">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="03603-155">For example:</span></span>

    ```xml
    <package id="Newtonsoft.json" version="6.0.4" allowedVersions="[6,7)" />
    ```

- <span data-ttu-id="03603-156">PackageReference: especifique un intervalo de versiones directamente con el número de versión de la dependencia.</span><span class="sxs-lookup"><span data-stu-id="03603-156">PackageReference: Specify a version range directly with the dependency's version number.</span></span> <span data-ttu-id="03603-157">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="03603-157">For example:</span></span>

    ```xml
    <PackageReference Include="Newtonsoft.json" Version="[6, 7)" />
    ```

<span data-ttu-id="03603-158">En todos los casos, use la notación que se describe en [Package versioning](../reference/package-versioning.md) (Control de versiones de paquetes).</span><span class="sxs-lookup"><span data-stu-id="03603-158">In all cases, use the notation described in [Package versioning](../reference/package-versioning.md).</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="03603-159">Solución de problemas</span><span class="sxs-lookup"><span data-stu-id="03603-159">Troubleshooting</span></span>

<span data-ttu-id="03603-160">Vea [Solucionar problemas de errores de restauración de paquetes en Visual Studio](package-restore-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="03603-160">See [Troubleshooting package restore](package-restore-troubleshooting.md).</span></span>