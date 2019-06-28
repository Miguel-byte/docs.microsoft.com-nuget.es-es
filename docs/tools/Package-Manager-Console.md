---
title: Instalar y administrar paquetes de NuGet con PowerShell en Visual Studio
description: Instrucciones para usar la consola de administrador de paquetes de NuGet en Visual Studio para trabajar con paquetes.
author: karann-msft
ms.author: karann
ms.date: 06/24/2019
ms.topic: conceptual
f1_keywords:
- vs.nuget.packagemanager.console
ms.openlocfilehash: 11ec25598d3110ba84dec5044642e205e13346af
ms.sourcegitcommit: b6810860b77b2d50aab031040b047c20a333aca3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67426221"
---
# <a name="install-and-manage-packages-using-powershell-in-visual-studio"></a><span data-ttu-id="9a8d4-103">Instalar y administrar paquetes mediante PowerShell en Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9a8d4-103">Install and manage packages using PowerShell in Visual Studio</span></span>

<span data-ttu-id="9a8d4-104">La consola de administrador de paquetes de NuGet le permite usar [comandos de PowerShell de NuGet](../tools/powershell-reference.md) para buscar, instalar, desinstalar y actualizar paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-104">The NuGet Package Manager Console lets you use [NuGet PowerShell commands](../tools/powershell-reference.md) to find, install, uninstall, and update NuGet packages.</span></span> <span data-ttu-id="9a8d4-105">Es necesario en casos donde el Administrador de paquetes de UI no proporciona una manera de realizar una operación mediante la consola.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-105">Using the console is necessary in cases where the Package Manager UI does not provide a way to perform an operation.</span></span> <span data-ttu-id="9a8d4-106">Para usar `nuget.exe` comandos de la CLI en la consola, consulte [mediante la CLI de nuget.exe en la consola de](#using-the-nugetexe-cli-in-the-console).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-106">To use `nuget.exe` CLI commands in the console, see [Using the nuget.exe CLI in the console](#using-the-nugetexe-cli-in-the-console).</span></span>

<span data-ttu-id="9a8d4-107">La consola está integrada en Visual Studio en Windows.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-107">The console is built into Visual Studio on Windows.</span></span> <span data-ttu-id="9a8d4-108">No se incluye con Visual Studio para Mac o Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-108">It is not included with Visual Studio for Mac or Visual Studio Code.</span></span>

## <a name="find-and-install-a-package"></a><span data-ttu-id="9a8d4-109">Buscar e instalar un paquete</span><span class="sxs-lookup"><span data-stu-id="9a8d4-109">Find and install a package</span></span>

<span data-ttu-id="9a8d4-110">Por ejemplo, la búsqueda e instalación de un paquete se realiza con tres sencillos pasos:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-110">For example, finding and installing a package is done with three easy steps:</span></span>

1. <span data-ttu-id="9a8d4-111">Abra el proyecto o solución en Visual Studio y abra la consola utilizando la **Herramientas > Administrador de paquetes NuGet > consola del Administrador de paquetes** comando.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-111">Open the project/solution in Visual Studio, and open the console using the **Tools > NuGet Package Manager > Package Manager Console** command.</span></span>

1. <span data-ttu-id="9a8d4-112">Busque el paquete que desea instalar.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-112">Find the package you want to install.</span></span> <span data-ttu-id="9a8d4-113">Si ya sabe esto, vaya al paso 3.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-113">If you already know this, skip to step 3.</span></span>

    ```ps
    # Find packages containing the keyword "elmah"
    Find-Package elmah
    ```

1. <span data-ttu-id="9a8d4-114">Ejecute el comando de instalación:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-114">Run the install command:</span></span>

    ```ps
    # Install the Elmah package to the project named MyProject.
    Install-Package Elmah -ProjectName MyProject
    ```

> [!Important]
> <span data-ttu-id="9a8d4-115">Todas las operaciones que están disponibles en la consola también se pueden hacer con el [CLI de NuGet](../tools/nuget-exe-cli-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-115">All operations that are available in the console can also be done with the [NuGet CLI](../tools/nuget-exe-cli-reference.md).</span></span> <span data-ttu-id="9a8d4-116">Sin embargo, los comandos de consola operan dentro del contexto de Visual Studio y una proyecto o solución guardada y a menudo llevar más de sus comandos equivalente de la CLI.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-116">However, console commands operate within the context of Visual Studio and a saved project/solution and often accomplish more than their equivalent CLI commands.</span></span> <span data-ttu-id="9a8d4-117">Por ejemplo, instalar un paquete a través de la consola, agrega una referencia al proyecto mientras que el comando de CLI no.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-117">For example, installing a package through the console adds a reference to the project whereas the CLI command does not.</span></span> <span data-ttu-id="9a8d4-118">Por este motivo, los desarrolladores que trabajan en Visual Studio normalmente prefieren usar la consola de la CLI.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-118">For this reason, developers working in Visual Studio typically prefer using the console to the CLI.</span></span>

> [!Tip]
> <span data-ttu-id="9a8d4-119">Muchas operaciones de la consola dependen de tener una solución abierta en Visual Studio con un nombre de ruta de acceso conocida.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-119">Many console operations depend on having a solution opened in Visual Studio with a known path name.</span></span> <span data-ttu-id="9a8d4-120">Si tiene una solución que no haya guardado o no hay ninguna solución, puede ver el error, "solución no es abrir o no guarda.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-120">If you have an unsaved solution, or no solution, you can see the error, "Solution is not opened or not saved.</span></span> <span data-ttu-id="9a8d4-121">Asegúrese de que tener una solución abierta y guardada."</span><span class="sxs-lookup"><span data-stu-id="9a8d4-121">Please ensure you have an open and saved solution."</span></span> <span data-ttu-id="9a8d4-122">Esto indica que la consola no puede determinar la carpeta de soluciones.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-122">This indicates that the console cannot determine the solution folder.</span></span> <span data-ttu-id="9a8d4-123">Guardar una solución que no haya guardado, o crear y guardar una solución si no tiene uno abierto, debe corregir el error.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-123">Saving an unsaved solution, or creating and saving a solution if you don't have one open, should correct the error.</span></span>

## <a name="opening-the-console-and-console-controls"></a><span data-ttu-id="9a8d4-124">Abra la consola y los controles de la consola</span><span class="sxs-lookup"><span data-stu-id="9a8d4-124">Opening the console and console controls</span></span>

1. <span data-ttu-id="9a8d4-125">Abra la consola en Visual Studio mediante el **Herramientas > Administrador de paquetes NuGet > consola del Administrador de paquetes** comando.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-125">Open the console in Visual Studio using the **Tools > NuGet Package Manager > Package Manager Console** command.</span></span> <span data-ttu-id="9a8d4-126">La consola es una ventana de Visual Studio que se puede organizar y colocada que desee (vea [personalizar los diseños de ventana de Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio)).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-126">The console is a Visual Studio window that can be arranged and positioned however you like (see [Customize window layouts in Visual Studio](/visualstudio/ide/customizing-window-layouts-in-visual-studio)).</span></span>

1. <span data-ttu-id="9a8d4-127">De forma predeterminada, los comandos de consola funcionan con un origen de paquete específico y un proyecto como se establece en el control en la parte superior de la ventana:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-127">By default, console commands operate against a specific package source and project as set in the control at the top of the window:</span></span>

    ![Controles de la consola de administrador de paquetes para el origen del paquete y proyecto](media/PackageManagerConsoleControls1.png)

1. <span data-ttu-id="9a8d4-129">Seleccionar un origen de otro paquete o proyecto cambia los valores predeterminados para los comandos siguientes.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-129">Selecting a different package source and/or project changes those defaults for subsequent commands.</span></span> <span data-ttu-id="9a8d4-130">Anular estos valores sin cambiar los valores predeterminados, mayoría de los comandos admite `-Source` y `-ProjectName` opciones.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-130">To overrride these settings without changing the defaults, most commands support `-Source` and `-ProjectName` options.</span></span>

1. <span data-ttu-id="9a8d4-131">Para administrar orígenes de paquetes, seleccione el icono de engranaje.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-131">To manage package sources, select the gear icon.</span></span> <span data-ttu-id="9a8d4-132">Se trata de un acceso directo a la **Herramientas > Opciones > Administrador de paquetes NuGet > orígenes del paquete** cuadro de diálogo como se describe en el [UI del Administrador de paquetes](package-manager-ui.md#package-sources) página.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-132">This is a shortcut to the **Tools > Options > NuGet Package Manager > Package Sources** dialog box as described on the [Package Manager UI](package-manager-ui.md#package-sources) page.</span></span> <span data-ttu-id="9a8d4-133">Además, el control a la derecha del selector de proyecto borra el contenido de la consola:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-133">Also, the control to the right of the project selector clears the console's contents:</span></span>

    ![Configuración de la consola de administrador de paquetes y desactive los controles](media/PackageManagerConsoleControls2.png)

1. <span data-ttu-id="9a8d4-135">El botón situado más a interrupciones de un comando de ejecución prolongada.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-135">The rightmost button interrupts a long-running command.</span></span> <span data-ttu-id="9a8d4-136">Por ejemplo, ejecutar `Get-Package -ListAvailable -PageSize 500` se muestran los primeros 500 paquetes en el origen predeterminado (por ejemplo, nuget.org), que puede tardar varios minutos en ejecutarse.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-136">For example, running `Get-Package -ListAvailable -PageSize 500` lists the top 500 packages on the default source (such as nuget.org), which could take several minutes to run.</span></span>

    ![Control de detención de la consola de administrador de paquetes](media/PackageManagerConsoleControls3.png)

## <a name="installing-a-package"></a><span data-ttu-id="9a8d4-138">Instalar un paquete</span><span class="sxs-lookup"><span data-stu-id="9a8d4-138">Installing a package</span></span>

```ps
# Add the Elmah package to the default project as specified in the console's project selector
Install-Package Elmah

# Add the Elmah package to a project named UtilitiesLib that is not the default
Install-Package Elmah -ProjectName UtilitiesLib
```

<span data-ttu-id="9a8d4-139">Consulte [Install-Package](../tools/ps-ref-install-package.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-139">See [Install-Package](../tools/ps-ref-install-package.md).</span></span>

<span data-ttu-id="9a8d4-140">Instalar un paquete en la consola realiza los mismos pasos, tal como se describe en [lo que sucede cuando se instala un paquete](../concepts/package-installation-process.md), con las siguientes adiciones:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-140">Installing a package in the console performs the same steps as described on [What happens when a package is installed](../concepts/package-installation-process.md), with the following additions:</span></span>

- <span data-ttu-id="9a8d4-141">La consola muestra los términos de licencia aplicables en su ventana con un acuerdo implícito.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-141">The Console displays applicable license terms in its window with implied agreement.</span></span> <span data-ttu-id="9a8d4-142">Si no acepta los términos, debe desinstalar el paquete inmediatamente.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-142">If you do not agree to the terms, you should uninstall the package immediately.</span></span>
- <span data-ttu-id="9a8d4-143">También una referencia al paquete se agrega al archivo de proyecto y aparece en **el Explorador de soluciones** bajo el **referencias** nodo, debe guardar el proyecto para ver los cambios en el archivo de proyecto directamente.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-143">Also a reference to the package is added to the project file and appears in **Solution Explorer** under the **References** node, you need to save the project to see the changes in the project file directly.</span></span>

## <a name="uninstalling-a-package"></a><span data-ttu-id="9a8d4-144">Al desinstalar un paquete</span><span class="sxs-lookup"><span data-stu-id="9a8d4-144">Uninstalling a package</span></span>

```ps
# Uninstalls the Elmah package from the default project
Uninstall-Package Elmah

# Uninstalls the Elmah package and all its unused dependencies
Uninstall-Package Elmah -RemoveDependencies 

# Uninstalls the Elmah package even if another package depends on it
Uninstall-Package Elmah -Force
```

<span data-ttu-id="9a8d4-145">Consulte [Uninstall-Package](../tools/ps-ref-uninstall-package.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-145">See [Uninstall-Package](../tools/ps-ref-uninstall-package.md).</span></span> <span data-ttu-id="9a8d4-146">Use [Get-Package](../tools/ps-ref-get-package.md) para ver todos los paquetes instalados actualmente en el proyecto predeterminado, si necesita encontrar un identificador.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-146">Use [Get-Package](../tools/ps-ref-get-package.md) to see all packages currently installed in the default project if you need to find an identifier.</span></span>

<span data-ttu-id="9a8d4-147">Al desinstalar un paquete realiza las acciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-147">Uninstalling a package performs the following actions:</span></span>

- <span data-ttu-id="9a8d4-148">Quita las referencias al paquete del proyecto (y cualquier otro formato de administración está en uso).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-148">Removes references to the package from the project (and whatever management format is in use).</span></span> <span data-ttu-id="9a8d4-149">Las referencias ya no aparecen en **el Explorador de soluciones**.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-149">References no longer appear in **Solution Explorer**.</span></span> <span data-ttu-id="9a8d4-150">(Es posible que deba volver a generar el proyecto para verlo quita de la **Bin** carpeta.)</span><span class="sxs-lookup"><span data-stu-id="9a8d4-150">(You might need to rebuild the project to see it removed from the **Bin** folder.)</span></span>
- <span data-ttu-id="9a8d4-151">Invierte los cambios realizados en `app.config` o `web.config` cuando se instaló el paquete.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-151">Reverses any changes made to `app.config` or `web.config` when the package was installed.</span></span>
- <span data-ttu-id="9a8d4-152">Quita instalada anteriormente dependencias si no hay paquetes restantes utilizan esas dependencias.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-152">Removes previously-installed dependencies if no remaining packages use those dependencies.</span></span>

## <a name="updating-a-package"></a><span data-ttu-id="9a8d4-153">Actualizar un paquete</span><span class="sxs-lookup"><span data-stu-id="9a8d4-153">Updating a package</span></span>

```ps
# Checks if there are newer versions available for any installed packages
Get-Package -updates

# Updates a specific package using its identifier, in this case jQuery
Update-Package jQuery

# Update all packages in the project named MyProject (as it appears in Solution Explorer)
Update-Package -ProjectName MyProject

# Update all packages in the solution
Update-Package
```

<span data-ttu-id="9a8d4-154">Consulte [Get-Package](../tools/ps-ref-get-package.md) y [-paquete de actualización](../tools/ps-ref-update-package.md)</span><span class="sxs-lookup"><span data-stu-id="9a8d4-154">See [Get-Package](../tools/ps-ref-get-package.md) and [Update-Package](../tools/ps-ref-update-package.md)</span></span>

## <a name="finding-a-package"></a><span data-ttu-id="9a8d4-155">Buscar un paquete</span><span class="sxs-lookup"><span data-stu-id="9a8d4-155">Finding a package</span></span>

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

<span data-ttu-id="9a8d4-156">Consulte [Find-Package](../tools/ps-ref-find-package.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-156">See [Find-Package](../tools/ps-ref-find-package.md).</span></span> <span data-ttu-id="9a8d4-157">En Visual Studio 2013 y versiones anteriores, utilice [Get-Package](../tools/ps-ref-get-package.md) en su lugar.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-157">In Visual Studio 2013 and earlier, use [Get-Package](../tools/ps-ref-get-package.md) instead.</span></span>

## <a name="availability-of-the-console"></a><span data-ttu-id="9a8d4-158">Disponibilidad de la consola</span><span class="sxs-lookup"><span data-stu-id="9a8d4-158">Availability of the console</span></span>

<span data-ttu-id="9a8d4-159">A partir de Visual Studio 2017, NuGet y el Administrador de paquetes de NuGet se instalan automáticamente cuando se selecciona cualquiera. Cargas de trabajo relacionados con la red; También puede instalarlo por separado mediante la comprobación de la **componentes individuales > herramientas de código > Administrador de paquetes de NuGet** opción en el instalador de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-159">Starting in Visual Studio 2017, NuGet and the NuGet Package Manager are automatically installed when you select any .NET-related workloads; you can also install it individually by checking the **Individual components > Code tools > NuGet package manager** option in the Visual Studio installer.</span></span>

<span data-ttu-id="9a8d4-160">Además, compruebe si faltan el Administrador de paquetes de NuGet en Visual Studio 2015 y versiones anteriores, **Herramientas > extensiones y actualizaciones...**  y busque la extensión del Administrador de paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-160">Also, if you're missing the NuGet Package Manager in Visual Studio 2015 and earlier, check **Tools > Extensions and Updates...** and search for the NuGet Package Manager extension.</span></span> <span data-ttu-id="9a8d4-161">Si no puede usar el instalador de extensiones de Visual Studio, puede descargar la extensión directamente desde [ https://dist.nuget.org/index.html ](https://dist.nuget.org/index.html).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-161">If you're unable to use the extensions installer in Visual Studio, you can download the extension directly from [https://dist.nuget.org/index.html](https://dist.nuget.org/index.html).</span></span>

<span data-ttu-id="9a8d4-162">La consola de administrador de paquetes no está actualmente disponible con Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-162">The Package Manager Console is not presently available with Visual Studio for Mac.</span></span> <span data-ttu-id="9a8d4-163">Los comandos equivalentes, pero están disponibles a través de la [CLI de NuGet](nuget-exe-CLI-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-163">The equivalent commands, however, are available through the [NuGet CLI](nuget-exe-CLI-reference.md).</span></span> <span data-ttu-id="9a8d4-164">Visual Studio para Mac tiene una interfaz de usuario para administrar paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-164">Visual Studio for Mac does have a UI for managing NuGet packages.</span></span> <span data-ttu-id="9a8d4-165">Consulte [incluir un paquete NuGet en el proyecto](/visualstudio/mac/nuget-walkthrough).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-165">See [Including a NuGet package in your project](/visualstudio/mac/nuget-walkthrough).</span></span>

<span data-ttu-id="9a8d4-166">La consola de administrador de paquetes no se incluye con Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-166">The Package Manager Console is not included with Visual Studio Code.</span></span>

## <a name="extending-the-package-manager-console"></a><span data-ttu-id="9a8d4-167">Extender la consola de administrador de paquetes</span><span class="sxs-lookup"><span data-stu-id="9a8d4-167">Extending the Package Manager Console</span></span>

<span data-ttu-id="9a8d4-168">Algunos paquetes instalan nuevos comandos para la consola.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-168">Some packages install new commands for the console.</span></span> <span data-ttu-id="9a8d4-169">Por ejemplo, `MvcScaffolding` crea comandos como `Scaffold` se muestra a continuación, lo cual genera controladores y vistas MVC de ASP.NET:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-169">For example, `MvcScaffolding` creates commands like `Scaffold` shown below, which generates ASP.NET MVC controllers and views:</span></span>

![Instalar y usar MvcScaffold](media/PackageManagerConsoleInstall.png)

## <a name="setting-up-a-nuget-powershell-profile"></a><span data-ttu-id="9a8d4-171">Configuración de un perfil de PowerShell de NuGet</span><span class="sxs-lookup"><span data-stu-id="9a8d4-171">Setting up a NuGet PowerShell profile</span></span>

<span data-ttu-id="9a8d4-172">Un perfil de PowerShell le permite disponer de los comandos usados frecuentemente allá donde use PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a8d4-172">A PowerShell profile lets you make commonly-used commands available wherever you use PowerShell.</span></span> <span data-ttu-id="9a8d4-173">NuGet es compatible con un perfil específico NuGet que normalmente se encuentran en la siguiente ubicación:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-173">NuGet supports a NuGet-specific profile typically found at the following location:</span></span>

    %UserProfile%\Documents\WindowsPowerShell\NuGet_profile.ps1

<span data-ttu-id="9a8d4-174">Para encontrar el perfil, escriba `$profile` en la consola:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-174">To find the profile, type `$profile` in the console:</span></span>

```ps
$profile
C:\Users\<user>\Documents\WindowsPowerShell\NuGet_profile.ps1
```

<span data-ttu-id="9a8d4-175">Para obtener más información, consulte [perfiles de Windows PowerShell](https://technet.microsoft.com/library/bb613488.aspx).</span><span class="sxs-lookup"><span data-stu-id="9a8d4-175">For more details, refer to [Windows PowerShell Profiles](https://technet.microsoft.com/library/bb613488.aspx).</span></span>

## <a name="using-the-nugetexe-cli-in-the-console"></a><span data-ttu-id="9a8d4-176">Uso de la CLI de nuget.exe en la consola</span><span class="sxs-lookup"><span data-stu-id="9a8d4-176">Using the nuget.exe CLI in the console</span></span>

<span data-ttu-id="9a8d4-177">Para realizar la [ `nuget.exe` CLI](nuget-exe-cli-reference.md) disponibles en la consola de administrador de paquetes, instale el [NuGet.CommandLine](http://www.nuget.org/packages/NuGet.CommandLine/) paquete desde la consola:</span><span class="sxs-lookup"><span data-stu-id="9a8d4-177">To make the [`nuget.exe` CLI](nuget-exe-cli-reference.md) available in the Package Manager Console, install the [NuGet.CommandLine](http://www.nuget.org/packages/NuGet.CommandLine/) package from the console:</span></span>

```ps
# Other versions are available, see http://www.nuget.org/packages/NuGet.CommandLine/
Install-Package NuGet.CommandLine -Version 4.4.1
```
