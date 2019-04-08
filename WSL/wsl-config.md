---
title: Administrar las distribuciones de Linux
description: Hacer referencia a enumerar y configurar varias distribuciones de Linux que se ejecuta en el subsistema de Windows para Linux.
keywords: BashOnWindows, bash, wsl, windows, subsistema de windows para linux, windowssubsystem, ubuntu, wsl.conf, wslconfig
author: scooley
ms.author: scooley
ms.date: 02/7/2018
ms.topic: article
ms.assetid: 7ca59bd7-d9d3-4f6d-8b92-b8faa9bcf250
ms.custom: seodec18
ms.openlocfilehash: c806552750f413fcb75f989d868a57cc939af64a
ms.sourcegitcommit: ca08a78925880ed3eccf88edb30def16c83f2543
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/04/2019
ms.locfileid: "59063503"
---
# <a name="manage-and-configure-windows-subsystem-for-linux"></a><span data-ttu-id="5997b-104">Administrar y configurar el subsistema de Windows para Linux</span><span class="sxs-lookup"><span data-stu-id="5997b-104">Manage and configure Windows Subsystem for Linux</span></span>

> <span data-ttu-id="5997b-105">Se aplica a Windows 10 Fall Creators Update y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5997b-105">Applies to Windows 10 Fall Creators Update and later.</span></span>  <span data-ttu-id="5997b-106">Consulte nuestro actualizada [Guía de instalación](./install_guide.md) para probar nuevas características de administración y empezar a ejecutar varias distribuciones de Linux desde el Store de Windows.</span><span class="sxs-lookup"><span data-stu-id="5997b-106">See our updated [installation guide](./install_guide.md) to try new management features and start running multiple Linux distributions from the Windows Store.</span></span>

## <a name="ways-to-run-wsl"></a><span data-ttu-id="5997b-107">Modos de ejecutar WSL</span><span class="sxs-lookup"><span data-stu-id="5997b-107">Ways to run WSL</span></span>

<span data-ttu-id="5997b-108">Hay muchas maneras de ejecutar Linux con el subsistema de Windows para Linux.</span><span class="sxs-lookup"><span data-stu-id="5997b-108">There are many ways to run Linux with the Windows Subsystem for Linux.</span></span>

1. `[distro]` <span data-ttu-id="5997b-109">ie</span><span class="sxs-lookup"><span data-stu-id="5997b-109">ie</span></span> `ubuntu`
1. `wsl.exe` <span data-ttu-id="5997b-110">o bien</span><span class="sxs-lookup"><span data-stu-id="5997b-110">or</span></span> `bash.exe`
1. `wsl [command]` <span data-ttu-id="5997b-111">o bien</span><span class="sxs-lookup"><span data-stu-id="5997b-111">or</span></span> `bash -c [command]`

<span data-ttu-id="5997b-112">Qué método debe usar depende de lo que está haciendo.</span><span class="sxs-lookup"><span data-stu-id="5997b-112">Which method you should use depends on what you're doing.</span></span>

### <a name="launch-wsl-by-distribution"></a><span data-ttu-id="5997b-113">Iniciar WSL según la distribución</span><span class="sxs-lookup"><span data-stu-id="5997b-113">Launch WSL by distribution</span></span>

<span data-ttu-id="5997b-114">Distribución en su propia ventana de consola inicia ejecutando una distribución mediante su aplicación específica de cada distribución.</span><span class="sxs-lookup"><span data-stu-id="5997b-114">Running a distribution using it's distro-specific application launches that distribution in it's own console window.</span></span>

![Inicie WSL desde el menú Inicio](media/start-launch.png)

<span data-ttu-id="5997b-116">Es el mismo que al hacer clic en "Iniciar" en el Store de Windows.</span><span class="sxs-lookup"><span data-stu-id="5997b-116">It is the same as clicking "Launch" in the Windows Store.</span></span>

![Iniciar WSL desde el Store de Windows](media/store-launch.png)

<span data-ttu-id="5997b-118">También puede ejecutar la distribución de la línea de comandos ejecutando `[distribution].exe`.</span><span class="sxs-lookup"><span data-stu-id="5997b-118">You can also run the distribution from the command line by running `[distribution].exe`.</span></span>

<span data-ttu-id="5997b-119">La desventaja de la ejecución de una distribución de la línea de comandos de esta manera es que cambiará automáticamente el directorio de trabajo desde el directorio actual al directorio principal de la distribución.</span><span class="sxs-lookup"><span data-stu-id="5997b-119">The disadvantage of running a distribution from the command line in this way is that it will automatically change your working directory from the current directory to the distribution's home directory.</span></span>

**<span data-ttu-id="5997b-120">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-120">Example:</span></span>**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> ubuntu

scooley@scooley-elmer:~$ pwd
/home/scooley
scooley@scooley-elmer:~$ exit
logout

