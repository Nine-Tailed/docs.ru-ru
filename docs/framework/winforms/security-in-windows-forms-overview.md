---
title: Общие сведения о безопасности в Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- code access security [Windows Forms], Windows Forms
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms], about security
- access control [Windows Forms], Windows Forms
ms.assetid: 4810dc9f-ea23-4ce1-8ea1-657f0ff1d820
ms.openlocfilehash: 36d38756f7df88ec04aca781525f0f6b0a48b768
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2018
ms.locfileid: "48839135"
---
# <a name="security-in-windows-forms-overview"></a>Общие сведения о безопасности в Windows Forms
До выпуска [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] весь код, выполняемый на компьютере пользователя, имел те же права и разрешения на доступ к ресурсам, которыми обладал пользователь компьютера. Например, если пользователю был разрешен доступ к файловой системе, то код также получал доступ к файловой системе Если пользователю был разрешен доступ к базе данных, то и коду предоставлялся доступ к ней. Наличие таких прав или разрешений может быть допустимо для кода в исполняемых файлах, которые пользователь собственноручно установил на локальном компьютере, но оно неприемлемо в тех случаях, когда речь идет о потенциально вредоносном коде, поступившем из Интернета или локальной интрасети. Такой код не должен получать доступ к ресурсам компьютера пользователя без его разрешения.  
  
 В [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] появилась инфраструктура, которая называется управлением доступом для кода. Она позволяет разграничивать права и разрешения, которыми обладает пользователь и код. По умолчанию код, поступающий из Интернета или интрасети, может выполняться только в режиме частичного доверия. В режиме частичного доверия приложение подвергается ряду ограничений: помимо всего прочего, приложению отказано в доступе к локальным жестким дискам, и оно не может запускать неуправляемый код. Платформа [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] управляет ресурсами, к которым код может получить доступ, на основе идентификатора этого кода: его происхождения, имеет ли он [сборки со строгими именами](../../../docs/framework/app-domains/strong-named-assemblies.md), подписан ли он с помощью сертификата и т. д.  
  
 Технология [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], используемая для развертывания приложений Windows Forms, облегчает разработку приложений, которые запускаются с частичным доверием, с полным доверием или с частичным доверием и повышенным уровнем разрешений. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] предоставляет такие функции, как повышение уровня разрешений и развертывание доверенного приложения, чтобы приложение могло подобающим образом запрашивать полное доверие или повышенный уровень разрешений у локального пользователя.  
  
