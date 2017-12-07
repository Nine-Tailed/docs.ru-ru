---
title: "С помощью Azure Service Fabric"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | С помощью Azure Service Fabric"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a>С помощью Azure Service Fabric

Azure Service Fabric возникших от корпорации Майкрософт переход с доставкой поле программных продуктов, которые были обычно монолитные в стиле, предоставление услуг. Процесс построения и эксплуатации больших служб в масштабе, например базы данных SQL Azure, Azure Cosmos DB, Azure Service Bus или серверной Cortana в форму Service Fabric. Платформа развиваются как больше служб, что существует его. Главное Service Fabric приходилось выполнять не только в Azure, но также в изолированных развертываниях Windows Server.

Для решения сложных проблем построения и запуска службы и эффективно, используя ресурсы инфраструктуры, чтобы команды можно решать бизнес-задачи, используя подход микрослужбами является целью Service Fabric.

Service Fabric предоставляет два областям для построения приложения, использующие подход микрослужбами:

-   Платформа, которая предоставляет системные службы для развертывания, масштабирования, обновления, обнаружения и перезапустите службы не удалось, обнаружить расположение службы, управления состоянием и отслеживать работоспособность. Эти службы системы фактически позволяют многие характеристики микрослужбами было описано выше.

-   Программные API или платформы, для построения приложений, как микрослужбами: [службы reliable actor и надежные службы](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Конечно можно выбрать любой код для создания вашего микрослужбу, но эти API-интерфейсы делают более простой и их интеграцию с платформой на более глубоком уровне. Таким образом, можно получить работоспособности и сведения диагностики или вы сможете использовать управление состоянием надежный.

Service Fabric не зависит от относительно способа создания службы, и можно использовать любую технологию. Тем не менее он предоставляет встроенные API-интерфейсы программирования, чтобы упростить создание микрослужбами.

Как показано на рисунке 4-26, можно создать и запустить микрослужбами в Service Fabric в виде простых процессов или как контейнеры Docker. Можно также смешивать микрослужбами основе контейнера с микрослужбами на основе процесса внутри одного кластера Service Fabric.

![](./media/image30.png)

**Рис. 4-26**. Развертывание микрослужбами как процессы или контейнеры в Azure Service Fabric

Структуры службы кластеров на основе на узлах Linux и Windows можно запускать контейнеры Docker Linux и Windows, соответственно.

Самые последние сведения о поддержке контейнеры в Azure Service Fabric. в разделе [Service Fabric и контейнеры](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric представляет собой хороший пример платформы, где можно определить другой логической архитектуры (business микрослужбами или ограниченного контексты) чем физическую реализацию, появившихся в [логической архитектуры и физического Архитектура](#logical-architecture-versus-physical-architecture) раздела. Например, если вы реализуете [надежных служб с отслеживанием состояния](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) в [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), которого представлены в разделе [Stateless сравнение с отслеживанием состояния микрослужбами](#stateless-versus-stateful-microservices) более поздней версии может иметь бизнес-концепция микрослужбу, с несколькими физический службами.

Как показано на рис. 4-27 и решения с точки зрения логического или business микрослужбу, при реализации службы с отслеживанием состояния надежные службы структуры обычно необходимо реализовать два уровня служб. Первый — в серверной части с отслеживанием состояния надежного службу, которая обрабатывает несколько секций (каждая секция имеет службы с отслеживанием состояния). Второе — внешняя служба или служба шлюза, ответственный за маршрутизацию и данных статистической обработки нескольких секций или экземпляры службы с отслеживанием состояния. Службы шлюза также обрабатывает клиентские взаимодействие с циклами повторных попыток доступа к внутренней службы.
При реализации пользовательской службы или alternatevely, можно также использовать Service Fabric out of box вызывается служба шлюза [обратного прокси-службы](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**На рисунке 4-27**. Микрослужбу бизнеса с несколько экземпляров службы с отслеживанием состояния и пользовательского интерфейса шлюза

В любом случае при использовании надежного служб Service Fabric с отслеживанием состояния, также имеется логического или бизнес-микрослужбу (ограниченная контекст), обычно состоит из нескольких физических служб. Каждой их, служба шлюза и разделов службы может быть реализован как службы веб-API ASP.NET, как показано на рисунке 4-26.

В Service Fabric можно группировать и развертывание групп служб, как [приложение Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), который представляет собой единицу упаковки и развертывания для orchestrator или кластера. Таким образом приложение Service Fabric может быть сопоставлен этот самостоятельных и микрослужбу логических границ или ограниченного контекста, а также так, чтобы эти службы можно развернуть автономно.

## <a name="service-fabric-and-containers"></a>Service Fabric и контейнеров

По отношению к контейнерам в Service Fabric также можно развернуть службы в образы контейнеров в пределах кластера Service Fabric. Как показано на рисунке 4-28, большую часть времени будет существовать только один контейнер каждой службы.

![](./media/image32.png)

**Рис. 4-28**. Микрослужбу бизнеса с несколькими службами (контейнеров) в Service Fabric

Тем не менее так называемые «сопроводительные» контейнеры (двух контейнеров, которые должны быть развернуты вместе как часть службы логических) также возможны в Service Fabric. Самое важное является микрослужбу бизнеса логических границ вокруг несколько целостного элементов. Во многих случаях может быть одной службы с одной модели данных, но в некоторых других случаях может потребоваться физического несколько служб.

Начиная с mid 2017 г в Service Fabric невозможно развернуть SF надежных служб с отслеживанием состояния в контейнерах, можно развернуть только без сохранения состояния службы и службы субъекта в контейнерах. Но Обратите внимание, что вы можете сочетать в процессах и службы в контейнеры, в то же приложение Service Fabric как показано на рисунке 4-29.

![](./media/image33.png)

**На рисунке 4-29**. Business микрослужбу сопоставлен с контейнерами и служб с отслеживанием состояния приложения Service Fabric

Дополнительные сведения о поддержке контейнера в Azure Service Fabric см. в разделе [Service Fabric и контейнеры](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Без учета состояния, сравнение с отслеживанием состояния микрослужбами

Как упоминалось ранее, его модели домена (данные и логику) должен быть владельцем каждого микрослужбу (логического ограниченного контекста). В случае без сохранения состояния микрослужбами базы данных будут внешних применением реляционных вариантах, например SQL Server или NoSQL вариантах, например MongoDB или Cosmos Azure DB.

Однако сами службы может быть с отслеживанием состояния в Service Fabric, это означает, что данные находятся в пределах микрослужбу. Эти данные могут существовать не только на том же сервере, но внутри процесса микрослужбу в памяти и сохраняется на жестких дисках реплицируются на другие узлы. На рисунке 4-30 показаны различные подходы.

![](./media/image34.png)

**На рисунке 4-30**. Без учета состояния, сравнение с отслеживанием состояния микрослужбами

Подход без сохранения состояния правильный и проще в реализации, чем микрослужбами с отслеживанием состояния, поскольку подход аналогичен традиционных и хорошо известных шаблонов. Но без сохранения состояния микрослужбами наложить задержки между процесса и источников данных. Они также требуют более перемещения фрагментов, при попытке повысить производительность с помощью дополнительных кэша и очередей. Получается, что можно столкнуться с сложные архитектуры, имеющих слишком много уровней.

Напротив [с отслеживанием состояния микрослужбами](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) можно excel в сложных сценариях, так как нет задержка между доменную логику и данные. Обработка большого объема данных, игры обратно завершает, базы данных в качестве службы, и все другие сценарии низкой задержкой выиграть от служб с отслеживанием состояния, которые позволяют локального состояния для более быстрого доступа.

Службы без отслеживания состояния и с отслеживанием состояния дополняют друг друга. Для экземпляра вы увидите в на рисунке 4 — 30 на схеме справа, службы с отслеживанием состояния можно разбить на несколько секций. Чтобы открыть эти разделы, может потребоваться службы без отслеживания состояния, выступающего в качестве службы шлюза, который знает, как для решения каждой секции на основе ключей секционирования.

Службы с отслеживанием состояния имеют недостатки. Уровень сложности, который позволяет масштабировать ресурсов. Функции, которые обычно будут реализованы в системах внешней базы данных должны учитываться для задач, таких как репликация данных между с отслеживанием состояния микрослужбами и секционирования данных. Тем не менее, это одна из областей, где orchestrator, например [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) с его [надежных служб с отслеживанием состояния](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) помогут наиболее — за счет упрощения разработки и жизненного цикла с отслеживанием состояния с помощью микрослужбами [надежные API служб](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) и [службы Reliable Actor](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Другие платформы микрослужбу, позволяющие с отслеживанием состояния службы, которые поддерживают шаблон субъекта, и который повышает отказоустойчивость и задержка между бизнес-логику и данные являются Microsoft [Орлеане](https://github.com/dotnet/orleans)из Microsoft Research и [ Akka.NET](http://getakka.net/). Обе платформы в настоящее время, повысить их поддержку Docker.

Обратите внимание, что контейнеры Docker сами без сохранения состояния. Если требуется для реализации службы с отслеживанием состояния, требуется одна из дополнительных платформ предписания и более высокого уровня, записанные ранее. 

>[!div class="step-by-step"]
[Предыдущие] (scalable-available-multi-container-microservice-applications.md) [Далее] (.. /docker-Application-Development-Process/index.MD)