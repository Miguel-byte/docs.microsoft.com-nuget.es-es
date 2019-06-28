---
title: Comando de CLI de NuGet firmantes de confianza
description: Referencia del comando de firmantes de confianza de nuget.exe
author: patbel
ms.author: patbel
ms.date: 11/12/2018
ms.topic: reference
ms.reviewer: rmpablos
ms.openlocfilehash: c22c7f0a6b6878bec4f8396e02e2d97998170455
ms.sourcegitcommit: b6810860b77b2d50aab031040b047c20a333aca3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425980"
---
# <a name="trusted-signers-command-nuget-cli"></a><span data-ttu-id="8d919-103">comando de firmantes de confianza (CLI de NuGet)</span><span class="sxs-lookup"><span data-stu-id="8d919-103">trusted-signers command (NuGet CLI)</span></span>

<span data-ttu-id="8d919-104">**Se aplica a:** consumo de paquetes &bullet; **versiones compatibles:** 4.9.1+</span><span class="sxs-lookup"><span data-stu-id="8d919-104">**Applies to:** package consumption &bullet; **Supported versions:** 4.9.1+</span></span>

<span data-ttu-id="8d919-105">Obtiene o establece los firmantes de confianza a la configuración de NuGet.</span><span class="sxs-lookup"><span data-stu-id="8d919-105">Gets or sets trusted signers to the NuGet configuration.</span></span> <span data-ttu-id="8d919-106">Para el uso adicional, consulte [configuraciones comunes NuGet](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="8d919-106">For additional usage, see [Common NuGet configurations](../consume-packages/configuring-nuget-behavior.md).</span></span> <span data-ttu-id="8d919-107">Para obtener más información sobre cómo el esquema de nuget.config parece, consulte el [referencia del archivo de configuración de NuGet](../reference/nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="8d919-107">For details on how the nuget.config schema looks like, refer to the [NuGet config file reference](../reference/nuget-config-file.md).</span></span>

## <a name="usage"></a><span data-ttu-id="8d919-108">Uso</span><span class="sxs-lookup"><span data-stu-id="8d919-108">Usage</span></span>

```cli
nuget trusted-signers <list|add|remove|sync> [options]
```

<span data-ttu-id="8d919-109">Si ninguno de `list|add|remove|sync` se especifica, el comando predeterminado será `list`.</span><span class="sxs-lookup"><span data-stu-id="8d919-109">if none of `list|add|remove|sync` is specified, the command will default to `list`.</span></span>

## <a name="nuget-trusted-signers-list"></a><span data-ttu-id="8d919-110">lista de confianza de firmantes de NuGet</span><span class="sxs-lookup"><span data-stu-id="8d919-110">nuget trusted-signers list</span></span>

<span data-ttu-id="8d919-111">Enumera todos los firmantes de confianza en la configuración.</span><span class="sxs-lookup"><span data-stu-id="8d919-111">Lists all the trusted signers in the configuration.</span></span> <span data-ttu-id="8d919-112">Esta opción incluirá todos los certificados (con la huella digital y el algoritmo de huella digital) tiene cada firmante.</span><span class="sxs-lookup"><span data-stu-id="8d919-112">This option will include all the certificates (with fingerprint and fingerprint algorithm) each signer has.</span></span> <span data-ttu-id="8d919-113">Si un certificado tiene un carácter `[U]`, significa que la entrada de certificado tiene `allowUntrustedRoot` establecer como `true`.</span><span class="sxs-lookup"><span data-stu-id="8d919-113">If a certificate has a preceding `[U]`, it means that certificate entry has `allowUntrustedRoot` set as `true`.</span></span>

<span data-ttu-id="8d919-114">A continuación es un ejemplo de salida de este comando:</span><span class="sxs-lookup"><span data-stu-id="8d919-114">Below is an example output from this command:</span></span>

```cli
$ nuget trusted-signers
Registered trusted signers:


 1.   nuget.org [repository]
      Service Index: https://api.nuget.org/v3/index.json
      Certificate fingerprint(s):
        SHA256 - 0E5F38F57DC1BCC806D8494F4F90FBCEDD988B46760709CBEEC6F4219AA6157D

 2.   microsoft [author]
      Certificate fingerprint(s):
        SHA256 - 3F9001EA83C560D712C24CF213C3D312CB3BFF51EE89435D3430BD06B5D0EECE

 3.   myUntrustedAuthorSignature [author]
      Certificate fingerprint(s):
        [U] SHA256 - 518F9CF082C0872025EFB2587B6A6AB198208F63EA58DD54D2B9FF6735CA4434
        
```

## <a name="nuget-trusted-signers-add-options"></a><span data-ttu-id="8d919-115">nuget trusted-signers add [options]</span><span class="sxs-lookup"><span data-stu-id="8d919-115">nuget trusted-signers add [options]</span></span>

<span data-ttu-id="8d919-116">Agrega un firmante de confianza con el nombre dado a la configuración. Esta opción tiene diferentes movimientos para agregar un repositorio o autor de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-116">Adds a trusted signer with the given name to the config. This option has different gestures to add a trusted author or repository.</span></span>

## <a name="options-for-add-based-on-a-package"></a><span data-ttu-id="8d919-117">Opciones para agregar basándose en un paquete</span><span class="sxs-lookup"><span data-stu-id="8d919-117">Options for add based on a package</span></span>

```cli
nuget trusted-signers add <package(s)> -Name <name> [options]
```

<span data-ttu-id="8d919-118">donde `<package(s)>` consta de uno o más `.nupkg` archivos.</span><span class="sxs-lookup"><span data-stu-id="8d919-118">where `<package(s)>` is one or more `.nupkg` files.</span></span>

| <span data-ttu-id="8d919-119">Opción</span><span class="sxs-lookup"><span data-stu-id="8d919-119">Option</span></span> | <span data-ttu-id="8d919-120">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d919-120">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d919-121">Autor</span><span class="sxs-lookup"><span data-stu-id="8d919-121">Author</span></span> | <span data-ttu-id="8d919-122">Especifica que se debe confiar en la firma del autor de los paquetes.</span><span class="sxs-lookup"><span data-stu-id="8d919-122">Specifies that the author signature of the package(s) should be trusted.</span></span> |
| <span data-ttu-id="8d919-123">Repositorio</span><span class="sxs-lookup"><span data-stu-id="8d919-123">Repository</span></span> | <span data-ttu-id="8d919-124">Especifica que la firma de repositorio o la contrafirma de los paquetes debe ser de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-124">Specifies that the repository signature or countersignature of the package(s) should be trusted.</span></span> |
| <span data-ttu-id="8d919-125">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="8d919-125">AllowUntrustedRoot</span></span> | <span data-ttu-id="8d919-126">Especifica si se debe permitir el certificado del firmante de confianza encadenar a una raíz de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-126">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |
| <span data-ttu-id="8d919-127">Owners</span><span class="sxs-lookup"><span data-stu-id="8d919-127">Owners</span></span> | <span data-ttu-id="8d919-128">Lista separada por punto y coma de los propietarios de confianza para restringir aún más la confianza de un repositorio.</span><span class="sxs-lookup"><span data-stu-id="8d919-128">Semi-colon separated list of trusted owners to further restrict the trust of a repository.</span></span> <span data-ttu-id="8d919-129">Solo es válido cuando se usa el `-Repository` opción.</span><span class="sxs-lookup"><span data-stu-id="8d919-129">Only valid when using the `-Repository` option.</span></span> |

<span data-ttu-id="8d919-130">Proporcionar ambos `-Author` y `-Repository` al mismo tiempo, no se admite.</span><span class="sxs-lookup"><span data-stu-id="8d919-130">Providing both `-Author` and `-Repository` at the same time is not supported.</span></span>

## <a name="options-for-add-based-on-a-service-index"></a><span data-ttu-id="8d919-131">Opciones para agregar basándose en un índice de servicio</span><span class="sxs-lookup"><span data-stu-id="8d919-131">Options for add based on a service index</span></span>

```cli
nuget trusted-signers add -Name <name> [options]
```

<span data-ttu-id="8d919-132">_Nota_: Esta opción sólo permiten agregar repositorios de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-132">_Note_: This option will only add trusted repositories.</span></span> 

| <span data-ttu-id="8d919-133">Opción</span><span class="sxs-lookup"><span data-stu-id="8d919-133">Option</span></span> | <span data-ttu-id="8d919-134">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d919-134">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d919-135">ServiceIndex</span><span class="sxs-lookup"><span data-stu-id="8d919-135">ServiceIndex</span></span> | <span data-ttu-id="8d919-136">Especifica el índice de servicio V3 del repositorio que sean de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-136">Specifies the V3 service index of the repository to be trusted.</span></span> <span data-ttu-id="8d919-137">Este repositorio debe ser compatible con el recurso de firmas de repositorio.</span><span class="sxs-lookup"><span data-stu-id="8d919-137">This repository has to support the repository signatures resource.</span></span> <span data-ttu-id="8d919-138">Si no se proporciona, el comando buscará un origen del paquete con el mismo `-Name` y obtener el índice de servicio a partir de ahí.</span><span class="sxs-lookup"><span data-stu-id="8d919-138">If not provided, the command will look for a package source with the same `-Name` and get the service index from there.</span></span> |
| <span data-ttu-id="8d919-139">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="8d919-139">AllowUntrustedRoot</span></span> | <span data-ttu-id="8d919-140">Especifica si se debe permitir el certificado del firmante de confianza encadenar a una raíz de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-140">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |
| <span data-ttu-id="8d919-141">Owners</span><span class="sxs-lookup"><span data-stu-id="8d919-141">Owners</span></span> | <span data-ttu-id="8d919-142">Lista separada por punto y coma de los propietarios de confianza para restringir aún más la confianza de un repositorio.</span><span class="sxs-lookup"><span data-stu-id="8d919-142">Semi-colon separated list of trusted owners to further restrict the trust of a repository.</span></span> |

## <a name="options-for-add-based-on-the-certificate-information"></a><span data-ttu-id="8d919-143">Opciones para agregar según la información del certificado</span><span class="sxs-lookup"><span data-stu-id="8d919-143">Options for add based on the certificate information</span></span>

```cli
nuget trusted-signers add -Name <name> [options]
```

<span data-ttu-id="8d919-144">_Nota_: Si ya existe un firmante de confianza con el nombre especificado, se agregará el elemento de certificado para ese firmante.</span><span class="sxs-lookup"><span data-stu-id="8d919-144">_Note_: If a trusted signer with the given name already exists, the certificate item will be added to that signer.</span></span> <span data-ttu-id="8d919-145">En caso contrario, se creará un autor de confianza con un elemento de certificado desde determinadas información del certificado.</span><span class="sxs-lookup"><span data-stu-id="8d919-145">Otherwise a trusted author will be created with a certificate item from given certificate information.</span></span>

| <span data-ttu-id="8d919-146">Opción</span><span class="sxs-lookup"><span data-stu-id="8d919-146">Option</span></span> | <span data-ttu-id="8d919-147">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d919-147">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d919-148">CertificateFingerprint</span><span class="sxs-lookup"><span data-stu-id="8d919-148">CertificateFingerprint</span></span> | <span data-ttu-id="8d919-149">Especifica un certificado de huellas digitales de un certificado que los paquetes firmados deben firmarse con.</span><span class="sxs-lookup"><span data-stu-id="8d919-149">Specifies a certificate fingerprints of a certificate which signed packages must be signed with.</span></span> <span data-ttu-id="8d919-150">Una huella digital del certificado es un hash del certificado.</span><span class="sxs-lookup"><span data-stu-id="8d919-150">A certificate fingerprint is a hash of the certificate.</span></span> <span data-ttu-id="8d919-151">Especifica el algoritmo hash utilizado para calcular este hash debe ser en el `FingerprintAlgorithm` opción.</span><span class="sxs-lookup"><span data-stu-id="8d919-151">The hash algorithm used for calculating this hash should be specifies in the `FingerprintAlgorithm` option.</span></span> |
| <span data-ttu-id="8d919-152">FingerprintAlgorithm</span><span class="sxs-lookup"><span data-stu-id="8d919-152">FingerprintAlgorithm</span></span> | <span data-ttu-id="8d919-153">Especifica el algoritmo hash utilizado para calcular la huella digital del certificado.</span><span class="sxs-lookup"><span data-stu-id="8d919-153">Specifies the hash algorithm used to calculate the certificate fingerprint.</span></span> <span data-ttu-id="8d919-154">Tiene como valor predeterminado `SHA256`.</span><span class="sxs-lookup"><span data-stu-id="8d919-154">Defaults to `SHA256`.</span></span> <span data-ttu-id="8d919-155">Valores admitidos son `SHA256`, `SHA384` y `SHA512`</span><span class="sxs-lookup"><span data-stu-id="8d919-155">Values supported are `SHA256`, `SHA384` and `SHA512`</span></span> |
| <span data-ttu-id="8d919-156">AllowUntrustedRoot</span><span class="sxs-lookup"><span data-stu-id="8d919-156">AllowUntrustedRoot</span></span> | <span data-ttu-id="8d919-157">Especifica si se debe permitir el certificado del firmante de confianza encadenar a una raíz de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-157">Specifies if the certificate for the trusted signer should be allowed to chain to an untrusted root.</span></span> |

## <a name="nuget-trusted-signers-remove--name-name"></a><span data-ttu-id="8d919-158">NuGet confianza-firmantes remove - nombre <name></span><span class="sxs-lookup"><span data-stu-id="8d919-158">nuget trusted-signers remove -Name <name></span></span>

<span data-ttu-id="8d919-159">Quita los firmantes de confianza que coinciden con el nombre especificado.</span><span class="sxs-lookup"><span data-stu-id="8d919-159">Removes any trusted signers that match the given name.</span></span>

## <a name="nuget-trusted-signers-sync--name-name"></a><span data-ttu-id="8d919-160">sincronización NuGet-firmantes de confianza - nombre <name></span><span class="sxs-lookup"><span data-stu-id="8d919-160">nuget trusted-signers sync -Name <name></span></span>

<span data-ttu-id="8d919-161">Solicita la lista más reciente de los certificados usados en un repositorio de confianza actualmente para actualizar el la lista de certificados existentes en el firmante de confianza.</span><span class="sxs-lookup"><span data-stu-id="8d919-161">Requests the latest list of certificates used in a currently trusted repository to update the the existing certificate list in the trusted signer.</span></span>

<span data-ttu-id="8d919-162">_Nota_: Este gesto eliminará la lista actual de los certificados y reemplazarlos por una lista actualizada desde el repositorio.</span><span class="sxs-lookup"><span data-stu-id="8d919-162">_Note_: This gesture will delete the current list of certificates and replace them with an up-to-date list from the repository.</span></span>

## <a name="options"></a><span data-ttu-id="8d919-163">Opciones</span><span class="sxs-lookup"><span data-stu-id="8d919-163">Options</span></span>

| <span data-ttu-id="8d919-164">Opción</span><span class="sxs-lookup"><span data-stu-id="8d919-164">Option</span></span> | <span data-ttu-id="8d919-165">Descripción</span><span class="sxs-lookup"><span data-stu-id="8d919-165">Description</span></span> |
| --- | --- |
| <span data-ttu-id="8d919-166">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="8d919-166">ConfigFile</span></span> | <span data-ttu-id="8d919-167">El archivo de configuración para aplicar.</span><span class="sxs-lookup"><span data-stu-id="8d919-167">The NuGet configuration file to apply.</span></span> <span data-ttu-id="8d919-168">Si no se especifica, `%AppData%\NuGet\NuGet.Config` (Windows) o `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) se utiliza.</span><span class="sxs-lookup"><span data-stu-id="8d919-168">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="8d919-169">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="8d919-169">ForceEnglishOutput</span></span> | <span data-ttu-id="8d919-170">Obliga a nuget.exe para ejecutarse con una referencia cultural invariable, en inglés.</span><span class="sxs-lookup"><span data-stu-id="8d919-170">Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="8d919-171">Help</span><span class="sxs-lookup"><span data-stu-id="8d919-171">Help</span></span> | <span data-ttu-id="8d919-172">Muestra información de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="8d919-172">Displays help information for the command.</span></span> |
| <span data-ttu-id="8d919-173">Verbosity</span><span class="sxs-lookup"><span data-stu-id="8d919-173">Verbosity</span></span> | <span data-ttu-id="8d919-174">Especifica la cantidad de detalle que se muestra en la salida: *normal*, *quiet*, *detallada*.</span><span class="sxs-lookup"><span data-stu-id="8d919-174">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

## <a name="examples"></a><span data-ttu-id="8d919-175">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="8d919-175">Examples</span></span>

```cli
nuget trusted-signers list

nuget trusted-signers Add -Name existingSource

nuget trusted-signers Add -Name trustedRepo -ServiceIndex https://trustedRepo.test/v3ServiceIndex

nuget trusted-signers Add -Name author1 -CertificateFingerprint CE40881FF5F0AD3E58965DA20A9F571EF1651A56933748E1BF1C99E537C4E039 -FingerprintAlgorithm SHA256

nuget trusted-signers Add -Repository .\..\MyRepositorySignedPackage.nupkg -Name TrustedRepo

nuget-trusted-signers Remove -Name TrustedRepo

nuget-trusted-signers Sync -Name TrustedRepo
```