## <a name="understanding-security-in-the-net-framework"></a>Общее представление о безопасности в .NET Framework  
 Управление доступом для кода позволяет считать код надежным в той или иной степени в зависимости от происхождения кода и других аспектов его удостоверения. Подробнее о данных, на основании которых среда CLR определяет политику безопасности, см. в разделе [Свидетельство](https://msdn.microsoft.com/library/64ceb7c8-a0b4-46c4-97dc-6c22da0539da). Это помогает защитить компьютеры от вредоносного кода, а доверенный код — от умышленного или случайного нарушения безопасности. Управление доступом для кода также позволяет лучше контролировать действия, которые может выполнять приложение, так как вы можете указать только те разрешения, которые необходимы для работы приложения. Управление доступом для кода влияет на весь управляемый код, который предназначен для среды CLR, даже если этот код не производит ни одной проверки разрешений, предоставленных посредством управления доступом для кода. Подробнее о безопасности в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] см. в разделах [Основные понятия безопасности](../../../docs/standard/security/key-security-concepts.md) и [Основы управления доступом для кода](../../../docs/framework/misc/code-access-security-basics.md).  
  
 Если пользователь запускает исполняемый файл Windows Forms непосредственно с веб-сервера или из общей папки, то степень доверия, предоставляемая приложению, зависит от того, где размещается код и как он запущен. При запуске приложения происходит его автоматическая оценка, после которой приложение получает именованный набор разрешений от среды CLR. По умолчанию код на локальном компьютере получает набор разрешений полного доверия, код из локальной сети — набор разрешений локальной интрасети, а код из Интернета — набор разрешений Интернета.  
  
> [!NOTE]
>  В [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] версии 1.0 с пакетами обновления 1 (SP1) и 2 (SP2) код из Интернета получает набор разрешений Nothing. Во всех остальных выпусках [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] код из Интернета получает набор разрешений Интернета.  
>   
>  Разрешения по умолчанию, которые содержатся в этих наборах, приведены в разделе [Политика безопасности по умолчанию](https://msdn.microsoft.com/library/2c086873-0894-4f4d-8f7e-47427c1a3b55). В зависимости от разрешений, которые получает приложение, оно выполняется правильно либо вызывает исключение безопасности.  
>   
>  Многие приложения Windows Forms развертываются с помощью [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]. Уровни безопасности по умолчанию средств, используемых для реализации развертывания [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)], отличаются от тех, которые обсуждались ранее. Подробнее см. далее в этом разделе.  
  
 Разрешения, предоставленные приложению, могут отличаться от разрешений по умолчанию, потому что политика безопасности может быть изменена. Это означает, что приложение может иметь некоторые разрешения на одном компьютере, но не иметь их на другом.  
  
## <a name="developing-a-more-secure-windows-forms-application"></a>Разработка более безопасных приложений Windows Forms  
 Безопасность важна на всех этапах разработки приложения. Начните с анализа и выполнения [правил написания безопасного кода](../../../docs/standard/security/secure-coding-guidelines.md).  
  
 Далее необходимо решить, будет ли приложение выполняться в режиме полного или частичного доверия. Выполнение приложения в режиме полного доверия облегчает доступ к ресурсам на локальном компьютере, но подвергает приложение и его пользователей высокому риску нарушения безопасности, если приложение проектировалось и разрабатывалось без строгого соблюдения правил написания безопасного кода. Выполнение приложения в режиме частичного доверия облегчает разработку более безопасных приложений и сокращает риски, но требует более тщательного планирования реализации некоторых возможностей.  
  
 Если используется частичное доверие (т. е. наборы разрешений "Интернет" или "Локальная интрасеть"), определите, как должно вести себя приложение в этой среде. Windows Forms предоставляет более безопасные альтернативные способы реализации возможностей приложения в среде с частичным доверием. Определенные части приложения, например отвечающие за доступ к данным, могут быть разработаны и написаны по-разному для среды с частичным доверием и среды с полным доверием. Некоторые возможности Windows Forms, такие как параметры приложения, предназначены для работы в среде с частичным доверием. Подробнее см. в разделе [Общие сведения о параметрах приложений](../../../docs/framework/winforms/advanced/application-settings-overview.md).  
  
 Если приложению требуется больше разрешений, чем позволяет среда с частичным доверием, однако предоставлять ему разрешения полного доверия нежелательно, можно работать в режиме частичного доверия, запросив только необходимые дополнительные разрешения. Например, если требуется работать в режиме частичного доверия, но необходимо предоставить приложению доступ только для чтения к каталогу в файловой системе пользователя, можно запросить разрешение <xref:System.Security.Permissions.FileIOPermission> только для этого каталога. При правильном применении этот подход может расширять функциональные возможности приложения и снижать угрозу безопасности для пользователей.  
  
 При разработке приложения, которое будет выполняться в среде с частичным доверием, отслеживайте, какие разрешения обязательны для его работы и какие могут использоваться им дополнительно. Когда известны все разрешения, необходимо подать декларативный запрос на разрешения на уровне приложения. Запрос разрешений уведомляет среду времени выполнения [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] о необходимых разрешениях и тех разрешениях, предоставлять которые не требуется. Дополнительные сведения о запросе разрешений см. в разделе [Запрос разрешений](https://msdn.microsoft.com/library/0447c49d-8cba-45e4-862c-ff0b59bebdc2).  
  
 При запросе необязательных разрешений необходимо обработать исключения безопасности, которые могут возникнуть, если приложение выполнит действие, требующее разрешений, которые не были предоставлены. Корректная обработка исключения <xref:System.Security.SecurityException> гарантирует, что приложение будет продолжать работать. Приложение может использовать исключения для определения того, следует ли отключить ту или иную возможность для пользователя. Например, приложение может отключить команду меню **Сохранить**, если не предоставлено соответствующее разрешение.  
  
 Иногда трудно определить, запрошены ли все необходимые разрешения. Например, вызов метода, который на первый взгляд выглядит вполне безобидно, может во время выполнения в какой-то момент обращаться к файловой системе. Если не выполнить развертывание приложения со всеми требуемыми разрешениями, оно может работать корректно при отладке, но отказать при развертывании. Оба [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK и Visual Studio 2005 имеются средства для определения разрешений, необходимых приложению: MT.exe командной строки и функция вычисления разрешений Visual Studio, соответственно.  
  
 Дополнительные функции обеспечения безопасности Windows Forms описаны в представленных ниже разделах.  
  
|Раздел|Описание:|  
|-----------|-----------------|  
|-   [Более безопасный доступ к файлам и данным в Windows Forms](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)|Описание доступа к файлам и данным в среде с частичным доверием.|  
|-   [Более безопасная печать в Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)|Описание доступа к возможностям печати в среде с частичным доверием.|  
|-   [Дополнительные вопросы безопасности в формах Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)|Описание способов работы с окнами с помощью буфера обмена и вызова неуправляемого кода в среде с частичным доверием.|  
  
-  
  
### <a name="deploying-an-application-with-the-appropriate-permissions"></a>Развертывание приложения с соответствующими разрешениями  
 Чаще всего приложение Windows Forms развертывается на клиентском компьютере с использованием [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] — технологии развертывания, которая описывает все компоненты, необходимые для запуска приложения. В [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] для описания сборок и файлов, входящих в состав приложения, а также требуемых ему разрешений используются XML-файлы, называемые манифестами.  
  
 В состав [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] входят две технологии запроса повышенного уровня разрешений на клиентском компьютере. Обе технологии основаны на использовании сертификатов Authenticode. Сертификаты предоставляют пользователям некоторые гарантии того, что приложение поступило из надежного источника.  
  
 Эти технологии описаны в приведенной ниже таблице.  
  
|Технология повышения уровня разрешений|Описание|  
|------------------------------------|-----------------|  
|Повышение уровня разрешений|Запрашивает пользователя с помощью диалогового окна безопасности при первом запуске приложения. Диалоговое окно **Повышение разрешений** информирует пользователя об издателе приложения, чтобы пользователь мог принять обоснованное решение в отношении того, следует ли предоставлять приложению дополнительное доверие.|  
|Развертывание надежных приложений|Предусматривает однократную установку сертификата Authenticode издателя на клиентском компьютере, выполняемую системным администратором. С этого момента любые приложения, подписанные этим сертификатом, будут рассматриваться как надежные, и их можно будет запускать с полным доверием на локальном компьютере без дополнительных запросов.|  
  
 Выбор технологии зависит от среды развертывания. Подробнее см. в разделе [Выбор стратегии развертывания ClickOnce](/visualstudio/deployment/choosing-a-clickonce-deployment-strategy).  
  
 По умолчанию [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] приложений, развернутых с помощью Visual Studio или [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] средств SDK (Mage.exe и MageUI.exe), настроенных для запуска на клиентском компьютере с полным доверием. При развертывании приложения с помощью частичного доверия или с помощью только некоторых дополнительных разрешений необходимо изменить эту настройку по умолчанию. Это можно сделать с помощью Visual Studio или [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)] SDK средства MageUI.exe при настройке развертывания. Подробнее об использовании средства MageUI.exe см. в разделе "Пошаговое руководство. Развертывание приложения ClickOnce из командной строки".  См. также разделы [Практическое руководство. Установка пользовательских разрешений для приложения ClickOnce](https://msdn.microsoft.com/library/hafybdaa\(v=vs.110\)) или [Практическое руководство. Установка пользовательских разрешений для приложения ClickOnce](https://msdn.microsoft.com/library/hafybdaa\(v=vs.120\)).  
  
 Подробнее об аспектах безопасности [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] и повышении уровня разрешений см. в разделе [Развертывание и защита приложений ClickOnce](/visualstudio/deployment/securing-clickonce-applications). Подробнее о развертывании доверенных приложений см. в разделе [Общие сведения о развертывании доверенных приложений](/visualstudio/deployment/trusted-application-deployment-overview).  
  
### <a name="testing-the-application"></a>Тестирование приложения  
 Если вы развернули приложение Windows Forms с помощью Visual Studio, вы можете включить отладку в режиме частичного доверия или с ограниченным набором разрешений из среды разработки.  См. также разделы [Практическое руководство. Отладка приложения ClickOnce с ограниченными разрешениями](https://msdn.microsoft.com/library/593zkfdf\(v=vs.110\)) или [Практическое руководство. Отладка приложения ClickOnce с ограниченными разрешениями](https://msdn.microsoft.com/library/593zkfdf\(v=vs.120\)).  
  
## <a name="see-also"></a>См. также  
 [Безопасность Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Основы управления доступом для кода](../../../docs/framework/misc/code-access-security-basics.md)  
 [Развертывание и безопасность технологии ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Общие сведения о развертывании доверенных приложений](/visualstudio/deployment/trusted-application-deployment-overview)  
 [Mage.exe (средство создания и редактирования манифеста)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (средство создания и редактирования манифестов, графический клиент)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
