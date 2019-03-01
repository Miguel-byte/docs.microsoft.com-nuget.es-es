---
title: Cómo publicar paquetes de símbolos de NuGet con el nuevo formato de paquete de símbolos ".snupkg" | Microsoft Docs
author:
- cristinamanu
- kraigb
ms.author:
- cristinamanu
- kraigb
manager: skofman
ms.date: 10/30/2018
ms.topic: reference
ms.prod: nuget
ms.technology: ''
description: Cómo crear paquetes de símbolos de NuGet (snupkg).
keywords: Paquetes de símbolos de NuGet, depuración de paquetes de NuGet, compatibilidad con la depuración de NuGet, símbolos de paquetes, convenciones de paquetes de símbolos
ms.reviewer:
- anangaur
- karann
ms.openlocfilehash: 43f346dc64ebbc59d02b9c7875b04205d8c5d83a
ms.sourcegitcommit: b6efd4b210d92bf163c67e412ca9a5a018d117f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56852447"
---
# <a name="creating-symbol-packages-snupkg"></a><span data-ttu-id="52e63-104">Crear paquetes de símbolos (.snupkg)</span><span class="sxs-lookup"><span data-stu-id="52e63-104">Creating symbol packages (.snupkg)</span></span>

<span data-ttu-id="52e63-105">Los paquetes de símbolos permiten mejorar la experiencia de depuración de los paquetes de NuGet.</span><span class="sxs-lookup"><span data-stu-id="52e63-105">Symbol packages allow you to improve the debugging experience of your NuGet packages.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52e63-106">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="52e63-106">Prerequisites</span></span>

