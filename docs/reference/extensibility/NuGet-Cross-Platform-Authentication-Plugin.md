---
title: NuGet entre el complemento de autenticación de la plataforma
description: NuGet entre los complementos de autenticación de la plataforma de NuGet.exe, dotnet.exe, msbuild.exe y Visual Studio
author: nkolev92
ms.author: nikolev
manager: rrelyea
ms.date: 07/01/2018
ms.topic: conceptual
ms.openlocfilehash: 02db20e72f67463fffc45f3cba891ae670d67067
ms.sourcegitcommit: 8d5121af528e68789485405e24e2100fda2868d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/23/2018
ms.locfileid: "42794197"
---
# <a name="nuget-cross-platform-authentication-plugin"></a><span data-ttu-id="84180-103">NuGet entre el complemento de autenticación de la plataforma</span><span class="sxs-lookup"><span data-stu-id="84180-103">NuGet cross platform authentication plugin</span></span>

<span data-ttu-id="84180-104">En la versión 4.8, NuGet todos los clientes (NuGet.exe, Visual Studio, dotnet.exe y MSBuild.exe) pueden usar un complemento de autenticación que se crean a partir de la [NuGet cross platform complementos](NuGet-Cross-Platform-Plugins.md) modelo.</span><span class="sxs-lookup"><span data-stu-id="84180-104">In version 4.8+, all NuGet clients (NuGet.exe, Visual Studio, dotnet.exe and MSBuild.exe) can use an authentication plugin built on top of the [NuGet cross platform plugins](NuGet-Cross-Platform-Plugins.md) model.</span></span>

## <a name="authentication-in-dotnetexe"></a><span data-ttu-id="84180-105">Autenticación de dotnet.exe</span><span class="sxs-lookup"><span data-stu-id="84180-105">Authentication in dotnet.exe</span></span>

<span data-ttu-id="84180-106">Visual Studio y NuGet.exe son interactivos de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="84180-106">Visual Studio and NuGet.exe are by default interactive.</span></span> <span data-ttu-id="84180-107">NuGet.exe contendrá un conmutador para que sea [no interactivo](../../tools/nuget-exe-CLI-Reference.md).</span><span class="sxs-lookup"><span data-stu-id="84180-107">NuGet.exe contains a switch to make it [non interactive](../../tools/nuget-exe-CLI-Reference.md).</span></span>
<span data-ttu-id="84180-108">Además, los complementos de NuGet.exe y Visual Studio preguntar al usuario para la entrada.</span><span class="sxs-lookup"><span data-stu-id="84180-108">Additionally the NuGet.exe and Visual Studio plugins prompt the user for input.</span></span>
<span data-ttu-id="84180-109">En dotnet.exe no hay pedir confirmación y el valor predeterminado es no interactivo.</span><span class="sxs-lookup"><span data-stu-id="84180-109">In dotnet.exe there is no prompting and the default is non interactive.</span></span>

<span data-ttu-id="84180-110">El mecanismo de autenticación de dotnet.exe es flujo de dispositivos.</span><span class="sxs-lookup"><span data-stu-id="84180-110">The authentication mechanism in dotnet.exe is device flow.</span></span> <span data-ttu-id="84180-111">Cuando la restauración o agregar la operación del paquete se ejecuta de forma interactiva, la operación se bloquea e instrucciones al usuario cómo para completar las autenticaciones se proporcionará en la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="84180-111">When the restore or add package operation is run interactively, the operation blocks and instructions to the user how to complete the authentications will be provided on the command line.</span></span>
<span data-ttu-id="84180-112">Cuando el usuario completa la autenticación de la operación continuará.</span><span class="sxs-lookup"><span data-stu-id="84180-112">When the user completes the authentication the operation will continue.</span></span>

