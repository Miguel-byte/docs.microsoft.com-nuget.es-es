---
title: Creación de paquetes con ensamblados de interoperabilidad COM
description: En este artículo se describe cómo crear paquetes que contengan ensamblados de interoperabilidad COM.
author: karann-msft
ms.author: karann
ms.date: 07/09/2019
ms.topic: conceptual
ms.openlocfilehash: d0e368f43171ce71abc60b3e09d08b010d2d8880
ms.sourcegitcommit: 0dea3b153ef823230a9d5f38351b7cef057cb299
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "67843487"
---
## <a name="create-nuget-packages-that-contain-com-interop-assemblies"></a>Creación de paquetes NuGet que contengan ensamblados de interoperabilidad COM

Los paquetes que contienen ensamblados de interoperabilidad COM deben incluir un [archivo de destinos](creating-a-package.md#include-msbuild-props-and-targets-in-a-package) adecuado para que los metadatos `EmbedInteropTypes` correctos se agreguen a los proyectos con el formato PackageReference. De forma predeterminada, los metadatos `EmbedInteropTypes` siempre son false para todos los ensamblados cuando se usa PackageReference, por lo que el archivo de destinos agrega estos metadatos de manera explícita. Para evitar conflictos, el nombre del destino debe ser único; lo ideal es usar una combinación del nombre del paquete y del ensamblado que se va a insertar, reemplazando el `{InteropAssemblyName}` en el ejemplo siguiente con ese valor. (Vea también [NuGet.Samples.Interop](https://github.com/NuGet/Samples/tree/master/NuGet.Samples.Interop) para obtener un ejemplo).

```xml
<Target Name="Embedding**AssemblyName**From**PackageId**" AfterTargets="ResolveReferences" BeforeTargets="FindReferenceAssembliesForReferences">
  <ItemGroup>
    <ReferencePath Condition=" '%(FileName)' == '{InteropAssemblyName}' AND '%(ReferencePath.NuGetPackageId)' == '$(MSBuildThisFileName)' ">
      <EmbedInteropTypes>true</EmbedInteropTypes>
    </ReferencePath>
  </ItemGroup>
</Target>
```

Tenga en cuenta que, cuando se usa el formato de administración `packages.config`, agregar referencias a los ensamblados desde los paquetes hace que NuGet y Visual Studio comprueben los ensamblados de interoperabilidad COM y establezcan `EmbedInteropTypes` en true en el archivo de proyecto. En este caso, los destinos se reemplazan.

Además, de forma predeterminada los [activos de compilación no fluyen de manera transitiva](../consume-packages/package-references-in-project-files.md#controlling-dependency-assets). Los paquetes creados como se describe aquí funcionan de manera diferente cuando se extraen como una dependencia transitiva de un proyecto a una referencia de proyecto. El consumidor del paquete puede permitir que fluyan si modifica el valor predeterminado de PrivateAssets para que no se incluya la compilación.

<a name="creating-the-package"></a>