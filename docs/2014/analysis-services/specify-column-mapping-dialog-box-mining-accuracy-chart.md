---
title: Диалоговое окно «Определение сопоставления столбцов» (диаграмма точности интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.coltotablecolmapping.f1
ms.assetid: 68e9e2d2-173f-4363-a515-fc60bfee3af0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4416a51ea32500d56c209d745065da20bf8010c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66068422"
---
# <a name="specify-column-mapping-dialog-box-mining-accuracy-chart"></a>Диалоговое окно «Указание сопоставления столбцов» (диаграмма точности интеллектуального анализа данных)
  Вкладка **Указание сопоставления столбцов** позволяет выбрать таблицы из внешнего источника данных и сопоставить столбцы с моделью интеллектуального анализа данных. Затем с помощью внешних данных можно проверить точность модели интеллектуального анализа данных и представить результаты в диаграмме точности.  
  
 **Дополнительные сведения:** [тестирование и проверка &#40;интеллектуального анализа данных&#41;](data-mining/testing-and-validation-data-mining.md)  
  
## <a name="options"></a>Параметры  
 **Структура интеллектуального анализа данных**  
 Показывает выбранную структуру интеллектуального анализа данных, в которых содержится модель, требующая проверки.  
  
 **Выбор структуры**  
 Нажмите, чтобы открыть диалоговое окно **Выбор структуры интеллектуального анализа данных** и выбрать другую структуру интеллектуального анализа данных.  
  
 **Выбор входных таблиц**  
 Показывает выбранные входные таблицы, используемые для формирования диаграммы точности прогнозов. Выберите таблицу, содержащую проверочные данные, которые будут использованы для проверки точности моделей.  
  
> [!NOTE]  
>  Если панель не содержит никаких таблиц, нажмите кнопку **Выбрать таблицу вариантов** , чтобы добавить таблицы из представления источников данных.  
  
 **Удаление таблицы**  
 Удаляет выбранную таблицу. Эта кнопка отключена, если не было выбрано ни одной таблицы или если в списке **Выбор входных таблиц** не отображаются никакие таблицы.  
  
 **Выбрать таблицу вариантов**  
 Нажмите, чтобы открыть диалоговое окно **Выбор таблицы** и выбрать представление источника данных.  
  
 **Примечание** . Эта кнопка появляется только в том случае, если таблица вариантов не была выбрана. Чтобы включить кнопку и получить возможность выбрать другую таблицу вариантов, очистите список, выбрав все существующие таблицы и нажав кнопку **Удалить таблицу**.  
  
 **Выбор вложенной таблицы**  
 Открывает диалоговое окно **Выбор таблицы** . Данная кнопка появляется, только если была выбрана таблица вариантов. Если связанная структура интеллектуального анализа данных не содержит вложенной таблицы, данная кнопка отключена.  
  
 **Изменить соединение**  
 Открывает диалоговое окно **Определение вложенного соединения** . Данная кнопка активна, только если выбрана вложенная таблица.  
  
## <a name="see-also"></a>См. также:  
 [Задачи тестирования и проверки и инструкции &#40;&#41;интеллектуального анализа данных](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md)   
 [Конструктор диаграмм точности интеллектуального анализа &#40;&#41;интеллектуального анализа данных](mining-accuracy-chart-designer-data-mining.md)  
  
  
