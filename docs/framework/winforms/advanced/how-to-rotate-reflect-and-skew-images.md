---
title: Практическое руководство. Поворот, отражение и наклон изображений
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], reflecting
- images [Windows Forms], rotating
- images [Windows Forms], skewing
ms.assetid: a3bf97eb-63ed-425a-ba07-dcc65efb567c
ms.openlocfilehash: 7f580b4d3016f1ecedc33302fe57caeec5698aeb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523459"
---
# <a name="how-to-rotate-reflect-and-skew-images"></a>Практическое руководство. Поворот, отражение и наклон изображений
Поворот, отражать и наклонять изображения путем указания точек назначения для верхнего левого, правого верхнего и левого нижнего углов исходного изображения. Эти три точки назначения определяют аффинное преобразование, которое сопоставляет исходное прямоугольное изображение в параллелограмм.  
  
## <a name="example"></a>Пример  
 Предположим, что исходное изображение представляет собой прямоугольник с левого верхнего угла в (0, 0), правого верхнего угла в (100, 0) и левого нижнего угла на (0, 50). Теперь допустим, эти три точки в конечные точки следующим образом.  
  
|Исходная точка|Конечная точка|  
|--------------------|-----------------------|  
|Верхний левый угол (0, 0)|(200, 20)|  
|Правый верхний угол (100, 0)|(110, 100)|  
|Нижний левый угол (0, 50)|(250, 30)|  
  
 Ниже показан исходный образ и образ в параллелограмм. Исходный образ была синхронизована, отражаются, поворачивать и преобразовать. На строку, проходящую через сопоставлен горизонтальной оси вдоль верхнего края исходного изображения (200, 20) и (110, 100). Ось y — вдоль левого края исходного изображения сопоставляется строку, проходящую через (200, 20) и (250, 30).  
  
 ![Полосы](../../../../docs/framework/winforms/advanced/media/stripes1.gif "Stripes1")  
  
 Аналогичные преобразования, примененного к фотографии на следующем рисунке.  
  
 ![Преобразовать Climber](../../../../docs/framework/winforms/advanced/media/transformedclimber.png "TransformedClimber")  
  
 На следующем рисунке аналогичные преобразования, примененного в метафайл.  
  
 ![Преобразовать метафайл](../../../../docs/framework/winforms/advanced/media/transformedmetafile.png "TransformedMetafile")  
  
 В следующем примере создается изображения, показанные на первом рисунке.  
  
 [!code-csharp[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.WorkingWithImages#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Предыдущий пример предназначен для работы с Windows Forms, и для него необходим <xref:System.Windows.Forms.PaintEventArgs> `e`, который является параметром <xref:System.Windows.Forms.Control.Paint> обработчика событий. Обязательно замените `Stripes.bmp` с путем к изображение, которое находится в вашей системе.  
  
## <a name="see-also"></a>См. также  
 [Работа с растровыми и векторными изображениями, значками и метафайлами](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
