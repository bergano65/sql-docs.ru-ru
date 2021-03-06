---
title: Свойства полнотекстового индекса (страница «Столбцы») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 67b7e72e0c4b248e8951667561eaf7548bfba1b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62778859"
---
# <a name="full-text-index-properties-columns-page"></a>Свойства полнотекстового индекса (страница «Столбцы»)
  **Просмотр или изменение свойств полнотекстового индекса**  
  
-   [Управление полнотекстовыми индексами](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Уникальный индекс**  
 Выберите индекс из раскрывающегося списка. Индекс должен иметь один ключевой столбец, быть уникальным и не допускающим значения NULL.  
  
 **Выберите подходящие столбцы, для которых будет построен полнотекстовый индекс**  
 В сетке отображаются столбцы таблицы, доступные для этого полнотекстового индекса. Для столбцов, которые включены в полнотекстовый индекс, установлены флажки. Можно установить флажки для дополнительных столбцов, которые нужно включить в полнотекстовый индекс.  
  
> [!IMPORTANT]  
>  Убедитесь, что выбран хотя бы один столбец, и нажмите кнопку «ОК».  
  
|||  
|-|-|  
|**Доступные столбцы**|Имя столбца.|  
|**Язык для разбиения по словам**|Язык, для которого средства разбиения по словам и парадигматические модули выполняют лингвистический анализ данных, проходящих полнотекстовое индексирование.<br /><br /> Дополнительные сведения см. в статьях [Настройка и Управление разделителями слов и парадигматические модули для поиска](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md) и [Выбор языка при создании полнотекстового индекса](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md).|  
|**Тип**|Имя столбца таблицы, который содержит тип документа выбранного столбца. Это свойство доступно только для чтения.|  
|**Статистическая семантика**|Укажите, следует ли включить статистическое семантическое индексирование для выбранного столбца. Дополнительные сведения см. в разделе [Семантический поиск (SQL Server)](../relational-databases/search/semantic-search-sql-server.md).<br /><br /> Если **Язык** выбран до выбора режима **Статистическая семантика**и выбранный язык не имеет связанной семантической модели языка, флажок **Статистическая семантика** будет недоступным. Если режим **Статистическая семантика** выбран до выбора **Языка**, в раскрывающемся поле со списком будут доступны только языки, имеющие семантическую модель языка.|  
  
## <a name="see-also"></a>См. также:  
 [Заполнение полнотекстовых индексов](../relational-databases/search/populate-full-text-indexes.md)  
  
  