PS C:\Users\sarah>
```

### <a name="wsl-and-wsl-command"></a><span data-ttu-id="5997b-121">wsl and wsl [command]</span><span class="sxs-lookup"><span data-stu-id="5997b-121">wsl and wsl [command]</span></span>

<span data-ttu-id="5997b-122">La mejor manera de ejecutar WSL desde la línea de comandos usa `wsl.exe`.</span><span class="sxs-lookup"><span data-stu-id="5997b-122">The best way to run WSL from the command line is using `wsl.exe`.</span></span>

**<span data-ttu-id="5997b-123">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-123">Example:</span></span>**

```console
PS C:\Users\sarah> pwd

Path
----
C:\Users\sarah

PS C:\Users\sarah> wsl

scooley@scooley-elmer:/mnt/c/Users/sarah$ pwd
/mnt/c/Users/sarah
```

<span data-ttu-id="5997b-124">No sólo hace `wsl` mantener el directorio de trabajo actual en su lugar, le permite ejecutar un comando único a lo largo de los comandos de Windows de lado.</span><span class="sxs-lookup"><span data-stu-id="5997b-124">Not only does `wsl` keep the current working directory in place, it lets you run a single command along side Windows commands.</span></span>

**<span data-ttu-id="5997b-125">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-125">Example:</span></span>**

```console
PS C:\Users\sarah> Get-Date

Sunday, March 11, 2018 7:54:05 PM

PS C:\Users\sarah> wsl
scooley@scooley-elmer:/mnt/c/Users/sarah$ date
Sun Mar 11 19:56:57 DST 2018
scooley@scooley-elmer:/mnt/c/Users/sarah$ exit
logout

PS C:\Users\sarah> wsl date
Sun Mar 11 19:55:47 DST 2018
```

**<span data-ttu-id="5997b-126">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-126">Example:</span></span>**

```console
PS C:\Users\sarah> Get-VM

Name            State CPUUsage(%) MemoryAssigned(M) Uptime   Status
----            ----- ----------- ----------------- ------   ------
Server17093     Off   0           0                 00:00:00 Opera...
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
Windows         Off   0           0                 00:00:00 Opera...