<span data-ttu-id="52e63-107">[nuget.exe v4.9.0 o una versión superior](https://www.nuget.org/downloads) o [dotnet.exe v2.2.0 o una versión superior](https://www.microsoft.com/net/download/dotnet-core/2.2), que implementan los [protocolos de NuGet](../api/nuget-protocols.md) requeridos.</span><span class="sxs-lookup"><span data-stu-id="52e63-107">[nuget.exe v4.9.0 or above](https://www.nuget.org/downloads) or [dotnet.exe v2.2.0 or above](https://www.microsoft.com/net/download/dotnet-core/2.2), which implement the required [NuGet protocols](../api/nuget-protocols.md).</span></span>

## <a name="creating-a-symbol-package"></a><span data-ttu-id="52e63-108">Crear un paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="52e63-108">Creating a symbol package</span></span>

<span data-ttu-id="52e63-109">Puede crear un paquete de símbolos snupkg mediante dotnet.exe, NuGet.exe o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="52e63-109">You can create a snupkg symbol package using dotnet.exe, NuGet.exe, or MSBuild.</span></span> <span data-ttu-id="52e63-110">Si usa NuGet.exe, puede emplear los siguientes comandos para crear un archivo .snupkg, además del archivo .nupkg:</span><span class="sxs-lookup"><span data-stu-id="52e63-110">If you're using NuGet.exe, you can use the following commands to create a .snupkg file in addition to the .nupkg file:</span></span>

```
nuget pack MyPackage.nuspec -Symbols -SymbolPackageFormat snupkg

nuget pack MyPackage.csproj -Symbols -SymbolPackageFormat snupkg
```

<span data-ttu-id="52e63-111">Si usa dotnet.exe o MSBuild, siga los siguientes pasos para crear un archivo .snupkg, además del archivo .nupkg:</span><span class="sxs-lookup"><span data-stu-id="52e63-111">If you're using dotnet.exe or MSBuild, use the following steps to create a .snupkg file in addition to the .nupkg file:</span></span>

1. <span data-ttu-id="52e63-112">Agregue las siguientes propiedades al archivo .csproj:</span><span class="sxs-lookup"><span data-stu-id="52e63-112">Add the following properties to your .csproj file:</span></span>

    ```xml
    <PropertyGroup>
      <IncludeSymbols>true</IncludeSymbols>
      <SymbolPackageFormat>snupkg</SymbolPackageFormat>
    </PropertyGroup>
    ```

1. <span data-ttu-id="52e63-113">Empaquete el proyecto con `dotnet pack MyPackage.csproj` o `msbuild -t:pack MyPackage.csproj`.</span><span class="sxs-lookup"><span data-stu-id="52e63-113">Pack your project with `dotnet pack MyPackage.csproj` or `msbuild -t:pack MyPackage.csproj`.</span></span>

<span data-ttu-id="52e63-114">La propiedad `SymbolPackageFormat` puede tener uno de estos dos valores: `symbols.nupkg` (predeterminado) o `snupkg`.</span><span class="sxs-lookup"><span data-stu-id="52e63-114">The `SymbolPackageFormat` property can have one of the two values: `symbols.nupkg` (the default) or `snupkg`.</span></span> <span data-ttu-id="52e63-115">Si no se especifica la propiedad `SymbolPackageFormat`, el valor predeterminado es `symbols.nupkg` y se crea un paquete de símbolos heredado.</span><span class="sxs-lookup"><span data-stu-id="52e63-115">If the `SymbolPackageFormat` property is not specified, it defaults to `symbols.nupkg` and a legacy symbol package will be created.</span></span>

> [!Note]
> <span data-ttu-id="52e63-116">El formato heredado `.symbols.nupkg` todavía se admite, pero solo por motivos de compatibilidad (vea [Paquetes de símbolos heredados](Symbol-Packages.md)).</span><span class="sxs-lookup"><span data-stu-id="52e63-116">The legacy format `.symbols.nupkg` is still supported but only for compatibility reasons (see [Legacy Symbol Packages](Symbol-Packages.md)).</span></span> <span data-ttu-id="52e63-117">El servidor de símbolos de NuGet.org solo acepta el nuevo formato de paquete de símbolos, `.snupkg`.</span><span class="sxs-lookup"><span data-stu-id="52e63-117">NuGet.org symbols server only accepts the new symbol package format - `.snupkg`.</span></span>

## <a name="publishing-a-symbol-package"></a><span data-ttu-id="52e63-118">Publicar un paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="52e63-118">Publishing a symbol package</span></span>

1. <span data-ttu-id="52e63-119">Para su comodidad, guarde primero la clave de API con NuGet (vea [publicar un paquete](../create-packages/publish-a-package.md)).</span><span class="sxs-lookup"><span data-stu-id="52e63-119">For convenience, first save your API key with NuGet (see [publish a package](../create-packages/publish-a-package.md)).</span></span>

    ```cli
    nuget SetApiKey Your-API-Key
    ```

1. <span data-ttu-id="52e63-120">Después de publicar el paquete principal en nuget.org, inserte el paquete de símbolos tal y como se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="52e63-120">After publishing your primary package to nuget.org, push the symbol package as follows.</span></span>

    ```cli
    nuget push MyPackage.snupkg
    ```

1. <span data-ttu-id="52e63-121">También puede insertar ambos paquetes al mismo tiempo con el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="52e63-121">You can also push both primary and symbol packages at the same time using the below command.</span></span> <span data-ttu-id="52e63-122">Tanto los archivos .nupkg como .snupkg deben estar presentes en la carpeta actual.</span><span class="sxs-lookup"><span data-stu-id="52e63-122">Both .nupkg and .snupkg files need to be present in the current folder.</span></span>

    ```cli
    nuget push MyPackage.nupkg
    ```

<span data-ttu-id="52e63-123">NuGet publicará ambos paquetes en nuget.org. `MyPackage.nupkg` se publica en primer lugar, y luego `MyPackage.snupkg`.</span><span class="sxs-lookup"><span data-stu-id="52e63-123">NuGet will publish both packages to nuget.org. `MyPackage.nupkg` will be published first, followed by `MyPackage.snupkg`.</span></span>

## <a name="nugetorg-symbol-server"></a><span data-ttu-id="52e63-124">Servidor de símbolos de NuGet.org</span><span class="sxs-lookup"><span data-stu-id="52e63-124">NuGet.org symbol server</span></span>

<span data-ttu-id="52e63-125">NuGet.org admite su propio repositorio de servidor de símbolos y solo acepta el nuevo formato de paquete de símbolos, `.snupkg`.</span><span class="sxs-lookup"><span data-stu-id="52e63-125">NuGet.org supports its own symbols server repository and only accepts the new symbol package format - `.snupkg`.</span></span> <span data-ttu-id="52e63-126">Los consumidores de paquetes pueden usar los símbolos publicados en el servidor de símbolos de nuget.org agregando `https://symbols.nuget.org/download/symbols` a sus orígenes de símbolos en Visual Studio, que permite entrar en el código del paquete en el depurador de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="52e63-126">Package consumers can use the symbols published to nuget.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their symbol sources in Visual Studio, which allows stepping into package code in the Visual Studio debugger.</span></span> <span data-ttu-id="52e63-127">Vea [Especificar archivos de código fuente y símbolos (.pdb) en el depurador de Visual Studio](https://docs.microsoft.com/en-us/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger?view=vs-2017) para obtener información detallada sobre ese proceso.</span><span class="sxs-lookup"><span data-stu-id="52e63-127">See [Specify symbol (.pdb) and source files in the Visual Studio debugger](https://docs.microsoft.com/en-us/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger?view=vs-2017) for details on that process.</span></span>

### <a name="nugetorg-symbol-package-constraints"></a><span data-ttu-id="52e63-128">Restricciones de paquete de símbolos de Nuget.org</span><span class="sxs-lookup"><span data-stu-id="52e63-128">Nuget.org symbol package constraints</span></span>

<span data-ttu-id="52e63-129">Los paquetes de símbolos admitidos en nuget.org tienen las siguientes restricciones:</span><span class="sxs-lookup"><span data-stu-id="52e63-129">The symbol packages supported on nuget.org have the following contraints</span></span>

- <span data-ttu-id="52e63-130">Solo se permite agregar las siguientes extensiones a un paquete de símbolos.</span><span class="sxs-lookup"><span data-stu-id="52e63-130">Only the following file extensions are allowed to be added to a symbol package.</span></span> ```.pdb,.nuspec,.xml,.psmdcp,.rels,.p7s```
- <span data-ttu-id="52e63-131">En estos momentos, solo se admiten archivos [pdb portátiles](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.Metadata/specs/PortablePdb-Metadata.md) en el servidor de símbolos de nuget.</span><span class="sxs-lookup"><span data-stu-id="52e63-131">Only managed [Portable pdbs](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.Metadata/specs/PortablePdb-Metadata.md) are currently supported on nuget symbol server.</span></span>
- <span data-ttu-id="52e63-132">Los archivos pdb y los dll de nupkg asociados deben compilarse con el compilador de la versión 15.9 de Visual Studio o una superior (vea [hash criptográfico de pdb](https://github.com/dotnet/roslyn/issues/24429)).</span><span class="sxs-lookup"><span data-stu-id="52e63-132">The pdbs and associated nupkg dlls need to be built with the compiler in Visual Studio version 15.9 or above (see [pdb crypto hash](https://github.com/dotnet/roslyn/issues/24429))</span></span>

<span data-ttu-id="52e63-133">La publicación del paquete de símbolos en nuget.org producirá un error si cualquiera de los otros tipos de archivo se incluyen en el archivo .snupkg.</span><span class="sxs-lookup"><span data-stu-id="52e63-133">The symbol package publish on nuget.org will fail if any other file types are included in the .snupkg.</span></span>

### <a name="symbol-package-validation-and-indexing"></a><span data-ttu-id="52e63-134">Validación e indexación de paquetes de símbolos</span><span class="sxs-lookup"><span data-stu-id="52e63-134">Symbol package validation and indexing</span></span>

<span data-ttu-id="52e63-135">Los paquetes de símbolos publicados en [NuGet.org](https://www.nuget.org/) se someten a varias validaciones, como comprobaciones de virus.</span><span class="sxs-lookup"><span data-stu-id="52e63-135">Symbol packages published to [NuGet.org](https://www.nuget.org/) undergo several validations, such as virus checks.</span></span>

<span data-ttu-id="52e63-136">Cuando el paquete haya pasado todas las comprobaciones de validación, tardará un tiempo para que los símbolos se indexen y estén disponibles para su consumo desde los servidores de símbolos de NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="52e63-136">When the package has passed all validation checks, it might take a while for the symbols to index and be available for consumption from the NuGet.org symbol servers.</span></span> <span data-ttu-id="52e63-137">Si se produce un error de comprobación de validación en el paquete, la página de detalles del archivo .nupkg se actualizará y mostrará el error correspondiente. También recibirá un correo electrónico en el que se le notificará este extremo.</span><span class="sxs-lookup"><span data-stu-id="52e63-137">If the package fails a validation check, the package details page for the .nupkg will update to display the associated error and you will also receive an email notifying you about it.</span></span>

<span data-ttu-id="52e63-138">La validación y la indexación del paquete suelen tardar menos de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="52e63-138">Package validation and indexing usually takes under 15 minutes.</span></span> <span data-ttu-id="52e63-139">Si la publicación del paquete tarda más de lo esperado, visite [status.nuget.org](https://status.nuget.org/) para comprobar si nuget.org está experimentando alguna interrupción.</span><span class="sxs-lookup"><span data-stu-id="52e63-139">If the package publishing is taking longer than expected, visit [status.nuget.org](https://status.nuget.org/) to check if nuget.org is experiencing any interruptions.</span></span> <span data-ttu-id="52e63-140">Si todos los sistemas están operativos y el paquete no se ha publicado correctamente en una hora, inicie sesión en nuget.org y póngase en contacto con nosotros mediante el vínculo de contacto con el equipo de soporte técnico de la página de detalles del paquete.</span><span class="sxs-lookup"><span data-stu-id="52e63-140">If all systems are operational and the package hasn't been successfully published within an hour, please login to nuget.org and contact us using the Contact Support link on the package details page.</span></span>

## <a name="symbol-package-structure"></a><span data-ttu-id="52e63-141">Estructura del paquete de símbolos</span><span class="sxs-lookup"><span data-stu-id="52e63-141">Symbol package structure</span></span>

<span data-ttu-id="52e63-142">El archivo .nupkg debería ser exactamente el mismo que el de hoy, pero el archivo .snupkg debería tener las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="52e63-142">The .nupkg file would be exactly the same as it is today, but the .snupkg file would have the following characteristics:</span></span>

1) <span data-ttu-id="52e63-143">El archivo .snupkg debe tener el mismo id. y la misma versión que el archivo .nupkg correspondiente.</span><span class="sxs-lookup"><span data-stu-id="52e63-143">The .snupkg will have the same id and version as the corresponding .nupkg.</span></span>
2) <span data-ttu-id="52e63-144">El archivo .snupkg debe tener la misma estructura de carpetas exacta que el archivo .nupkg para cualquier archivo DLL o EXE con distinción de que, en vez de los archivos DLL o EXE, los archivos PDB correspondientes deben estar incluidos en la misma jerarquía de carpetas.</span><span class="sxs-lookup"><span data-stu-id="52e63-144">The .snupkg will have the exact folder structure as the nupkg for any DLL or EXE files with the distinction that instead of DLLs/EXEs, their corresponding PDBs will be included in the same folder hierarchy.</span></span> <span data-ttu-id="52e63-145">El archivo .snupkg no debe incluir ningún archivos o carpetas con extensiones que no sean PDB.</span><span class="sxs-lookup"><span data-stu-id="52e63-145">Files and folders with extensions other than PDB will be left out of the snupkg.</span></span>
3) <span data-ttu-id="52e63-146">El archivo .nuspec del archivo .snupkg también debe especificar un nuevo PackageType, tal y como se muestra a continuación.</span><span class="sxs-lookup"><span data-stu-id="52e63-146">The .nuspec file in the .snupkg will also specify a new PackageType as below.</span></span> <span data-ttu-id="52e63-147">Este debería ser el único PackageType especificado.</span><span class="sxs-lookup"><span data-stu-id="52e63-147">This should the only one PackageType specified.</span></span> 
``` 
<packageTypes>
  <packageType name="SymbolsPackage"/>
</packageTypes>
```
4) <span data-ttu-id="52e63-148">Si un autor decide usar un archivo .nuspec personalizado para compilar sus archivos .nupkg y .snupkg, estos deben tener la misma jerarquía de carpetas y archivos mostrados en el punto 2.</span><span class="sxs-lookup"><span data-stu-id="52e63-148">If an author decides to use a custom nuspec to build their nupkg and snupkg, the snupkg should have the same folder hierarchy and files detailed in 2).</span></span>
5) <span data-ttu-id="52e63-149">Los campos ```authors``` y ```owners``` deben excluirse del archivo .nuspec del archivo .snupkg.</span><span class="sxs-lookup"><span data-stu-id="52e63-149">```authors``` and ```owners``` field will be excluded from the snupkg's nuspec.</span></span>

## <a name="see-also"></a><span data-ttu-id="52e63-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="52e63-150">See Also</span></span>

[<span data-ttu-id="52e63-151">NuGet-Package-Debugging-&-Symbols-Improvements</span><span class="sxs-lookup"><span data-stu-id="52e63-151">NuGet-Package-Debugging-&-Symbols-Improvements</span></span>](https://github.com/NuGet/Home/wiki/NuGet-Package-Debugging-&-Symbols-Improvements)
