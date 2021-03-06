---
title: Практическое руководство. Создание средства просмотра HTML-документов в приложении Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 1330e20cc4fe7df86e51bebca28e4a71e3108673
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530547"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Практическое руководство. Создание средства просмотра HTML-документов в приложении Windows Forms
Можно использовать <xref:System.Windows.Forms.WebBrowser> управления для отображения и печати HTML-документов с ограниченными возможностями обозревателя. Это полезно в том случае, если необходимо воспользоваться возможностями форматирования HTML, но запретить пользователям произвольным веб-страницам, которые могут содержать ненадежных веб-элементы управления или потенциально вредоносный код скрипта. Может потребоваться ограничить возможности <xref:System.Windows.Forms.WebBrowser> управления таким образом, например, для использования в качестве средства просмотра электронной почты HTML или предоставить справку формате HTML в приложении.  
  
### <a name="to-create-an-html-document-viewer"></a>Создание средства просмотра документа HTML  
  
1.  Задать <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> свойства `false` для предотвращения <xref:System.Windows.Forms.WebBrowser> управления открывать файлы, которые перетаскиваются на него.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Задать <xref:System.Windows.Forms.WebBrowser.Url%2A> свойства нужный исходный файл для отображения.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   элемент управления <xref:System.Windows.Forms.WebBrowser> с именем `webBrowser1`;  
  
-   ссылки на сборки `System` и `System.Windows.Forms`.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [Общие сведения об элементе управления WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [Безопасность элемента управления WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Практическое руководство. Переход по заданному URL-адресу с помощью элемента управления WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Практическое руководство. Печать с использованием элемента управления WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