PS C:\Users\sarah> Get-VM | wsl grep "Ubuntu"
Ubuntu          Off   0           0                 00:00:00 Opera...
Ubuntu (bionic) Off   0           0                 00:00:00 Opera...
PS C:\Users\sarah>
```


## <a name="managing-multiple-linux-distributions"></a><span data-ttu-id="5997b-127">Administrar varias distribuciones de Linux</span><span class="sxs-lookup"><span data-stu-id="5997b-127">Managing multiple Linux Distributions</span></span>

### <a name="windows-10-version-1903-and-later"></a><span data-ttu-id="5997b-128">Versión de Windows 10 1903 y versiones posterior</span><span class="sxs-lookup"><span data-stu-id="5997b-128">Windows 10 Version 1903 and later</span></span>

<span data-ttu-id="5997b-129">Puede usar `wsl.exe` para administrar sus distribuciones en el subsistema de Windows para Linux (WSL), incluidos listado distribuciones disponibles, el establecimiento de una distribución de forma predeterminada y desinstalación de las distribuciones.</span><span class="sxs-lookup"><span data-stu-id="5997b-129">You can use `wsl.exe` to manage your distributions in the Windows Subsystem for Linux (WSL), including listing available distributions, setting a default distribution, and uninstalling distributions.</span></span>

<span data-ttu-id="5997b-130">Cada distribución de Linux independiente administra sus propias configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5997b-130">Each Linux distribution independently manages its own configurations.</span></span> <span data-ttu-id="5997b-131">Para ver los comandos específicos de distribución, ejecute `[distro.exe] /?`.</span><span class="sxs-lookup"><span data-stu-id="5997b-131">To see distribution-specific commands, run `[distro.exe] /?`.</span></span>  <span data-ttu-id="5997b-132">Por ejemplo, `ubuntu /?`.</span><span class="sxs-lookup"><span data-stu-id="5997b-132">For example `ubuntu /?`.</span></span>

#### <a name="list-distributions"></a><span data-ttu-id="5997b-133">Distribuciones de lista</span><span class="sxs-lookup"><span data-stu-id="5997b-133">List distributions</span></span>

`wsl -l` <span data-ttu-id="5997b-134">,</span><span class="sxs-lookup"><span data-stu-id="5997b-134">,</span></span> `wsl --list`  
<span data-ttu-id="5997b-135">Listas disponibles distribuciones de Linux disponibles en WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-135">Lists available Linux distributions available to WSL.</span></span>  <span data-ttu-id="5997b-136">Si se muestra una distribución, se instala y está lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="5997b-136">If a distribution is listed, it's installed and ready to use.</span></span>

`wsl --list --all`   
<span data-ttu-id="5997b-137">Enumera todas las distribuciones, las que no están actualmente utilizable incluidas.</span><span class="sxs-lookup"><span data-stu-id="5997b-137">Lists all distributions, including ones that aren't currently usable.</span></span>  <span data-ttu-id="5997b-138">Se puede estar en el proceso de instalar, desinstalar, o se encuentran en un estado interrumpido.</span><span class="sxs-lookup"><span data-stu-id="5997b-138">They may be in the process of installing, uninstalling, or are in a broken state.</span></span>  

`wsl --list --running`   
<span data-ttu-id="5997b-139">Enumera todas las distribuciones que se están ejecutando actualmente.</span><span class="sxs-lookup"><span data-stu-id="5997b-139">Lists all distributions that are currently running.</span></span>

#### <a name="set-a-default-distribution"></a><span data-ttu-id="5997b-140">Configurar una distribución predeterminada</span><span class="sxs-lookup"><span data-stu-id="5997b-140">Set a default distribution</span></span>

<span data-ttu-id="5997b-141">La distribución de WSL predeterminada es la que se ejecuta cuando se ejecuta `wsl` en una línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="5997b-141">The default WSL distribution is the one that runs when you run `wsl` on a command line.</span></span>

`wsl -s <DistributionName>`<span data-ttu-id="5997b-142">,</span><span class="sxs-lookup"><span data-stu-id="5997b-142">,</span></span> `wsl --setdefault <DistributionName>`

<span data-ttu-id="5997b-143">La distribución predeterminada se establece en `<DistributionName>`.</span><span class="sxs-lookup"><span data-stu-id="5997b-143">Sets the default distribution to `<DistributionName>`.</span></span>

**<span data-ttu-id="5997b-144">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-144">Example:</span></span>**  
`wsl -s Ubuntu` <span data-ttu-id="5997b-145">establecer la distribución de forma predeterminada en Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-145">would set my default distribution to Ubuntu.</span></span>  <span data-ttu-id="5997b-146">Ahora cuando ejecuto `wsl npm init` se ejecutará en Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-146">Now when I run `wsl npm init` it will run in Ubuntu.</span></span>  <span data-ttu-id="5997b-147">Si ejecuto `wsl` abrirá una sesión de Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-147">If I run `wsl` it will open an Ubuntu session.</span></span>

#### <a name="unregister-and-reinstall-a-distribution"></a><span data-ttu-id="5997b-148">Anular el registro y volver a instalar una distribución</span><span class="sxs-lookup"><span data-stu-id="5997b-148">Unregister and reinstall a distribution</span></span>

<span data-ttu-id="5997b-149">Mientras Linux distribuciones pueden instalarse a través de la Windows almacén, no se puede desinstalar a través de la tienda.</span><span class="sxs-lookup"><span data-stu-id="5997b-149">While Linux distributions can be installed through the Windows store, they can't be uninstalled through the store.</span></span>  <span data-ttu-id="5997b-150">WSL Config permite distribuciones se anula el registro o desinstalado.</span><span class="sxs-lookup"><span data-stu-id="5997b-150">WSL Config allows distributions to be unregistered/uninstalled.</span></span>

<span data-ttu-id="5997b-151">Al anular el registro también permite que las distribuciones deben volver a instalar.</span><span class="sxs-lookup"><span data-stu-id="5997b-151">Unregistering also allows distributions to be reinstalled.</span></span>

> <span data-ttu-id="5997b-152">**Precaución:** Una vez que se anula el registro, se perderán permanentemente todos los datos, configuraciones y asociadas con esa distribución de software.</span><span class="sxs-lookup"><span data-stu-id="5997b-152">**Caution:** Once unregistered, all data, settings, and software associated with that distribution will be permanently lost.</span></span>  <span data-ttu-id="5997b-153">Volver a instalar desde el almacén se instalará una copia limpia de la distribución.</span><span class="sxs-lookup"><span data-stu-id="5997b-153">Reinstalling from the store will install a clean copy of the distribution.</span></span>

`wsl --unregister <DistributionName>`  
<span data-ttu-id="5997b-154">Anula el registro de la distribución de WSL por lo que puede volver a instalar o limpiado.</span><span class="sxs-lookup"><span data-stu-id="5997b-154">Unregisters the distribution from WSL so it can be reinstalled or cleaned up.</span></span>

<span data-ttu-id="5997b-155">Por ejemplo: `wsl -unregister Ubuntu` quitarían Ubuntu desde las distribuciones disponibles en WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-155">For example: `wsl -unregister Ubuntu` would remove Ubuntu from the distributions available in WSL.</span></span>  <span data-ttu-id="5997b-156">Cuando ejecuto `wsl --list` no se mostrará.</span><span class="sxs-lookup"><span data-stu-id="5997b-156">When I run `wsl --list` it will not be listed.</span></span>

<span data-ttu-id="5997b-157">Para volver a instalar, busque la distribución en el Store de Windows y seleccione "Iniciar".</span><span class="sxs-lookup"><span data-stu-id="5997b-157">To reinstall, find the distribution in the Windows Store and select "Launch".</span></span>

#### <a name="run-as-a-specific-user"></a><span data-ttu-id="5997b-158">Ejecutar como un usuario específico</span><span class="sxs-lookup"><span data-stu-id="5997b-158">Run as a specific user</span></span>

`wsl -u <Username>`<span data-ttu-id="5997b-159">,</span><span class="sxs-lookup"><span data-stu-id="5997b-159">,</span></span> `wsl --user <Username>`

<span data-ttu-id="5997b-160">Ejecute WSL como el usuario especificado.</span><span class="sxs-lookup"><span data-stu-id="5997b-160">Run WSL as the specified user.</span></span> <span data-ttu-id="5997b-161">Tenga en cuenta que el usuario debe existir dentro de la distribución de WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-161">Please note that user must exist inside of the WSL distribution.</span></span>

#### <a name="run-a-specific-distribution"></a><span data-ttu-id="5997b-162">Ejecutar una distribución específica</span><span class="sxs-lookup"><span data-stu-id="5997b-162">Run a specific distribution</span></span>

`wsl --d <DistributionName>`<span data-ttu-id="5997b-163">,</span><span class="sxs-lookup"><span data-stu-id="5997b-163">,</span></span> `wsl --distribution <DistributionName>`

<span data-ttu-id="5997b-164">Ejecutar una distribución de WSL especificada, puede usarse para enviar comandos a una distribución específica sin tener que cambiar su valor predeterminado.</span><span class="sxs-lookup"><span data-stu-id="5997b-164">Run a specified distribution of WSL, can be used to send commands to a specific distribution without having to change your default.</span></span>

### <a name="versions-earlier-than-windows-10-version-1903"></a><span data-ttu-id="5997b-165">Versiones anteriores a Windows 10 versión 1903</span><span class="sxs-lookup"><span data-stu-id="5997b-165">Versions Earlier than Windows 10 Version 1903</span></span>

<span data-ttu-id="5997b-166">Configuración de WSL (`wslconfig.exe`) es una herramienta de línea de comandos para administrar las distribuciones de Linux que se ejecuta en el subsistema de Windows para Linux (WSL).</span><span class="sxs-lookup"><span data-stu-id="5997b-166">WSL Config (`wslconfig.exe`) is a command-line tool for managing Linux distributions running on the Windows Subsystem for Linux (WSL).</span></span>  <span data-ttu-id="5997b-167">Permite enumerar distribuciones disponibles, establecer una distribución de forma predeterminada y desinstalar las distribuciones.</span><span class="sxs-lookup"><span data-stu-id="5997b-167">It lets you list available distributions, set a default distribution, and uninstall distributions.</span></span>

<span data-ttu-id="5997b-168">Mientras WSL configuración es útil para los valores que abarcan o coordinan las distribuciones, cada distribución de Linux independiente administra sus propias configuraciones.</span><span class="sxs-lookup"><span data-stu-id="5997b-168">While WSL Config is helpful for settings that span or coordinate distributions, each Linux distribution independently manages its own configurations.</span></span>  <span data-ttu-id="5997b-169">Para ver los comandos específicos de distribución, ejecute `[distro.exe] /?`.</span><span class="sxs-lookup"><span data-stu-id="5997b-169">To see distribution-specific commands, run `[distro.exe] /?`.</span></span>  <span data-ttu-id="5997b-170">Por ejemplo, `ubuntu /?`.</span><span class="sxs-lookup"><span data-stu-id="5997b-170">For example `ubuntu /?`.</span></span>

<span data-ttu-id="5997b-171">Para ver todas las opciones disponibles para wslconfig, ejecute:</span><span class="sxs-lookup"><span data-stu-id="5997b-171">To see all available options for wslconfig, run:</span></span>  `wslconfig /?`

```console
wslconfig.exe
Performs administrative operations on Windows Subsystem for Linux

