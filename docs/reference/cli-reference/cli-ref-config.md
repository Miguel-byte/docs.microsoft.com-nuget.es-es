---
title: Comando de configuración de la CLI de NuGet
description: Referencia del comando de configuración de Nuget. exe
author: karann-msft
ms.author: karann
ms.date: 01/18/2018
ms.topic: reference
ms.openlocfilehash: 51c4c9937483e7f8a57356515c06a60c0f9e6f62
ms.sourcegitcommit: efc18d484fdf0c7a8979b564dcb191c030601bb4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "68327852"
---
# <a name="config-command-nuget-cli"></a><span data-ttu-id="dbead-103">comando config (CLI de NuGet)</span><span class="sxs-lookup"><span data-stu-id="dbead-103">config command (NuGet CLI)</span></span>

<span data-ttu-id="dbead-104">**Se aplica a:** todas &bullet; **las versiones compatibles**: todas</span><span class="sxs-lookup"><span data-stu-id="dbead-104">**Applies to:** all &bullet; **Supported versions**: all</span></span>

<span data-ttu-id="dbead-105">Obtiene o establece los valores de configuración de NuGet.</span><span class="sxs-lookup"><span data-stu-id="dbead-105">Gets or sets NuGet configuration values.</span></span> <span data-ttu-id="dbead-106">Para obtener más uso, consulte [configuraciones comunes de NuGet](../../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="dbead-106">For additional usage, see [Common NuGet configurations](../../consume-packages/configuring-nuget-behavior.md).</span></span> <span data-ttu-id="dbead-107">Para obtener más información sobre los nombres de clave permitidos, consulte la [Referencia del archivo de configuración de NuGet](../nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="dbead-107">For details on allowable key names, refer to the [NuGet config file reference](../nuget-config-file.md).</span></span>

## <a name="usage"></a><span data-ttu-id="dbead-108">Uso</span><span class="sxs-lookup"><span data-stu-id="dbead-108">Usage</span></span>

```cli
nuget config -Set <name>=[<value>] [<name>=<value> ...] [options]
nuget config -AsPath <name> [options]
```

<span data-ttu-id="dbead-109">donde `<name>` y`<value>` especifican un par clave-valor que se establecerá en la configuración.</span><span class="sxs-lookup"><span data-stu-id="dbead-109">where `<name>` and `<value>` specify a key-value pair to be set in the configuration.</span></span> <span data-ttu-id="dbead-110">Puede especificar tantos pares como desee.</span><span class="sxs-lookup"><span data-stu-id="dbead-110">You can specify as many pairs as desired.</span></span> <span data-ttu-id="dbead-111">Para quitar un valor, especifique el nombre y el `=` signo pero no el valor.</span><span class="sxs-lookup"><span data-stu-id="dbead-111">To remove a value, specify the name and the `=` sign but no value.</span></span>

<span data-ttu-id="dbead-112">Para ver los nombres de clave permitidos, consulte la [Referencia del archivo de configuración de NuGet](../nuget-config-file.md).</span><span class="sxs-lookup"><span data-stu-id="dbead-112">For allowable key names, see the [NuGet config file reference](../nuget-config-file.md).</span></span>

<span data-ttu-id="dbead-113">En NuGet 3.4 +, `<value>` puede usar [variables de entorno](cli-ref-environment-variables.md).</span><span class="sxs-lookup"><span data-stu-id="dbead-113">In NuGet 3.4+, `<value>` can use [environment variables](cli-ref-environment-variables.md).</span></span>

## <a name="options"></a><span data-ttu-id="dbead-114">Opciones</span><span class="sxs-lookup"><span data-stu-id="dbead-114">Options</span></span>

| <span data-ttu-id="dbead-115">Opción</span><span class="sxs-lookup"><span data-stu-id="dbead-115">Option</span></span> | <span data-ttu-id="dbead-116">DESCRIPCIÓN</span><span class="sxs-lookup"><span data-stu-id="dbead-116">Description</span></span> |
| --- | --- |
| <span data-ttu-id="dbead-117">AsPath</span><span class="sxs-lookup"><span data-stu-id="dbead-117">AsPath</span></span> | <span data-ttu-id="dbead-118">Devuelve el valor de configuración como una ruta de acceso `-Set` , que se omite cuando se usa.</span><span class="sxs-lookup"><span data-stu-id="dbead-118">Returns the config value as a path, ignored when `-Set` is used.</span></span> |
| <span data-ttu-id="dbead-119">ConfigFile</span><span class="sxs-lookup"><span data-stu-id="dbead-119">ConfigFile</span></span> | <span data-ttu-id="dbead-120">El archivo de configuración de NuGet que se va a modificar.</span><span class="sxs-lookup"><span data-stu-id="dbead-120">The NuGet configuration file to modify.</span></span> <span data-ttu-id="dbead-121">Si no se especifica `%AppData%\NuGet\NuGet.Config` , se usa ( `~/.nuget/NuGet/NuGet.Config` Windows) o (Mac/Linux).</span><span class="sxs-lookup"><span data-stu-id="dbead-121">If not specified, `%AppData%\NuGet\NuGet.Config` (Windows) or `~/.nuget/NuGet/NuGet.Config` (Mac/Linux) is used.</span></span>|
| <span data-ttu-id="dbead-122">ForceEnglishOutput</span><span class="sxs-lookup"><span data-stu-id="dbead-122">ForceEnglishOutput</span></span> | <span data-ttu-id="dbead-123">*(3.5 +)* Fuerza a Nuget. exe a ejecutarse mediante una referencia cultural invariable basada en inglés.</span><span class="sxs-lookup"><span data-stu-id="dbead-123">*(3.5+)* Forces nuget.exe to run using an invariant, English-based culture.</span></span> |
| <span data-ttu-id="dbead-124">Help</span><span class="sxs-lookup"><span data-stu-id="dbead-124">Help</span></span> | <span data-ttu-id="dbead-125">Muestra información de ayuda para el comando.</span><span class="sxs-lookup"><span data-stu-id="dbead-125">Displays help information for the command.</span></span> |
| <span data-ttu-id="dbead-126">NonInteractive</span><span class="sxs-lookup"><span data-stu-id="dbead-126">NonInteractive</span></span> | <span data-ttu-id="dbead-127">Suprime los mensajes de entrada o confirmaciones de usuario.</span><span class="sxs-lookup"><span data-stu-id="dbead-127">Suppresses prompts for user input or confirmations.</span></span> |
| <span data-ttu-id="dbead-128">Verbosity</span><span class="sxs-lookup"><span data-stu-id="dbead-128">Verbosity</span></span> | <span data-ttu-id="dbead-129">Especifica la cantidad de detalle que se muestra en la salida: *normal*, *silenciosa*, *detallado*.</span><span class="sxs-lookup"><span data-stu-id="dbead-129">Specifies the amount of detail displayed in the output: *normal*, *quiet*, *detailed*.</span></span> |

<span data-ttu-id="dbead-130">Vea también [variables de entorno](cli-ref-environment-variables.md)</span><span class="sxs-lookup"><span data-stu-id="dbead-130">Also see [Environment variables](cli-ref-environment-variables.md)</span></span>

### <a name="examples"></a><span data-ttu-id="dbead-131">Ejemplos</span><span class="sxs-lookup"><span data-stu-id="dbead-131">Examples</span></span>

```cli
nuget config -Set repositoryPath=c:\packages -configfile c:\my.config

nuget config -Set repositoryPath=

nuget config -Set repositoryPath=%PACKAGE_REPO% -configfile %ProgramData%\NuGet\NuGetDefaults.Config

nuget config -Set HTTP_PROXY=http://127.0.0.1 -set HTTP_PROXY.USER=domain\user
```