---
title: Страница "Просмотр", отчеты (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4874ba29-429b-4dd4-a8cb-d4f087237dc2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c8731c1d0f79d99919c4a087521565a6ec590278
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66098742"
---
# <a name="view-page-reports-report-manager"></a>Страница «Вид», отчеты (диспетчер отчетов)
  Просмотреть отчет можно на странице «Просмотр». При первом открытии в диспетчере отчетов отчет имеет формат HTML. В верхней части HTML-отчета содержится панель инструментов, позволяющая перемещаться по страницам отчета, выполнять поиск или экспортировать отчет в другой формат. На следующей диаграмме представлена панель инструментов «Отчеты».  
  
 ![Панель инструментов «Отчеты»](media/htmlviewer-toolbar.gif "Панель инструментов «Отчеты»")  
Панель инструментов «Отчеты»  
  
 В службах [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]отчеты можно настроить таким образом, чтобы они выполнялись по запросу или из снимка состояния выполнения отчета. Если отчет выполняется по требованию, обработка всех данных и отчета происходит при открытии отчета. Если просматривается отчет, настроенный для выполнения как снимок состояния выполнения отчета, данные обрабатываются при создании моментального снимка.  
  
## <a name="exporting-reports"></a>Экспорт отчетов  
 Не все функции отчетов доступны во всех без исключения экспортируемых форматах. При экспорте HTML-отчета в другой формат возможны некоторые отличия в его отображении. Кроме того, если отчет содержит интерактивные функции (гиперссылки, закладки или схемы документов), они могут быть недоступны или работать по-другому в новом формате.  
  
## <a name="generating-data-feeds-from-report-data"></a>Формирование потоков данных из данных отчетов  
 Каналы данных можно формировать с помощью отчетов. Модуль подготовки отчетов служб [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Atom формирует два документа, совместимые с протоколом Atom: сервисный документ Atom, в котором перечислены веб-каналы данных, доступные в отчете, а также веб-каналы данных, содержащие данные отчета. Веб-каналы данных создаются службами [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] в стандартизированном формате, совместимом с Atom 1.0, который поддерживает возможность чтения и обмена данными с другими приложениями, потребляющими веб-каналы данных, совместимые с Atom. Примером клиента, потребляющего веб-каналы данных, которые формируются из отчетов, является клиент [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] .  
  
## <a name="running-parameterized-reports"></a>Запуск параметризованных отчетов  
 Параметризированными называются отчеты, содержащие поля ввода и кнопку **Просмотр отчета** . Чтобы просмотреть параметризированный отчет, необходимо задать значения, которые используются для его выполнения.  
  
> [!NOTE]  
>  Моментальные снимки состояния выполнения отчетов и некоторые форматы экспорта доступны не во всех выпусках [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Дополнительные сведения см. [в разделе функции, поддерживаемые различными Выпусками SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="see-also"></a>См. также:  
 [Диспетчер отчетов (службы Reporting Services в основном режиме)](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [Справка F1 диспетчера отчетов](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