Usage:
    /l, /list [/all] - Lists registered distributions.
        /all - Optionally list all distributions, including distributions that
               are currently being installed or uninstalled.
    /s, /setdefault <DistributionName> - Sets the specified distribution as the default.
    /u, /unregister <DistributionName> - Unregisters a distribution.
```

#### <a name="list-distributions"></a><span data-ttu-id="5997b-172">Distribuciones de lista</span><span class="sxs-lookup"><span data-stu-id="5997b-172">List distributions</span></span>

`wslconfig /list`  
<span data-ttu-id="5997b-173">Listas disponibles distribuciones de Linux disponibles en WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-173">Lists available Linux distributions available to WSL.</span></span>  <span data-ttu-id="5997b-174">Si se muestra una distribución, se instala y está lista para usarse.</span><span class="sxs-lookup"><span data-stu-id="5997b-174">If a distribution is listed, it's installed and ready to use.</span></span>

`wslconfig /list /all`  
<span data-ttu-id="5997b-175">Enumera todas las distribuciones, las que no están actualmente utilizable incluidas.</span><span class="sxs-lookup"><span data-stu-id="5997b-175">Lists all distributions, including ones that aren't currently usable.</span></span>  <span data-ttu-id="5997b-176">Se puede estar en el proceso de instalar, desinstalar, o se encuentran en un estado interrumpido.</span><span class="sxs-lookup"><span data-stu-id="5997b-176">They may be in the process of installing, uninstalling, or are in a broken state.</span></span>  

#### <a name="set-a-default-distribution"></a><span data-ttu-id="5997b-177">Configurar una distribución predeterminada</span><span class="sxs-lookup"><span data-stu-id="5997b-177">Set a default distribution</span></span>

<span data-ttu-id="5997b-178">La distribución de WSL predeterminada es la que se ejecuta cuando se ejecuta `wsl` en una línea de comandos.</span><span class="sxs-lookup"><span data-stu-id="5997b-178">The default WSL distribution is the one that runs when you run `wsl` on a command line.</span></span>

`wslconfig /setdefault <DistributionName>`

<span data-ttu-id="5997b-179">La distribución predeterminada se establece en `<DistributionName>`.</span><span class="sxs-lookup"><span data-stu-id="5997b-179">Sets the default distribution to `<DistributionName>`.</span></span>

**<span data-ttu-id="5997b-180">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5997b-180">Example:</span></span>**  
`wslconfig /setdefault Ubuntu` <span data-ttu-id="5997b-181">establecer la distribución de forma predeterminada en Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-181">would set my default distribution to Ubuntu.</span></span>  <span data-ttu-id="5997b-182">Ahora cuando ejecuto `wsl npm init` se ejecutará en Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-182">Now when I run `wsl npm init` it will run in Ubuntu.</span></span>  <span data-ttu-id="5997b-183">Si ejecuto `wsl` abrirá una sesión de Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="5997b-183">If I run `wsl` it will open an Ubuntu session.</span></span>

#### <a name="unregister-and-reinstall-a-distribution"></a><span data-ttu-id="5997b-184">Anular el registro y volver a instalar una distribución</span><span class="sxs-lookup"><span data-stu-id="5997b-184">Unregister and reinstall a distribution</span></span>

<span data-ttu-id="5997b-185">Mientras Linux distribuciones pueden instalarse a través de la Windows almacén, no se puede desinstalar a través de la tienda.</span><span class="sxs-lookup"><span data-stu-id="5997b-185">While Linux distributions can be installed through the Windows store, they can't be uninstalled through the store.</span></span>  <span data-ttu-id="5997b-186">WSL Config permite distribuciones se anula el registro o desinstalado.</span><span class="sxs-lookup"><span data-stu-id="5997b-186">WSL Config allows distributions to be unregistered/uninstalled.</span></span>

<span data-ttu-id="5997b-187">Al anular el registro también permite que las distribuciones deben volver a instalar.</span><span class="sxs-lookup"><span data-stu-id="5997b-187">Unregistering also allows distributions to be reinstalled.</span></span>

> <span data-ttu-id="5997b-188">**Precaución:** Una vez que se anula el registro, se perderán permanentemente todos los datos, configuraciones y asociadas con esa distribución de software.</span><span class="sxs-lookup"><span data-stu-id="5997b-188">**Caution:** Once unregistered, all data, settings, and software associated with that distribution will be permanently lost.</span></span>  <span data-ttu-id="5997b-189">Volver a instalar desde el almacén se instalará una copia limpia de la distribución.</span><span class="sxs-lookup"><span data-stu-id="5997b-189">Reinstalling from the store will install a clean copy of the distribution.</span></span>

`wslconfig /unregister <DistributionName>`  
<span data-ttu-id="5997b-190">Anula el registro de la distribución de WSL por lo que puede volver a instalar o limpiado.</span><span class="sxs-lookup"><span data-stu-id="5997b-190">Unregisters the distribution from WSL so it can be reinstalled or cleaned up.</span></span>

<span data-ttu-id="5997b-191">Por ejemplo: `wslconfig /unregister Ubuntu` quitarían Ubuntu desde las distribuciones disponibles en WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-191">For example: `wslconfig /unregister Ubuntu` would remove Ubuntu from the distributions available in WSL.</span></span>  <span data-ttu-id="5997b-192">Cuando ejecuto `wslconfig /list` no se mostrará.</span><span class="sxs-lookup"><span data-stu-id="5997b-192">When I run `wslconfig /list` it will not be listed.</span></span>

<span data-ttu-id="5997b-193">Para volver a instalar, busque la distribución en el Store de Windows y seleccione "Iniciar".</span><span class="sxs-lookup"><span data-stu-id="5997b-193">To reinstall, find the distribution in the Windows Store and select "Launch".</span></span>

## <a name="set-wsl-launch-settings"></a><span data-ttu-id="5997b-194">Establecer la configuración de inicio WSL</span><span class="sxs-lookup"><span data-stu-id="5997b-194">Set WSL launch settings</span></span>

> **<span data-ttu-id="5997b-195">Disponible en Windows Insider compilar 17093 y versiones posteriores</span><span class="sxs-lookup"><span data-stu-id="5997b-195">Available in Windows Insider Build 17093 and later</span></span>**

<span data-ttu-id="5997b-196">Configurar automáticamente cierta funcionalidad en WSL que se aplicarán cada vez que inicie el subsistema con `wsl.conf`.</span><span class="sxs-lookup"><span data-stu-id="5997b-196">Automatically configure certain functionality in WSL that will be applied every time you launch the subsystem using `wsl.conf`.</span></span> 

<span data-ttu-id="5997b-197">Derecha ahora, esto incluye las opciones de montaje automático y la configuración de red.</span><span class="sxs-lookup"><span data-stu-id="5997b-197">Right now, this includes automount options and network configuration.</span></span>

`wsl.conf` <span data-ttu-id="5997b-198">se encuentra en cada distribución de Linux en `/etc/wsl.conf`.</span><span class="sxs-lookup"><span data-stu-id="5997b-198">is located in each Linux distribution in `/etc/wsl.conf`.</span></span> <span data-ttu-id="5997b-199">Si el archivo no está allí, puede crearla usted.</span><span class="sxs-lookup"><span data-stu-id="5997b-199">If the file is not there, you can create it yourself.</span></span> <span data-ttu-id="5997b-200">WSL detectará la existencia del archivo y leerá su contenido.</span><span class="sxs-lookup"><span data-stu-id="5997b-200">WSL will detect the existence of the file and will read its contents.</span></span> <span data-ttu-id="5997b-201">Si el archivo falta o tiene un formato incorrecto (es decir, incorrecto marcado formato), continuará WSL iniciar con normalidad.</span><span class="sxs-lookup"><span data-stu-id="5997b-201">If the file is missing or malformed (that is, improper markup formatting), WSL will continue to launch as normal.</span></span>

<span data-ttu-id="5997b-202">Este es un ejemplo `wsl.conf` archivo puede agregar a sus distribuciones:</span><span class="sxs-lookup"><span data-stu-id="5997b-202">Here is a sample `wsl.conf` file you could add into your distros:</span></span>

```console
# Enable extra metadata options by default
[automount]
enabled = true
root = /windir/
options = "metadata,umask=22,fmask=11"
mountFsTab = false

