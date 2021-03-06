---
title: Импорт данных (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6617b2a2-9f69-433e-89e0-4c5dc92982cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b7eb3fe1157ba40466cc619f504255084aa845fa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66080618"
---
# <a name="import-data-ssas-tabular"></a>Импорт данных (табличные службы SSAS)
  Данные можно импортировать в табличную модель из разнообразных источников. Здесь представлены разделы, в которых описано использование мастера импорта данных для подключения и выбора данных, импортируемых в проект модели.  
  
> [!IMPORTANT]  
>  Если какая-либо из таблиц в модели будет содержать большое количество строк, во время разработки модели рассмотрите возможность импортировать только часть данных. Путем частичного импорта данных можно уменьшить время обработки и потребление ресурсов сервера баз данных рабочей области.  
  
 С помощью мастера импорта таблиц можно импортировать данные из следующих источников данных:  
  
|**Источник данных**|**Описание**|  
|---------------------|---------------------|  
|**Реляционные базы данных**|Реляционные источники данных включают:<br /><br /> Microsoft SQL Server<br /><br /> Microsoft SQL Azure<br /><br /> Параллельные хранилища данных Microsoft SQL Server<br /><br /> Microsoft Access<br /><br /> Oracle;<br /><br /> Teradata<br /><br /> Sybase<br /><br /> Informix<br /><br /> IBM DB2<br /><br /> OLEDB/ODBC|  
|**Многомерные источники**|Куб служб Microsoft SQL Server Analysis Services|  
|**Веб-каналы данных**|Веб-каналы данных включают:<br /><br /> Отчет служб Microsoft Reporting Services<br /><br /> Набор данных Azure DataMarket<br /><br /> Веб-каналы Atom от общедоступного или корпоративного поставщика|  
|**Текстовые файлы**|Текстовые файлы включают:<br /><br /> Файлы Excel (XLSX)<br /><br /> Текстовый файл (TXT)|  
  
 В дополнение к импорту данных с помощью мастера импорта таблиц, данные можно скопировать и вставить (из буфера обмена) в таблицу. Вставляемые данные ведут себя иначе, чем данные, которые были импортированы из других источников данных. Вставляемые данные в таблицах не обладают свойством имени соединения или данных источника. Вставленные данные сохраняются в файле Model.bim. При сохранении проекта или файла Model.bim вставленные данные также будут сохранены.  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Импорт из реляционного источника данных &#40;табличные&#41;SSAS](import-from-a-relational-data-source-ssas-tabular.md)|Описывает, как импортировать данные из реляционных источников данных, таких как базы данных Microsoft SQL Server, Oracle или Teradata.|  
|[Импорт из многомерного источника данных &#40;табличные&#41;SSAS](import-from-a-multidimensional-data-source-ssas-tabular.md)|Описывает, как импортировать данные из многомерного куба служб SQL Server Analysis Services.|  
|[Импорт из веб-канала данных &#40;табличные&#41;SSAS](import-from-a-data-feed-ssas-tabular.md)|Описывает, как импортировать данные из веб-канала данных, такого как отчет служб Microsoft Reporting Services или набор данных Azure Data Market Dataset.|  
|[Импорт из текстового файла &#40;табличные&#41;SSAS](import-from-a-text-file-ssas-tabular.md)|Описывает, как импортировать данные из книги Microsoft Excel или текстового файла.|  
|[Копирование и вставка данных &#40;табличные&#41;SSAS](copy-and-paste-data-ssas-tabular.md)|Описывает, как добавить данные в существующую таблицу в конструкторе моделей с помощью команд «Вставить» и «Вставить с добавлением».|  
  
  
