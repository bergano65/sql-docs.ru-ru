---
title: Отмена запрета предупреждений для пользовательских отчетов | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ed653b16fe524f364ba89f13e00715b725080033
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62824401"
---
# <a name="unsuppress-run-custom-report-warnings"></a>Отмена подавления предупреждений для пользовательских отчетов
  Для пользовательских отчетов предусмотрено два типа предупреждающих диалоговых окон. В этом разделе описано, как отменить подавление отображения этих полей в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
 По умолчанию перед запуском пользовательского отчета отображается диалоговое окно **Запустить пользовательский отчет** . Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет. Также по умолчанию диалоговое окно **Запустить пользовательский отчет** отображается, если после открытия одного пользовательского отчета нажать ссылку для открытия другого отчета. В этом диалоговом окне отображается полный путь к файлу пользовательского детализированного отчета. Если установить флажок **Больше не показывать это предупреждение** , то это диалоговое окно больше отображаться не будет.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>Отмена подавления основного диалогового окна предупреждения для пользовательских отчетов  
  
1.  Подключитесь \<к *серверу*>\\<*Общий*** \\ \>диск> \Documents and Settings<UserProfile \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.XML.>|\<  
  
2.  `reports.xml`Щелкните правой кнопкой мыши и выберите пункт **изменить**.  
  
3.  Замените**\<SuppressWarning>true\<>/суппрессварнинг на \<SuppressWarning>false\</суппрессварнинг>**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>Отмена подавления диалогового окна предупреждений для детализированных пользовательских отчетов  
  
1.  Подключитесь \<к *серверу*>\\<*Общий*** \\ \>диск> \Documents and Settings<UserProfile \Application Data\Microsoft\Microsoft SQL Server\120\Tools\Shell\reports.XML.>|\<  
  
2.  `reports.xml`Щелкните правой кнопкой мыши и выберите **изменить**.  
  
3.  Замените ** \<SuppressDrillthroughWarning>true\<>/суппрессдриллсраугхварнинг на \<SuppressDrillthroughWarning>false\</суппрессдриллсраугхварнинг>**.  
  
4.  Перезапустите [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Пользовательские отчеты в Management Studio](custom-reports-in-management-studio.md)   
 [Добавление пользовательского отчета в Management Studio](add-a-custom-report-to-management-studio.md)   
 [Использование пользовательских отчетов для свойств узлов обозревателя объектов](use-custom-reports-with-object-explorer-node-properties.md)  
  
  
