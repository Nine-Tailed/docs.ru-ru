---
title: Новые возможности .NET Core 2.1
description: Дополнительные сведения о новых возможностях .NET Core 2.1.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: 241ac0195e5edcd17ac67ea7ea0fac159af97414
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2018
ms.locfileid: "34826936"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="8f6d5-103">Новые возможности .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f6d5-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="8f6d5-104">В .NET Core 2.1 представлены следующие улучшения и новые возможности:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- <span data-ttu-id="8f6d5-105">[инструментарий](#tooling);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-105">[Tooling](#tooling)</span></span>
- <span data-ttu-id="8f6d5-106">[накат](#roll-forward);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-106">[Roll forward](#roll-forward)</span></span>
- [<span data-ttu-id="8f6d5-107">Развертывание</span><span class="sxs-lookup"><span data-stu-id="8f6d5-107">Deployment</span></span>](#deployment)
- <span data-ttu-id="8f6d5-108">[пакет обеспечения совместимости с Windows](#windows-compatibility-pack);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-108">[Windows Compatibility Pack](#windows-compatibility-pack)</span></span>
- <span data-ttu-id="8f6d5-109">[улучшения JIT-компиляции](#jit-compiler-improvements);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-109">[JIT compilation improvements](#jit-compiler-improvements)</span></span>
- <span data-ttu-id="8f6d5-110">[изменения API](#api-changes);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-110">[API changes](#api-changes)</span></span>

## <a name="tooling"></a><span data-ttu-id="8f6d5-111">Инструментарий</span><span class="sxs-lookup"><span data-stu-id="8f6d5-111">Tooling</span></span>

<span data-ttu-id="8f6d5-112">Пакет SDK .NET Core 2.1 (версия 2.1.300), который входит в комплектацию .NET Core 2.1, включает следующие изменения и усовершенствования.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="8f6d5-113">Повышение производительности сборки.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-113">Build performance improvements</span></span>

<span data-ttu-id="8f6d5-114">Основное внимание в .NET Core 2.1 уделено производительности сборки, что позволило сократить требуемое время, особенно для добавочной сборки.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="8f6d5-115">Эти улучшения производительности применяются к сборке, выполняемой из командной строки с помощью `dotnet build` или в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="8f6d5-116">Вот несколько из этих улучшений:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="8f6d5-117">при разрешении ресурсов в пакете разрешаются только те ресурсы, которые используются для сборки, а не все;</span><span class="sxs-lookup"><span data-stu-id="8f6d5-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="8f6d5-118">кэширование ссылок на сборки;</span><span class="sxs-lookup"><span data-stu-id="8f6d5-118">Caching of assembly references.</span></span>

- <span data-ttu-id="8f6d5-119">использование серверов сборки SDK длительного выполнения, которые не завершаются после каждого отдельного вызова `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="8f6d5-120">Это позволяет не применять JIT-компиляцию для больших блоков кода при каждом вызове `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="8f6d5-121">Процессы серверов сборки можно автоматически завершить с помощью следующей команды:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="8f6d5-122">Новые команды интерфейса командной строки</span><span class="sxs-lookup"><span data-stu-id="8f6d5-122">New CLI commands</span></span>

<span data-ttu-id="8f6d5-123">Ряд средств, которые ранее были доступны только для отдельных проектов с использованием [`DotnetCliToolReference`](../tools/extensibility.md), теперь стали частью пакета SDK для .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="8f6d5-124">К ним относятся следующие средства:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-124">These tools include:</span></span>

- <span data-ttu-id="8f6d5-125">`dotnet watch` предоставляет наблюдатель файловой системы, который ожидает изменений в файле и выполняет для него указанный набор команд.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="8f6d5-126">Например, следующая команда автоматически перестраивает текущий проект и выводит подробные результаты при любом изменении файла в проекте:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```
  
   <span data-ttu-id="8f6d5-127">Обратите внимание на параметр `--` перед параметром `--verbose`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="8f6d5-128">Он отделяет параметры, передаваемые непосредственно в команду `dotnet watch`, от аргументов для дочернего процесса `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="8f6d5-129">Без него параметр `--verbose` был бы применен к команде `dotnet watch`, а не к `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="8f6d5-130">Подробнее см. [Разработка приложений ASP.NET Core с использованием dotnet watch](/aspnet/core/tutorials/dotnet-watch);</span><span class="sxs-lookup"><span data-stu-id="8f6d5-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="8f6d5-131">`dotnet dev-certs` создает сертификаты, используемые при разработке в приложениях ASP.NET Core, и управляет ими;</span><span class="sxs-lookup"><span data-stu-id="8f6d5-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8f6d5-132">`dotnet user-secrets` управляет секретами в хранилище секретов пользователя в приложениях ASP.NET Core;</span><span class="sxs-lookup"><span data-stu-id="8f6d5-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="8f6d5-133">`dotnet sql-cache` создает в базе данных Microsoft SQL Server таблицу и индексы, которые будут использоваться для распределенного кэширования;</span><span class="sxs-lookup"><span data-stu-id="8f6d5-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="8f6d5-134">`dotnet ef` выполняет роль средства для управления базами данных, объектами <xref:Microsoft.EntityFrameworkCore.DbContext> и миграциями в приложениях Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="8f6d5-135">Дополнительные сведения см. в [описании программ командной строки для EF Core .NET](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="8f6d5-136">Глобальные инструменты</span><span class="sxs-lookup"><span data-stu-id="8f6d5-136">Global Tools</span></span>

<span data-ttu-id="8f6d5-137">.NET Core 2.1 поддерживает *глобальные инструменты*, то есть специальные средства, которые доступны глобально из командной строки.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="8f6d5-138">Модель расширяемости в предыдущих версиях .NET Core предоставляла пользовательские средства только отдельно для каждого проекта с использованием [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="8f6d5-139">Чтобы установить глобальные инструменты, выполните команду [dotnet tool install](..\tools\dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-139">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="8f6d5-140">Пример:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="8f6d5-141">Установленные инструменты можно запускать из командной строки, указав имя инструмента.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="8f6d5-142">См. дополнительные сведения о [глобальных инструментах .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="8f6d5-143">Управление инструментами с помощью команды `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="8f6d5-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="8f6d5-144">В пакете SDK для .NET Core 2.1 (2.1.300) все действия с инструментами выполняются с помощью команды `dotnet tool`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="8f6d5-145">Доступны следующие параметры.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-145">The following options are available:</span></span>

- <span data-ttu-id="8f6d5-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) устанавливает инструмент.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="8f6d5-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) удаляет и переустанавливает инструмент, то есть по сути обновляет его.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="8f6d5-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) выводит список установленных инструментов.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="8f6d5-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) удаляет все установленные инструменты.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="8f6d5-150">Накат</span><span class="sxs-lookup"><span data-stu-id="8f6d5-150">Roll forward</span></span>

<span data-ttu-id="8f6d5-151">Все приложения .NET Core, начиная с .NET Core версии 2.0, выполняют автоматический накат до последней *дополнительной версии*, установленной в системе.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> 

<span data-ttu-id="8f6d5-152">Начиная с .NET Core 2.0, если приложение было создано с помощью версии .NET Core, которая отсутствует во время выполнения, приложение автоматически выполняется в самой новой из установленных *дополнительных версий* .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="8f6d5-153">Другими словами, если приложение создано с помощью .NET 2.0 Core и выполняется в системе, где отсутствует .NET Core 2.0, но присутствует .NET Core 2.1, это приложение выполняется в .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8f6d5-154">Стратегия наката не применяется к предварительным версиям.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="8f6d5-155">Также она не применяется к основным выпускам.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="8f6d5-156">Например приложение .NET Core 1.0 не будет выполняться в .NET Core 2.0 или .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="8f6d5-157">Вы можете отключить накат до новой дополнительной версии любым из следующих трех способов.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="8f6d5-158">Установите для переменной среды `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` значение 0.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="8f6d5-159">Добавьте следующую строку в файл runtimeconfig.json:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="8f6d5-160">При использовании [средств интерфейса командной строки .NET Core](../tools/index.md) включите следующий параметр с помощью команды .NET Core `run`:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="8f6d5-161">Развертывание</span><span class="sxs-lookup"><span data-stu-id="8f6d5-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="8f6d5-162">Обслуживание автономного приложения</span><span class="sxs-lookup"><span data-stu-id="8f6d5-162">Self-contained application servicing</span></span>

<span data-ttu-id="8f6d5-163">Теперь `dotnet publish` публикует автономные приложения с обслуживаемой версией среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="8f6d5-164">При публикации автономного приложения с помощью пакета SDK для .NET Core 2.1 (версия 2.1.300) такое приложение использует самую последнюю обслуживаемую версию среды выполнения, известную этому пакету SDK.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="8f6d5-165">После обновления до последнего выпуска пакета SDK публикация выполняется с использованием последней версии среды выполнения .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="8f6d5-166">Это применимо для сред выполнения .NET Core 1.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="8f6d5-167">Автономная публикации зависит от версии среды выполнения в NuGet.org. Вам не нужно иметь обслуживаемую среду выполнения на локальном компьютере.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="8f6d5-168">Если используется пакет SDK 2.0 для .NET Core, автономные приложения публикуются с помощью среды выполнения .NET Core 2.0.0, если в свойстве `RuntimeFrameworkVersion` не указана другая версия.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="8f6d5-169">Такое поведение позволяет не устанавливать это свойство, когда нужно выбрать более позднюю версию среды выполнения для автономного приложения.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="8f6d5-170">Для перехода к новой версии проще всего опубликовать приложение с пакетом SDK для .NET Core 2.1 (версия 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="8f6d5-171">Пакет обеспечения совместимости с Windows</span><span class="sxs-lookup"><span data-stu-id="8f6d5-171">Windows Compatibility Pack</span></span>

<span data-ttu-id="8f6d5-172">При переносе существующего кода с платформы .NET Framework на .NET Core вы можете использовать [пакет обеспечения совместимости с Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="8f6d5-172">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="8f6d5-173">Он предоставляет доступ к 20 000 дополнительных интерфейсов API, которые не поддерживаются в .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-173">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="8f6d5-174">Сюда входят такие API-интерфейсы, как пространство имен <xref:System.Drawing?displayProperty="nameWithType">, класс <xref:System.Diagnostics.EventLog>, инструментарий WMI, счетчики производительности, службы Windows, типы и члены реестра Windows.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-174">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="8f6d5-175">Усовершенствования JIT-компилятора</span><span class="sxs-lookup"><span data-stu-id="8f6d5-175">JIT compiler improvements</span></span>

<span data-ttu-id="8f6d5-176">.NET Core теперь включает новую технологию JIT-компиляции, которая называется *многоуровневая компиляция* (или *адаптивная оптимизация*), что позволяет значительно повысить производительность.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-176">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="8f6d5-177">Многоуровневая компиляции включается пользователем.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-177">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="8f6d5-178">Одна из важных задач, которую выполняет JIT-компилятор, это оптимизация выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-178">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="8f6d5-179">Но для редко используемых путей кода компилятор может потратить на оптимизацию больше времени, чем потребуется на выполнение неоптимизированного кода.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-179">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="8f6d5-180">Многоуровневая компиляция разделяет JIT-компиляцию на два уровня.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-180">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="8f6d5-181">**Первый уровень** создает код настолько быстро, насколько это возможно.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-181">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="8f6d5-182">**Второй уровень** создает оптимизированный код для тех методов, которые выполняются часто.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-182">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="8f6d5-183">Второй уровень компиляции выполняется параллельно, чтобы повысить производительность.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-183">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="8f6d5-184">Вы можете включить многоуровневую компиляцию одним из двух способов.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-184">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="8f6d5-185">Чтобы использовать многоуровневую компиляцию во всех проектах, которые работают с пакетом SDK для 2.1 .NET Core, задайте следующую переменную среды:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-185">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="8f6d5-186">Чтобы использовать многоуровневую компиляцию отдельно для конкретных проектов, добавьте свойство `<TieredCompilation>` в раздел `<PropertyGroup>` файла проекта MSBuild, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-186">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="8f6d5-187">Изменения API</span><span class="sxs-lookup"><span data-stu-id="8f6d5-187">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="8f6d5-188">`Span<T>` и `Memory<T>`.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-188">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="8f6d5-189">.NET Core 2.1 включает несколько новых типов, которые значительно повышают эффективность работы с массивами и другими типами памяти.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-189">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="8f6d5-190">Новые типы включают:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-190">The new types include:</span></span>

- <span data-ttu-id="8f6d5-191"><xref:System.Span%601?displayProperty=nameWithType> и <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-191"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="8f6d5-192"><xref:System.Memory%601?displayProperty=nameWithType> и <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-192"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8f6d5-193">Без этих типов при передаче таких элементов в составе массива или в сегменте буфера памяти необходимо создавать копию данных перед их передачей в метод.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-193">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="8f6d5-194">Эти типы обеспечивают виртуальное представление данных, что позволяет не выделять дополнительную память и не выполнять дополнительные операции копирования.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-194">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="8f6d5-195">В следующем примере экземпляр <xref:System.Span%601> используется для создания виртуального представления 10 элементов массива.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-195">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="8f6d5-196">Сжатие Brotli</span><span class="sxs-lookup"><span data-stu-id="8f6d5-196">Brotli compression</span></span>

<span data-ttu-id="8f6d5-197">В .NET Core 2.1 добавлена поддержка сжатия и распаковки Brotli.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-197">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="8f6d5-198">Brotli — это универсальный алгоритм сжатия данных без потерь, который определен в [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) и поддерживается большинством веб-браузеров и всеми основными веб-серверами.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-198">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="8f6d5-199">Вы можете использовать потоковый класс <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> или высокопроизводительные классы <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> и <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> на основе диапазонов.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-199">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="8f6d5-200">Следующий пример демонстрирует сжатие с применением класса <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-200">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="8f6d5-201"><xref:System.IO.Compression.BrotliStream> действует так же, как <xref:System.IO.Compression.DeflateStream> и <xref:System.IO.Compression.GZipStream>, что позволяет легко преобразовать в <xref:System.IO.Compression.BrotliStream> код, вызывающий эти API-интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-201">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="8f6d5-202">Новые улучшения и API криптографии</span><span class="sxs-lookup"><span data-stu-id="8f6d5-202">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="8f6d5-203">.NET Core 2.1 включает многочисленные улучшения API криптографии:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-203">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="8f6d5-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> доступно в пакете System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-204"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="8f6d5-205">Реализация здесь такая же, как и в классе <xref:System.Security.Cryptography.Pkcs.SignedCms> для .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-205">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="8f6d5-206">Новые перегрузки методов <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> и <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> принимают идентификатор хэш-алгоритма, чтобы вызывающие методы могли получать значения отпечатка сертификата с алгоритмами, отличными от SHA-1.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-206">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="8f6d5-207">Доступен новый API криптографии на основе <xref:System.Span%601>, который поддерживает хэширование, HMAC, криптографический генератор случайных чисел, генератор асимметричной подписи, обработку асимметричной подписи и шифрование RSA.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-207">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="8f6d5-208">Производительность <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> улучшена примерно на 15 % благодаря реализации на основе <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-208">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="8f6d5-209">Новый класс <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> включает два новых метода:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-209">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="8f6d5-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> выполняется в течение строго фиксированного промежутка времени для любых входных параметров одинаковой длины, что очень удобно для использования в криптографической проверке без добавления информации о времени работы стороннего канала.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-210"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="8f6d5-211">Процедура <xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> выполняет очистку памяти и не может быть оптимизирована.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-211"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="8f6d5-212">Статический метод <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> заполняет <xref:System.Span%601> случайными значениями.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-212">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="8f6d5-213">Теперь <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> поддерживается в maxOS и Linux.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-213">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="8f6d5-214">Эллиптические кривые Диффи—Хелмана (ECDH) теперь доступны в семействе классов <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-214">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="8f6d5-215">Контактная зона сохраняется такой же, как в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-215">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="8f6d5-216">Экземпляр, возвращаемый <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>, умеет шифровать и расшифровывать данные с помощью OAEP и хэш-кода SHA-2, а также создавать и проверять подписи с помощью RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-216">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="8f6d5-217">Улучшения для сокетов</span><span class="sxs-lookup"><span data-stu-id="8f6d5-217">Sockets improvements</span></span>

<span data-ttu-id="8f6d5-218">.NET Core включает новый тип <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> и переработанный <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, которые создают основу для сетевых API-интерфейсов более высокого уровня.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-218">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="8f6d5-219">Например, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> является основой для реализации <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-219"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8f6d5-220">В предыдущих версиях .NET Core API-интерфейсы более высокого уровня основывались на собственных реализациях сетевых служб.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-220">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="8f6d5-221">Реализация сокетов, добавленная в .NET Core 2.1 имеет ряд преимуществ:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-221">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="8f6d5-222">Значительное улучшение производительности по сравнению с предыдущей реализацией.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-222">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="8f6d5-223">Устранение зависимостей платформы, что упрощает развертывание и обслуживание.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-223">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="8f6d5-224">Согласованное поведение на всех платформах .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-224">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="8f6d5-225"><xref:System.Net.Http.SocketsHttpHandler> является реализацией по умолчанию в .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-225"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="8f6d5-226">Но вы можете настроить в приложении использование более старой версии класса <xref:System.Net.Http.HttpClientHandler>, вызвав метод <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType">:</span><span class="sxs-lookup"><span data-stu-id="8f6d5-226">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", False)
```

<span data-ttu-id="8f6d5-227">Можно также использовать переменную среды, чтобы отказаться от использования реализации сокетов на основе <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-227">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="8f6d5-228">Для этого задайте для свойства `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` значение `false` или 0.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-228">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="8f6d5-229">В Windows можно использовать также <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, чтобы использовать собственную реализацию, или класс <xref:System.Net.Http.SocketsHttpHandler>, передав экземпляр этого класса в конструктор <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-229">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="8f6d5-230">В macOS и Linux вы можете настроить <xref:System.Net.Http.HttpClient> только отдельно для каждого процесса.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-230">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="8f6d5-231">В Linux необходимо развернуть [libcurl](https://curl.haxx.se/libcurl/), если вы хотите использовать старую реализацию <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="8f6d5-231">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="8f6d5-232">(Она устанавливается вместе с .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="8f6d5-232">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="8f6d5-233">См. также</span><span class="sxs-lookup"><span data-stu-id="8f6d5-233">See also</span></span>

[<span data-ttu-id="8f6d5-234">Новые возможности .NET Core</span><span class="sxs-lookup"><span data-stu-id="8f6d5-234">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="8f6d5-235">Новые возможности в EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f6d5-235">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="8f6d5-236">Новые возможности ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="8f6d5-236">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)