# Enable DNS – even though these are turned on by default, we’ll specify here just to be explicit.
[network]
generateHosts = true
generateResolvConf = true
```

### <a name="configuration-options"></a><span data-ttu-id="5997b-203">Opciones de configuración</span><span class="sxs-lookup"><span data-stu-id="5997b-203">Configuration Options</span></span>

<span data-ttu-id="5997b-204">De acuerdo con las convenciones. ini, las claves se declaran en una sección.</span><span class="sxs-lookup"><span data-stu-id="5997b-204">In keeping with .ini conventions, keys are declared under a section.</span></span> 

<span data-ttu-id="5997b-205">WSL admite dos secciones: `automount` y `network`.</span><span class="sxs-lookup"><span data-stu-id="5997b-205">WSL supports two sections: `automount` and `network`.</span></span>

#### <a name="automount"></a><span data-ttu-id="5997b-206">Montaje automático</span><span class="sxs-lookup"><span data-stu-id="5997b-206">automount</span></span>

<span data-ttu-id="5997b-207">Sección:</span><span class="sxs-lookup"><span data-stu-id="5997b-207">Section:</span></span> `[automount]`


| <span data-ttu-id="5997b-208">key</span><span class="sxs-lookup"><span data-stu-id="5997b-208">key</span></span>        | <span data-ttu-id="5997b-209">value</span><span class="sxs-lookup"><span data-stu-id="5997b-209">value</span></span>                          | <span data-ttu-id="5997b-210">valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="5997b-210">default</span></span>      | <span data-ttu-id="5997b-211">Notas de la</span><span class="sxs-lookup"><span data-stu-id="5997b-211">notes</span></span>                                                                                                                                                                                                                                                                                                                          |
|:-----------|:-------------------------------|:-------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5997b-212">enabled</span><span class="sxs-lookup"><span data-stu-id="5997b-212">enabled</span></span>    | <span data-ttu-id="5997b-213">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-213">boolean</span></span>                        | <span data-ttu-id="5997b-214">true</span><span class="sxs-lookup"><span data-stu-id="5997b-214">true</span></span>         | `true` <span data-ttu-id="5997b-215">hace que se ha corregido las unidades (como)</span><span class="sxs-lookup"><span data-stu-id="5997b-215">causes fixed drives (i.e</span></span> `C:/` <span data-ttu-id="5997b-216">o `D:/`) que se monte automáticamente con DrvFs en `/mnt`.</span><span class="sxs-lookup"><span data-stu-id="5997b-216">or `D:/`) to be automatically mounted with DrvFs under `/mnt`.</span></span>  `false` <span data-ttu-id="5997b-217">significa que las unidades no se montan automáticamente, pero todavía puede montarlas manualmente o a través de `fstab`.</span><span class="sxs-lookup"><span data-stu-id="5997b-217">means drives won’t be mounted automatically, but you could still mount them manually or via `fstab`.</span></span>                                                                                                             |
| <span data-ttu-id="5997b-218">mountFsTab</span><span class="sxs-lookup"><span data-stu-id="5997b-218">mountFsTab</span></span> | <span data-ttu-id="5997b-219">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-219">boolean</span></span>                        | <span data-ttu-id="5997b-220">true</span><span class="sxs-lookup"><span data-stu-id="5997b-220">true</span></span>         | `true` <span data-ttu-id="5997b-221">establece `/etc/fstab` procesarse en el inicio de WSL.</span><span class="sxs-lookup"><span data-stu-id="5997b-221">sets `/etc/fstab` to be processed on WSL start.</span></span> <span data-ttu-id="5997b-222">/ etc/fstab es un archivo donde se pueden declarar otros sistemas de archivos, como un recurso compartido SMB.</span><span class="sxs-lookup"><span data-stu-id="5997b-222">/etc/fstab is a file where you can declare other filesystems, like an SMB share.</span></span> <span data-ttu-id="5997b-223">Por lo tanto, puede montar estos sistemas de archivos automáticamente en WSL inicio de la seguridad.</span><span class="sxs-lookup"><span data-stu-id="5997b-223">Thus, you can mount these filesystems automatically in WSL on start up.</span></span>                                                                                                                |
| <span data-ttu-id="5997b-224">root</span><span class="sxs-lookup"><span data-stu-id="5997b-224">root</span></span>       | <span data-ttu-id="5997b-225">Cadena</span><span class="sxs-lookup"><span data-stu-id="5997b-225">String</span></span>                         | `/mnt/`      | <span data-ttu-id="5997b-226">Establece el directorio de unidades de disco duro donde se monta automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5997b-226">Sets the directory where fixed drives will be automatically mounted.</span></span> <span data-ttu-id="5997b-227">Por ejemplo, si tiene un directorio en WSL en `/windir/` y especifique que como la raíz, esperaría ver las unidades de disco fijos montados en</span><span class="sxs-lookup"><span data-stu-id="5997b-227">For example, if you have a directory in WSL at `/windir/` and you specify that as the root, you would expect to see your fixed drives mounted at</span></span> `/windir/c`                                                                                              |
| <span data-ttu-id="5997b-228">opciones</span><span class="sxs-lookup"><span data-stu-id="5997b-228">options</span></span>    | <span data-ttu-id="5997b-229">lista separada por comas de valores</span><span class="sxs-lookup"><span data-stu-id="5997b-229">comma-separated list of values</span></span> | <span data-ttu-id="5997b-230">Cadena vacía</span><span class="sxs-lookup"><span data-stu-id="5997b-230">empty string</span></span> | <span data-ttu-id="5997b-231">Este valor se anexa a la cadena de opciones de montaje de DrvFs predeterminada.</span><span class="sxs-lookup"><span data-stu-id="5997b-231">This value is appended to the default DrvFs mount options string.</span></span> **<span data-ttu-id="5997b-232">Se pueden especificar solo las opciones de DrvFs específicas.</span><span class="sxs-lookup"><span data-stu-id="5997b-232">Only DrvFs-specific options can be specified.</span></span>** <span data-ttu-id="5997b-233">No se admiten las opciones que el montaje binario podría analizar normalmente en una marca.</span><span class="sxs-lookup"><span data-stu-id="5997b-233">Options that the mount binary would normally parse into a flag are not supported.</span></span> <span data-ttu-id="5997b-234">Si desea especificar explícitamente estas opciones, debe incluir cada unidad para el que desea hacerlo en/etc/fstab.</span><span class="sxs-lookup"><span data-stu-id="5997b-234">If you want to explicitly specify those options, you must include every drive for which you want to do so in /etc/fstab.</span></span> |

<span data-ttu-id="5997b-235">De forma predeterminada, WSL establece el uid y gid en el valor del usuario predeterminado (en la distribución de Ubuntu, se crea el usuario predeterminado con uid = 1000, gid = 1000).</span><span class="sxs-lookup"><span data-stu-id="5997b-235">By default, WSL sets the uid and gid to the value of the default user (in Ubuntu distro, the default user is created with uid=1000,gid=1000).</span></span> <span data-ttu-id="5997b-236">Si el usuario especifica una opción de gid o uid explícitamente a través de esta clave, se sobrescribirá el valor asociado.</span><span class="sxs-lookup"><span data-stu-id="5997b-236">If the user specifies a gid or uid option explicitly via this key, the associated value will be overwritten.</span></span> <span data-ttu-id="5997b-237">En caso contrario, el valor predeterminado siempre se anexará.</span><span class="sxs-lookup"><span data-stu-id="5997b-237">Otherwise, the default value will always be appended.</span></span>

<span data-ttu-id="5997b-238">**Nota:** Estas opciones se aplican como las opciones de montaje para todas las unidades montadas automáticamente.</span><span class="sxs-lookup"><span data-stu-id="5997b-238">**Note:** These options are applied as the mount options for all automatically mounted drives.</span></span> <span data-ttu-id="5997b-239">Para cambiar las opciones para solo una unidad específica, use/etc/fstab en su lugar.</span><span class="sxs-lookup"><span data-stu-id="5997b-239">To change the options for a specific drive only, use /etc/fstab instead.</span></span>

#### <a name="network"></a><span data-ttu-id="5997b-240">red</span><span class="sxs-lookup"><span data-stu-id="5997b-240">network</span></span>

<span data-ttu-id="5997b-241">Etiqueta de sección:</span><span class="sxs-lookup"><span data-stu-id="5997b-241">Section label:</span></span> `[network]`

| <span data-ttu-id="5997b-242">key</span><span class="sxs-lookup"><span data-stu-id="5997b-242">key</span></span> | <span data-ttu-id="5997b-243">value</span><span class="sxs-lookup"><span data-stu-id="5997b-243">value</span></span> | <span data-ttu-id="5997b-244">valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="5997b-244">default</span></span> | <span data-ttu-id="5997b-245">Notas de la</span><span class="sxs-lookup"><span data-stu-id="5997b-245">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="5997b-246">generateHosts</span><span class="sxs-lookup"><span data-stu-id="5997b-246">generateHosts</span></span> | <span data-ttu-id="5997b-247">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-247">boolean</span></span> | `true` | `true` <span data-ttu-id="5997b-248">establece WSL para generar `/etc/hosts`.</span><span class="sxs-lookup"><span data-stu-id="5997b-248">sets WSL to generate `/etc/hosts`.</span></span> <span data-ttu-id="5997b-249">El `hosts` archivo contiene un mapa estático de direcciones IP correspondientes de los nombres de host.</span><span class="sxs-lookup"><span data-stu-id="5997b-249">The `hosts` file contains a static map of hostnames corresponding IP address.</span></span> |
| <span data-ttu-id="5997b-250">generateResolvConf</span><span class="sxs-lookup"><span data-stu-id="5997b-250">generateResolvConf</span></span> | <span data-ttu-id="5997b-251">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-251">boolean</span></span> | `true` | `true` <span data-ttu-id="5997b-252">establecer WSL para generar `/etc/resolv.conf`.</span><span class="sxs-lookup"><span data-stu-id="5997b-252">set WSL to generate `/etc/resolv.conf`.</span></span> <span data-ttu-id="5997b-253">El `resolv.conf` contiene una lista DNS que son capaces de resolver un nombre de host especificado en su dirección IP.</span><span class="sxs-lookup"><span data-stu-id="5997b-253">The `resolv.conf` contains a DNS list that are capable of resolving a given hostname to its IP address.</span></span> | 

#### <a name="interop"></a><span data-ttu-id="5997b-254">Interoperabilidad</span><span class="sxs-lookup"><span data-stu-id="5997b-254">interop</span></span>

<span data-ttu-id="5997b-255">Etiqueta de sección:</span><span class="sxs-lookup"><span data-stu-id="5997b-255">Section label:</span></span> `[interop]`

<span data-ttu-id="5997b-256">Estas opciones están disponibles en Insider 17713 de compilación y versiones posteriores.</span><span class="sxs-lookup"><span data-stu-id="5997b-256">These options are available in Insider Build 17713 and later.</span></span>

| <span data-ttu-id="5997b-257">key</span><span class="sxs-lookup"><span data-stu-id="5997b-257">key</span></span> | <span data-ttu-id="5997b-258">value</span><span class="sxs-lookup"><span data-stu-id="5997b-258">value</span></span> | <span data-ttu-id="5997b-259">valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="5997b-259">default</span></span> | <span data-ttu-id="5997b-260">Notas de la</span><span class="sxs-lookup"><span data-stu-id="5997b-260">notes</span></span>|
|:----|:----|:----|:----|
| <span data-ttu-id="5997b-261">enabled</span><span class="sxs-lookup"><span data-stu-id="5997b-261">enabled</span></span> | <span data-ttu-id="5997b-262">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-262">boolean</span></span> | `true` | <span data-ttu-id="5997b-263">Al definir esta clave determinará si WSL admitirá al iniciar los procesos de Windows.</span><span class="sxs-lookup"><span data-stu-id="5997b-263">Setting this key will determine whether WSL will support launching Windows processes.</span></span> |
| <span data-ttu-id="5997b-264">appendWindowsPath</span><span class="sxs-lookup"><span data-stu-id="5997b-264">appendWindowsPath</span></span> | <span data-ttu-id="5997b-265">boolean</span><span class="sxs-lookup"><span data-stu-id="5997b-265">boolean</span></span> | `true` | <span data-ttu-id="5997b-266">Al definir esta clave determinará si WSL agregará elementos de la ruta de acceso de Windows a la variable de entorno $PATH.</span><span class="sxs-lookup"><span data-stu-id="5997b-266">Setting this key will determine whether WSL will add Windows path elements to the $PATH environment variable.</span></span> | 