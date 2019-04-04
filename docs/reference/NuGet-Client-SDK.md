---
title: SDK de cliente de NuGet
description: La API está en constante evolución y no ha documentado, pero los ejemplos están disponibles en el blog de Dave Glick.
author: karann-msft
ms.author: karann
ms.date: 01/09/2018
ms.topic: conceptual
ms.openlocfilehash: 8f96bf289e8121fd25262fb95c2f36dfc89045c5
ms.sourcegitcommit: 9f94e00428d83aef4a7a87db679129eff7720c59
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2019
ms.locfileid: "58911041"
---
# <a name="nuget-client-sdk"></a><span data-ttu-id="17fab-103">SDK de cliente de NuGet</span><span class="sxs-lookup"><span data-stu-id="17fab-103">NuGet Client SDK</span></span>

> [!Note]
> <span data-ttu-id="17fab-104">Para que no debe confundirse con el [NuGet *Web* API](https://docs.microsoft.com/en-us/nuget/api/overview)</span><span class="sxs-lookup"><span data-stu-id="17fab-104">Not to be confused with the [NuGet *Web* API](https://docs.microsoft.com/en-us/nuget/api/overview)</span></span>

<span data-ttu-id="17fab-105">El *SDK del cliente NuGet* hace referencia a un grupo de bibliotecas de .NET que se centra en torno a [NuGet.Commands](https://www.nuget.org/packages/NuGet.Commands), [Nuget.Packaging](https://www.nuget.org/packages/NuGet.Packaging), y [NuGet.Protocol](https://www.nuget.org/packages/NuGet.Protocol).</span><span class="sxs-lookup"><span data-stu-id="17fab-105">The *NuGet Client SDK* refers to a group of .NET libraries centered around [NuGet.Commands](https://www.nuget.org/packages/NuGet.Commands), [Nuget.Packaging](https://www.nuget.org/packages/NuGet.Packaging), and [NuGet.Protocol](https://www.nuget.org/packages/NuGet.Protocol).</span></span> <span data-ttu-id="17fab-106">Estos paquetes reemplazan la anterior [NuGet.Core](https://www.nuget.org/packages/NuGet.Core/) biblioteca.</span><span class="sxs-lookup"><span data-stu-id="17fab-106">These packages replace the earlier [NuGet.Core](https://www.nuget.org/packages/NuGet.Core/) library.</span></span>

<span data-ttu-id="17fab-107">Estamos trabajando en tener un área de superficie estable que podemos documentamos pronto.</span><span class="sxs-lookup"><span data-stu-id="17fab-107">We are working on having a stable surface area that we can document soon.</span></span>

## <a name="source-code"></a><span data-ttu-id="17fab-108">Código fuente</span><span class="sxs-lookup"><span data-stu-id="17fab-108">Source code</span></span>

<span data-ttu-id="17fab-109">El código fuente se publica en GitHub en el proyecto [NuGet/NuGet.Client](https://github.com/NuGet/NuGet.Client).</span><span class="sxs-lookup"><span data-stu-id="17fab-109">The source code is published on GitHub in the project [NuGet/NuGet.Client](https://github.com/NuGet/NuGet.Client).</span></span>

## <a name="third-party-documentation"></a><span data-ttu-id="17fab-110">Documentación de terceros</span><span class="sxs-lookup"><span data-stu-id="17fab-110">Third-party documentation</span></span>

<span data-ttu-id="17fab-111">Puede encontrar ejemplos y documentación para algunas de las API en la serie de blogs por Dave Glick, publicado 2016:</span><span class="sxs-lookup"><span data-stu-id="17fab-111">You can find examples and documentation for some of the API in the following blog series by Dave Glick, published 2016:</span></span>

- [<span data-ttu-id="17fab-112">Exploración de las bibliotecas de NuGet v3, parte 1: Introducción y conceptos</span><span class="sxs-lookup"><span data-stu-id="17fab-112">Exploring the NuGet v3 Libraries, Part 1: Introduction and concepts</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-1)
- [<span data-ttu-id="17fab-113">Exploración de las bibliotecas de NuGet v3, 2ª parte: Buscar paquetes</span><span class="sxs-lookup"><span data-stu-id="17fab-113">Exploring the NuGet v3 Libraries, Part 2: Searching for packages</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-2)
- [<span data-ttu-id="17fab-114">Exploración de las bibliotecas de NuGet v3, parte 3: Instalación de paquetes</span><span class="sxs-lookup"><span data-stu-id="17fab-114">Exploring the NuGet v3 Libraries, Part 3: Installing packages</span></span>](http://daveaglick.com/posts/exploring-the-nuget-v3-libraries-part-3)

> [!Note]
> <span data-ttu-id="17fab-115">Estas entradas de blog escritas poco después de la **3.4.3** versión de NuGet se han publicado paquetes de SDK de cliente.</span><span class="sxs-lookup"><span data-stu-id="17fab-115">These blog posts were written shortly after the **3.4.3** version of the NuGet client SDK packages were released.</span></span>
> <span data-ttu-id="17fab-116">Las versiones más recientes de los paquetes pueden ser incompatibles con la información de las entradas de blog.</span><span class="sxs-lookup"><span data-stu-id="17fab-116">Newer versions of the packages may be incompatible with the information in the blog posts.</span></span>

<span data-ttu-id="17fab-117">Martin Björkström hizo un seguimiento del blog para la serie de blogs de Dave Glick donde presenta un enfoque diferente en mediante el SDK de cliente de NuGet para instalar paquetes de NuGet:</span><span class="sxs-lookup"><span data-stu-id="17fab-117">Martin Björkström did a follow-up blog post to Dave Glick's blog series where he introduces a different approach on using the NuGet Client SDK for installing NuGet packages:</span></span>

- [<span data-ttu-id="17fab-118">Nueva visita a las bibliotecas de NuGet v3</span><span class="sxs-lookup"><span data-stu-id="17fab-118">Revisiting the NuGet v3 Libraries</span></span>](https://martinbjorkstrom.com/posts/2018-09-19-revisiting-nuget-client-libraries)
