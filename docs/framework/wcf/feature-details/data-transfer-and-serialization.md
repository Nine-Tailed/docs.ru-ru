---
title: Передача данных и сериализация
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 53c1421bf14c598611e116c61353c4ecd465f1aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489210"
---
# <a name="data-transfer-and-serialization"></a>Передача данных и сериализация
В распределенных системах для выполнения каких-либо задач клиенты и службы обмениваются данными. Как разработчик службы или клиента необходимо также понять, как Windows Communication Foundation (WCF) обрабатывает и сериализации данных для создания приложений, которые эффективны и простые в обслуживании.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Задание передачи данных в контрактах служб](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Базовые принципы передачи данных в службах.  
  
 [Использование контрактов данных](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Понятие контрактов данных и процедур их создания и использования.  
  
 [Сериализатор контракта данных](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Сериализация данных с помощью класса <xref:System.Runtime.Serialization.DataContractSerializer> и каких-либо расширений класса <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 [Использование класса XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Способы и причины использования класса <xref:System.Xml.Serialization.XmlSerializer> в качестве альтернативы классу <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 [Использование контрактов сообщений](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 Точное управление сообщениями SOAP с помощью контрактов сообщений.  
  
 [Использование класса сообщений](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Использование возможностей класса Message.  
  
 [Фильтрация](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Фильтрация, позволяющая выполнять предварительную обработку сообщений на основе различных критериев.  
  
 [Большие наборы данных и потоковая передача](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Отправка больших фрагментов данных, например двоичных файлов.  
  
 [Вопросы безопасности для данных](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Вопросы, которые необходимо учитывать при решении задач сериализации и передачи данных.  
  
 [Общие сведения об архитектуре передачи данных](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Содержит описание представления обзор архитектуры передачи данных в WCF.  
  
## <a name="reference"></a>Ссылка  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширение кодировщиков и сериализаторов](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>См. также  
 [Рекомендации. Управление версиями контракта данных](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Управление версиями служб](../../../../docs/framework/wcf/service-versioning.md)
