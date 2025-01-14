---
title: Notas de la versión de NuGet 4.7 RTM
description: Notas de la versión de NuGet 4.7.0, incluidos problemas conocidos, correcciones de errores, características agregadas y DCR.
author: karann-msft
ms.author: karann
ms.date: 5/14/2018
ms.topic: conceptual
ms.openlocfilehash: fe769f95e3eda4bc07db4369544472c00b35363d
ms.sourcegitcommit: 7441f12f06ca380feb87c6192ec69f6108f43ee3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69488652"
---
# <a name="nuget-47-release-notes"></a>Notas de la versión de NuGet 4.7

[Visual Studio 2017 15.7 RTW](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes) incluye [NuGet 4.7.0](https://dist.nuget.org/win-x86-commandline/v4.7.0/nuget.exe).

## <a name="summary-whats-new-in-470"></a>Resumen: Novedades de la versión 4.7.0

* Se ha ampliado la firma de paquetes para habilitar los [paquetes firmados del repositorio](https://github.com/NuGet/Home/wiki/Repository-Signatures).

* Con Visual Studio 15.7, se ha presentado la funcionalidad de [migrar los proyectos existentes que usan el formato packages.config para usar PackageReference](https://docs.microsoft.com/en-us/nuget/consume-packages/migrate-packages-config-to-package-reference) en su lugar.

## <a name="summary-whats-new-in-472"></a>Resumen: Novedades de la versión 4.7.2

* Corrección de seguridad: Premisos demasiado amplios de los archivos creados en ~/.nuget: [n.º 7673](https://github.com/NuGet/Home/issues/7673) [CVE-2019-0757](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2019-0757)

## <a name="summary-whats-new-in-473"></a>Resumen: Novedades de la versión 4.7.3

* Corrección de seguridad: Posible ruta relativa de los archivos de NUPKG por encima del directorio NUPKG: [n.º 7906](https://github.com/NuGet/Home/issues/7906)

## <a name="known-issues"></a>Problemas conocidos

### <a name="the-migrate-packagesconfig-to-packagereference-option-is-not-available-in-the-right-click-context-menu"></a>La opción `Migrate packages.config to PackageReference...` no está disponible en el menú contextual.

#### <a name="issue"></a>Problema

Cuando se abre un proyecto por primera vez, NuGet puede no inicializarse hasta que se realiza una operación de NuGet. Esto da lugar a que la opción de migración no aparezca en el menú contextual en `packages.config` o `References`.

#### <a name="workaround"></a>Solución

Realice cualquiera de las siguientes acciones de NuGet:
* Abra la UI del administrador de paquetes; haga clic con el botón derecho en `References` y seleccione `Manage NuGet Packages...`.
* Abra la consola del administrador de paquetes; en `Tools > NuGet Package Manager`, seleccione `Package Manager Console`.
* Ejecute la restauración de NuGet; haga clic con el botón derecho en el nodo de la solución en el Explorador de soluciones y seleccione `Restore NuGet Packages`.
* Compile el proyecto, una acción que también desencadena la restauración de NuGet.

Ahora debería ver la opción de migración. Tenga en cuenta que esta opción no se admite y no se mostrará para los tipos de proyecto ASP.NET y C++.

### <a name="issues-with-net-standard-20-with-net-framework--nuget"></a>Problemas con .NET 2.0 Standard con .NET Framework y NuGet

.NET Standard y sus herramientas se han diseñado de forma que los proyectos destinados a .NET Framework 4.6.1 puedan usar los paquetes y proyectos de NuGet que tienen como destino .NET Standard 2.0 o versiones anteriores. [En este documento](https://github.com/dotnet/standard/issues/481) se resumen los problemas relacionados con ese escenario, el plan para abordarlos, así como soluciones alternativas que se pueden implementar con el estado actual de las herramientas.

## <a name="top-issues-fixed-in-this-release"></a>Principales problemas corregidos en esta versión

### <a name="bugs"></a>Errores

* NuGet ejecuta un interbloqueo en el sistema de proyectos de .NET Core (regresión nueva). - [n.º 6733](https://github.com/NuGet/Home/issues/6733)
* Paquete: construcción incorrecta de la ruta de acceso al paquete al usar TfmSpecificPackageFile con rutas de acceso de comodines: [n.º 6726](https://github.com/NuGet/Home/issues/6726)
* Paquete: El proyecto de Web API no puede crear el paquete a menos que se defina ispackable de manera explícita. - [N.º 6156](https://github.com/NuGet/Home/issues/6156)
* El nuevo paquete tarda 30 minutos en aparecer en la interfaz de usuario de VS y en PMC (nuget.exe lo ve de inmediato); [n.º 6657](https://github.com/NuGet/Home/issues/6657)
* Firma:  SignatureUtility.GetCertificateChain(...) no comprueba todos los estados de cadena: [n.º 6565](https://github.com/NuGet/Home/issues/6565)
* Firma: mejorar el control de GeneralizedTime en DER; [n.º 6564](https://github.com/NuGet/Home/issues/6564)
* Firma: VS no muestra un error NU3002 al instalar un paquete alterado: [n.º 6337](https://github.com/NuGet/Home/issues/6337)
* lockFile.GetLibrary distingue mayúsculas de minúsculas; [n.º 6500](https://github.com/NuGet/Home/issues/6500)
* El código de restauración para instalar y actualizar y las rutas de acceso al código de restauración no son coherentes; [n.º 3471](https://github.com/NuGet/Home/issues/3471)
* El cuadro combinado de la versión del Administrador de paquetes de la solución puede seleccionar el separador con el teclado; [n.º 2606](https://github.com/NuGet/Home/issues/2606)
* Imposibilidad de cargar el índice del servicio del origen `https://www.myget.org/F/<id>` ---> System.Net.Http.HttpRequestException: el código de estado de respuesta no indica la correcta realización de la operación: 403 (Prohibido): [n.º 2530](https://github.com/NuGet/Home/issues/2530)

### <a name="dcrs"></a>DCR

* Emitir encabezado X-NuGet-Session-Id para correlacionar las solicitudes [propuesta de característica] - [n.º 5330](https://github.com/NuGet/Home/issues/5330)
* Exponer una manera para esperar a que se ejecute la operación de restauración en Visual Studio mediante las API de IV. - [n.º 6029](https://github.com/NuGet/Home/issues/6029)
* NuGet.exe: NoServiceEndpoint evitará que se anexe el sufijo de la dirección URL del servicio; [n.º 6586](https://github.com/NuGet/Home/issues/6586)
* Agregar hash de confirmación a la versión informativa; [n.º 6492](https://github.com/NuGet/Home/issues/6492)
* Firma: habilitar eliminación de firma/contrafirma del repositorio; [n.º 6646](https://github.com/NuGet/Home/issues/6646)
* Firma:  API para eliminar la firma/contrafirma del repositorio: [n.º 6589](https://github.com/NuGet/Home/issues/6589)
* Registrar información de origen en VS; [n.º 6527](https://github.com/NuGet/Home/issues/6527)
* Filtrar /tools solo en TFM y RID, para que el archivo XML de configuración se pueda ubicar en la carpeta /tools; [n.º 6197](https://github.com/NuGet/Home/issues/6197)
* Advertir cuando el comando Pack excluye un archivo que empieza por .  - [n.º 3308](https://github.com/NuGet/Home/issues/3308)

[Lista de todos los problemas corregidos en esta versión](https://github.com/NuGet/Home/issues?q=is%3Aissue+is%3Aclosed+milestone%3A%224.7")