<span data-ttu-id="84180-113">Para que la operación sea interactivo, uno debe pasar `--interactive`.</span><span class="sxs-lookup"><span data-stu-id="84180-113">To make the operation interactive, one should pass `--interactive`.</span></span>
<span data-ttu-id="84180-114">Actualmente solo la configuración explícita `dotnet restore` y `dotnet add package` comandos admiten un modificador interactivo.</span><span class="sxs-lookup"><span data-stu-id="84180-114">Currently only the explicit `dotnet restore` and `dotnet add package` commands support an interactive switch.</span></span>
<span data-ttu-id="84180-115">No hay ningún conmutador interactivo en `dotnet build` y `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="84180-115">There is no interactive switch on `dotnet build` and `dotnet publish`.</span></span>

## <a name="authentication-in-msbuild"></a><span data-ttu-id="84180-116">Autenticación de MSBuild</span><span class="sxs-lookup"><span data-stu-id="84180-116">Authentication in MSBuild</span></span>

<span data-ttu-id="84180-117">Es similar a dotnet.exe, MSBuild.exe que no son que el mecanismo de autenticación de MSBuild.exe interactivo es flujo de dispositivos de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="84180-117">Similar to dotnet.exe, MSBuild.exe is by default non interactive the MSBuild.exe authentication mechanism is device flow.</span></span>
<span data-ttu-id="84180-118">Para permitir la restauración pausar y esperar la autenticación, llamar a la restauración con `msbuild /t:restore /p:NuGetInteractive="true"`.</span><span class="sxs-lookup"><span data-stu-id="84180-118">To allow the restore to pause and wait for authentication, call restore with `msbuild /t:restore /p:NuGetInteractive="true"`.</span></span>

## <a name="creating-a-cross-platform-authentication-plugin"></a><span data-ttu-id="84180-119">Crear un complemento de autenticación multiplataforma</span><span class="sxs-lookup"><span data-stu-id="84180-119">Creating a cross platform authentication plugin</span></span>

<span data-ttu-id="84180-120">Puede encontrar una implementación de ejemplo en [MSCredProvider complemento](https://github.com/Microsoft/mscredprovider).</span><span class="sxs-lookup"><span data-stu-id="84180-120">A sample implementation can be found in [MSCredProvider plugin](https://github.com/Microsoft/mscredprovider).</span></span>

<span data-ttu-id="84180-121">Es muy importante que los complementos se ajustan a los requisitos de seguridad establecidos por las herramientas de cliente de NuGet.</span><span class="sxs-lookup"><span data-stu-id="84180-121">It's very important that the plugins conforms to the security requirements set forth by the NuGet client tools.</span></span>
<span data-ttu-id="84180-122">La mínima necesaria es la versión para un complemento como un complemento de autenticación *2.0.0*.</span><span class="sxs-lookup"><span data-stu-id="84180-122">The minimum required version for a plugin to be an authentication plugin is *2.0.0*.</span></span>
<span data-ttu-id="84180-123">NuGet llevará a cabo el protocolo de enlace con el complemento y la consulta para las notificaciones de la operación admitida.</span><span class="sxs-lookup"><span data-stu-id="84180-123">NuGet will perform the handshake with the plugin and query for the supported operation claims.</span></span>
<span data-ttu-id="84180-124">El paquete NuGet entre el complemento de plataforma, consulte [los mensajes del protocolo](NuGet-Cross-Platform-Plugins.md#protocol-messages-index) para obtener más información acerca de los mensajes específicos.</span><span class="sxs-lookup"><span data-stu-id="84180-124">Please refer to the NuGet cross platform plugin [protocol messages](NuGet-Cross-Platform-Plugins.md#protocol-messages-index) for more details about the specific messages.</span></span>

<span data-ttu-id="84180-125">NuGet establecerá el nivel de registro y proporcionar información de proxy para el complemento cuando sea aplicable.</span><span class="sxs-lookup"><span data-stu-id="84180-125">NuGet will set the log level and provide proxy information to the plugin when applicable.</span></span>
<span data-ttu-id="84180-126">Registro para el paquete NuGet consola solo es aceptable después NuGet establece el nivel de registro en el complemento.</span><span class="sxs-lookup"><span data-stu-id="84180-126">Logging to the NuGet console is only acceptable after NuGet has set the log level to the plugin.</span></span>

- <span data-ttu-id="84180-127">Comportamiento de autenticación de complemento de .NET framework</span><span class="sxs-lookup"><span data-stu-id="84180-127">.NET Framework plugin authentication behavior</span></span>

<span data-ttu-id="84180-128">En .NET Framework, los complementos pueden solicitar al usuario para la entrada, en forma de un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-128">In .NET Framework, the plugins are allowed to prompt a user for input, in the form of a dialog.</span></span>

- <span data-ttu-id="84180-129">Comportamiento de autenticación de complemento de .NET core</span><span class="sxs-lookup"><span data-stu-id="84180-129">.NET Core plugin authentication behavior</span></span>

<span data-ttu-id="84180-130">En .NET Core, no se puede mostrar un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-130">In .NET Core, a dialog cannot be shown.</span></span> <span data-ttu-id="84180-131">Los complementos deben usar el flujo de dispositivos para autenticarse.</span><span class="sxs-lookup"><span data-stu-id="84180-131">The plugins should use device flow to authenticate.</span></span>
<span data-ttu-id="84180-132">El complemento puede enviar mensajes de registro a NuGet con instrucciones para el usuario.</span><span class="sxs-lookup"><span data-stu-id="84180-132">The plugin can send log messages to NuGet with instructions to the user.</span></span>
<span data-ttu-id="84180-133">Tenga en cuenta que está disponible el registro después de que se ha establecido el nivel de registro en el complemento.</span><span class="sxs-lookup"><span data-stu-id="84180-133">Note that logging is available after the log level has been set to the plugin.</span></span>
<span data-ttu-id="84180-134">NuGet no tendrán ninguna entrada interactiva desde la línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="84180-134">NuGet will not take any interactive input from the command line.</span></span>

<span data-ttu-id="84180-135">Cuando el cliente llama al complemento con un credenciales de autenticación obtener, los complementos deben ajustarse al conmutador interactividad y respeta el modificador de cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-135">When the client calls the plugin with a Get Authentication Credentials, the plugins need to conform to the interactivity switch and respect the dialog switch.</span></span> 

<span data-ttu-id="84180-136">En la tabla siguiente se resume cómo debe comportarse el complemento para todas las combinaciones.</span><span class="sxs-lookup"><span data-stu-id="84180-136">The following table summarizes how the plugin should behave for all combinations.</span></span>

| <span data-ttu-id="84180-137">IsNonInteractive</span><span class="sxs-lookup"><span data-stu-id="84180-137">IsNonInteractive</span></span> | <span data-ttu-id="84180-138">CanShowDialog</span><span class="sxs-lookup"><span data-stu-id="84180-138">CanShowDialog</span></span> | <span data-ttu-id="84180-139">Comportamiento de complemento</span><span class="sxs-lookup"><span data-stu-id="84180-139">Plugin behavior</span></span> |
| ---------------- | ------------- | --------------- |
| <span data-ttu-id="84180-140">true</span><span class="sxs-lookup"><span data-stu-id="84180-140">true</span></span> | <span data-ttu-id="84180-141">true</span><span class="sxs-lookup"><span data-stu-id="84180-141">true</span></span> | <span data-ttu-id="84180-142">El modificador IsNonInteractive tiene prioridad sobre el conmutador de cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-142">The IsNonInteractive switch takes precedence over the dialog switch.</span></span> <span data-ttu-id="84180-143">El complemento no se puede abrir un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-143">The plugin is not allowed to pop a dialog.</span></span> <span data-ttu-id="84180-144">Esta combinación solo es válida para los complementos de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84180-144">This combination is only valid for .NET Framework plugins</span></span> |
| <span data-ttu-id="84180-145">true</span><span class="sxs-lookup"><span data-stu-id="84180-145">true</span></span> | <span data-ttu-id="84180-146">False</span><span class="sxs-lookup"><span data-stu-id="84180-146">false</span></span> | <span data-ttu-id="84180-147">El modificador IsNonInteractive tiene prioridad sobre el conmutador de cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-147">The IsNonInteractive switch takes precedence over the dialog switch.</span></span> <span data-ttu-id="84180-148">El complemento no se permite para bloquear.</span><span class="sxs-lookup"><span data-stu-id="84180-148">The plugin is not allowed to block.</span></span> <span data-ttu-id="84180-149">Esta combinación solo es válida para los complementos de .NET Core</span><span class="sxs-lookup"><span data-stu-id="84180-149">This combination is only valid for .NET Core plugins</span></span> |
| <span data-ttu-id="84180-150">False</span><span class="sxs-lookup"><span data-stu-id="84180-150">false</span></span> | <span data-ttu-id="84180-151">true</span><span class="sxs-lookup"><span data-stu-id="84180-151">true</span></span> | <span data-ttu-id="84180-152">El complemento debe mostrar un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-152">The plugin should show a dialog.</span></span> <span data-ttu-id="84180-153">Esta combinación solo es válida para los complementos de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="84180-153">This combination is only valid for .NET Framework plugins</span></span> |
| <span data-ttu-id="84180-154">False</span><span class="sxs-lookup"><span data-stu-id="84180-154">false</span></span> | <span data-ttu-id="84180-155">False</span><span class="sxs-lookup"><span data-stu-id="84180-155">false</span></span> | <span data-ttu-id="84180-156">El complemento debe/puede no mostrar un cuadro de diálogo.</span><span class="sxs-lookup"><span data-stu-id="84180-156">The plugin should/can not show a dialog.</span></span> <span data-ttu-id="84180-157">El complemento debe usar el flujo de dispositivo para autenticar mediante el registro de un mensaje de la instrucción mediante el registrador.</span><span class="sxs-lookup"><span data-stu-id="84180-157">The plugin should use device flow to authenticate by logging an instruction message via the logger.</span></span> <span data-ttu-id="84180-158">Esta combinación solo es válida para los complementos de .NET Core</span><span class="sxs-lookup"><span data-stu-id="84180-158">This combination is only valid for .NET Core plugins</span></span> |

<span data-ttu-id="84180-159">Consulte las especificaciones siguientes antes de escribir un complemento.</span><span class="sxs-lookup"><span data-stu-id="84180-159">Please refer to the following specs before writing a plugin.</span></span>

- [<span data-ttu-id="84180-160">Complemento de descarga del paquete de NuGet</span><span class="sxs-lookup"><span data-stu-id="84180-160">NuGet Package Download Plugin</span></span>](https://github.com/NuGet/Home/wiki/NuGet-Package-Download-Plugin)
- [<span data-ttu-id="84180-161">NuGet entre el complemento de autenticación plat</span><span class="sxs-lookup"><span data-stu-id="84180-161">NuGet cross plat authentication plugin</span></span>](https://github.com/NuGet/Home/wiki/NuGet-cross-plat-authentication-plugin)