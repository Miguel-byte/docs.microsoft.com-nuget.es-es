---
title: Notas de la versión 5.0 preview de NuGet
description: Notas de la versión para las versiones preliminares de NuGet 5.0 incluidos problemas conocidos, correcciones de errores, nuevas características y dcr.
author: anangaur
ms.author: anangaur
ms.date: 1/25/2019
ms.topic: conceptual
ms.openlocfilehash: 57b66b347ac47a3d05907a4bb237002de8981ecc
ms.sourcegitcommit: 85bf94e0efcfcee1f914650bdc142309ef3e06d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/01/2019
ms.locfileid: "57196205"
---
# <a name="nuget-50-preview-release-notes"></a>Notas de la versión preliminar 5.0 NuGet

## <a name="nuget-50-preview-releases"></a>Versiones 5.0 Preview de NuGet

* 27 de febrero de 2010 - [NuGet 5.0 Preview 4](#summary-whats-new-in-50-preview-4)
* 13 de febrero de 2019 - [NuGet 5.0 Preview 3](#summary-whats-new-in-50-preview-3)
* 23 de enero de 2019 - [NuGet 5.0 Preview 2](#summary-whats-new-in-50-preview-2)

## <a name="summary-whats-new-in-nuget-50-preview-4"></a>Resumen: Novedades en NuGet 5.0 Preview 4

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión

**Errores:**

* NuGet.VisualStudio.IVsPackageInstaller - que realiza la llamada en un proyecto con ningún paquete hace referencia siempre usa packages.config, incluso si el valor predeterminado se establece en PackageReference - [7005 #](https://github.com/NuGet/Home/issues/7005)

* PMC: Paquete de actualización reinstalar se produce un error ("no se encuentra el paquete") en paquetes elimine de la lista. - [#7268](https://github.com/NuGet/Home/issues/7268)

* Agregar el aviso de terceros en nuestro repositorio y VSIX - [#7409](https://github.com/NuGet/Home/issues/7409)

* NuGet.VisualStudio.IVsPackageInstaller.InstallPackage debe instalar la versión más reciente cuando no hay ninguna versión dada - [#7493](https://github.com/NuGet/Home/issues/7493)

* --asistencia interactiva para dotnet nuget push - [#7519](https://github.com/NuGet/Home/issues/7519)

* Al restaurar el archivo de bloqueo, no debería generarse NU1603 advertencia. - [#7529](https://github.com/NuGet/Home/issues/7529)

* NuGet no debe imprimir la ruta de acceso del proyecto durante la restauración con registro mínimo - [#7647](https://github.com/NuGet/Home/issues/7647)

* --asistencia interactiva para dotnet quitar paquete - [#7727](https://github.com/NuGet/Home/issues/7727)

* Agregar copia NuGet.Packaging.Core con TypeForwardedTo attrs - [7768 #](https://github.com/NuGet/Home/issues/7768)

* plugins_cache necesita una ruta de acceso más corta para funcionar bien - [#7770](https://github.com/NuGet/Home/issues/7770)

* Prefiere la ruta de acceso para la detección de msbuild si el usuario no solicitar versión de msbuild específicas - [#7786](https://github.com/NuGet/Home/issues/7786)

**DCR:**

* limitar número de solicitud de http por código fuente a través de NuGet.Config - [4538 #](https://github.com/NuGet/Home/issues/4538)

* NuGet debe tener como destino Net472 (para ayudar a la compilación de la extensión VSIX 16.0 limpieza) - [7143 #](https://github.com/NuGet/Home/issues/7143)

* PMC: Quitar comando OpenPackagePage - [7384 #](https://github.com/NuGet/Home/issues/7384)

* Asegúrese de NetCoreApp 3.0 se asignan a NetStandard 2.1 - [#7762](https://github.com/NuGet/Home/issues/7762)

* Agregar compatibilidad de netstandard2.0 para paquetes NuGet.* - [6516 #](https://github.com/NuGet/Home/issues/6516)


## <a name="summary-whats-new-in-nuget-50-preview-3"></a>Resumen: Novedades en NuGet 5.0 Preview 3

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión 

**Errores:**

* nuget.exe /? debe enumerar las versiones correctas de msbuild - [#7794](https://github.com/NuGet/Home/issues/7794)

* NuGet.targets(498,5): error: No se encontró una parte de la ruta de acceso ' / tmp/NuGetScratch - en mono - [#7793](https://github.com/NuGet/Home/issues/7793)

* restauración innecesariamente enumera el contenido de todas las versiones de paquete que se hace referencia en la caché del equipo - [#7639](https://github.com/NuGet/Home/issues/7639)

* Detección automática de MSBuild siempre selecciona 16.0 después de obtener una vista previa en la instalación de VS 2019 - [#7621](https://github.com/NuGet/Home/issues/7621)

* paquete de dotnet lista en una solución genera entradas duplicadas para framework - [#7607](https://github.com/NuGet/Home/issues/7607)

* Excepción "el nombre de ruta de acceso vacía no es legal" cuando IVsPackageInstaller.InstallPackage que realiza la llamada en el antiguo proyectos y paquetes de la carpeta no existe. - [#5936](https://github.com/NuGet/Home/issues/5936)

* nivel de detalle de MSBuild/t: Restore mínimo debe ser más mínimo - [4695 #](https://github.com/NuGet/Home/issues/4695)

**DCR:**

* Permitir que los autores de paquetes definir el comportamiento de compilación activos transitiva - [#6091](https://github.com/NuGet/Home/issues/6091)

* Habilitar la restauración en VS se realice correctamente si un proyecto no forma parte de la solución o no está cargado, pero anteriormente se ha restaurado - [#5820](https://github.com/NuGet/Home/issues/5820)


## <a name="summary-whats-new-in-50-preview-2"></a>Resumen: Novedades de 5.0 Preview 2

### <a name="issues-fixed-in-this-release"></a>Problemas corregidos en esta versión

**Errores:**

* VS de 16.0 NuGet UI tiene pestañas ilegibles debido a problemas de color - [#7735](https://github.com/NuGet/Home/issues/7735)

* NuGet.Core & NuGet.Clients License.txt aclaración - [#7629](https://github.com/NuGet/Home/issues/7629)

* Restauración innecesariamente enumera la carpeta de paquetes global en intentar determinar el tipo - [#7596](https://github.com/NuGet/Home/issues/7596)

* Errores de cumplimiento del archivo de bloqueo deberían aparecer en la ventana Lista de errores - [#7429](https://github.com/NuGet/Home/issues/7429)

* Solucionar problemas de NuGet.Configuration - [7326 #](https://github.com/NuGet/Home/issues/7326)

* Adaptarse a la actualización de MSBuild de la ubicación de instalación.  - [#7325](https://github.com/NuGet/Home/issues/7325)

* NuGet.Build.Tasks.Pack debe ser una dependencia de desarrollo - [#7249](https://github.com/NuGet/Home/issues/7249)

* Agregar paquete de punto de extensión para incluir depurar símbolos - [7234 #](https://github.com/NuGet/Home/issues/7234)

* dotnet pack debe conservar el intervalo de versiones de dependencia en el nupkg creado. (incluso si se usa la versión flotante) - [7232 #](https://github.com/NuGet/Home/issues/7232)

* restauración de dotnet se produce un error en un origen autenticado cuando la configuración de nivel de usuario también tiene el origen: [#7209](https://github.com/NuGet/Home/issues/7209)

* Módulo no debe restringir el conjunto de BuildActions para archivos de contenido - [7155 #](https://github.com/NuGet/Home/issues/7155)

* Mediante un projectreference que requiere AssetTargetFallback se realice correctamente, debería advertir. - [#7137](https://github.com/NuGet/Home/issues/7137)

* Interbloqueo debido a problemas de subprocesamiento al llamar a CPS (CommonProjectSystem) - [7103 #](https://github.com/NuGet/Home/issues/7103)

* dotnet Agregar paquete no utilice credenciales desde la configuración global para un origen especificado en la configuración local: [#6935](https://github.com/NuGet/Home/issues/6935)

* Problemas de subprocesamiento con MEF que se va a llamar en async codepaths - [6771 #](https://github.com/NuGet/Home/issues/6771)

* De firma: error notificado dos veces y sin la pila de llamadas - [#6455](https://github.com/NuGet/Home/issues/6455)

* Instalar un paquete firmado con certificado de firma de confianza debería mostrar el error - [#6318](https://github.com/NuGet/Home/issues/6318)

* Restauración de NuGet incorrectamente NOOP cuando 2 proyectos están compartiendo el directorio obj - [#6114](https://github.com/NuGet/Home/issues/6114)

* No se puede usar PAT con dotnet se restaura en Linux con paquetes de fuente autenticado - [#5651](https://github.com/NuGet/Home/issues/5651)

* se produce un error en la restauración de dotnet debido a la amplia deshabilitado máquina fuente - [#5410](https://github.com/NuGet/Home/issues/5410)

**DCR:**

* Los ensamblados de NuGet 5.0 requieren .NET 4.7.2 (a través de cambio TFM) - [#7510](https://github.com/NuGet/Home/issues/7510)

* NuGetLicenseData desde NuGet.Packaging debe ser un tipo público. Actualizar los metadatos de licencia ingerido desde spdx. - [#7471](https://github.com/NuGet/Home/issues/7471)

* Quitar de la API de configuración obsoletas - [#7294](https://github.com/NuGet/Home/issues/7294)

* Tiempos de espera de restauración de solución alternativa en sistemas con 1 cpu - [6742 #](https://github.com/NuGet/Home/issues/6742)

* NuGet prefiere la autenticación NTLM, incluso si no hay credenciales en NuGet.config: agregar la opción de configuración para filtrar los tipos de autenticación de credenciales: [#5286](https://github.com/NuGet/Home/issues/5286)

* Habilitar EmbedInteropTypes packagereference (capacidad de búsqueda de coincidencias Packages.Config) - [2365 #](https://github.com/NuGet/Home/issues/2365)

[Lista de todos los problemas corregidos en esta versión 5.0.0-preview2](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.9.2")

### <a name="known-issues"></a>Problemas conocidos

#### <a name="packages-in-fallbackfolders-installed-by-net-core-sdk-are-custom-installed-and-fail-signature-validation---7414httpsgithubcomnugethomeissues7414"></a>Los paquetes en FallbackFolders instalados por el SDK de .NET Core de forma personalizada no superan la validación de firma. - [#7414](https://github.com/NuGet/Home/issues/7414)
**Problema** al usar dotnet.exe 2.x para restaurar esa netcoreapp varios destino de un proyecto 1.x y netcoreapp 2.x, la carpeta de reserva se trata como un archivo de fuente. Esto significa que, cuando se restaura, NuGet elegirá el paquete de la carpeta de reserva e intentará instalarlo en la carpeta de paquetes global y realizará la validación de firma habitual, lo cual produce un error.
**Solución alternativa** deshabilitar el uso de la carpeta reserva estableciendo el `RestoreAdditionalProjectSources` en nothing. `<RestoreAdditionalProjectSources/>` Use esta opción con precaución, ya que provocará que muchos paquetes, que de otro modo se habrían restaurado de la carpeta de reserva, se descarguen de NuGet.org.
