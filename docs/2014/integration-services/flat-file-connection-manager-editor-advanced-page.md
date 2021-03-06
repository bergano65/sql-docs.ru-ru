---
title: Редактор диспетчера соединений с неструктурированными файлами (страница "Дополнительно") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.ffileconnection.columnproperties.f1
helpviewer_keywords:
- Flat File Connection Manager Editor
ms.assetid: 58aa3dee-4774-4e0b-a956-96d199be4c3a
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0e6e85161ea95a9494bbaf91338b4ddc559ecbf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66058793"
---
# <a name="flat-file-connection-manager-editor-advanced-page"></a>Редактор диспетчера соединений с неструктурированными файлами (страница «Дополнительно»)
  Страница **Дополнительно** диалогового окна **Редактор диспетчера соединения с неструктурированными файлами** используется для установки свойств, указывающих, как службы Integration Services считывают и записывают данные в неструктурированные файлы. Можно изменить имена столбцов неструктурированного файла и установить свойства, включающие тип данных и разделители для каждого столбца файла.  
  
 По умолчанию, длина строковых столбцов составляет 50 символов. Чтобы не допустить усечения данных или установки избыточной ширины столбца, можно изменить длину столбцов. Также можно обновить другие метаданные, чтобы обеспечить совместимость с целевыми столбцами. Например, можно изменить тип данных столбца, который содержит только целые данные, на числовой тип данных, например DT_I2. Эти изменения можно выполнить вручную или нажать кнопку **Выбор типов** , чтобы вывести диалоговое окно **Предлагаемые типы столбцов** , оценить образец данных и выполнить некоторые из этих изменений автоматически.  
  
 Дополнительные сведения о диспетчере соединений с неструктурированными файлами см. в разделе [Flat File Connection Manager](connection-manager/file-connection-manager.md).  
  
## <a name="options"></a>Параметры  
 **Имя диспетчера соединений**  
 Введите уникальное имя для диспетчера соединений с неструктурированными файлами в рабочем процессе. Выбранное имя будет отображаться в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 **Описание**  
 Задайте описание диспетчера соединений. Рекомендуется описать назначение диспетчера соединений, чтобы сделать пакеты самодокументируемыми и более простыми в использовании.  
  
 **Настройка свойств каждого столбца**  
 Выберите столбец в левой панели для просмотра его свойств в правой панели. В нижеследующей таблице приведены описания свойств типов данных.  Некоторые перечисленные свойства могут настраиваться только для некоторых форматов неструктурированных файлов.  
  
|Свойство|Description|  
|--------------|-----------------|  
|**ColumnType**|Указывает, ограничен ли столбец специальным символом, фиксированной шириной или оборван по правому краю. Это свойство доступно только для чтения. В файлах с текстом без выравнивания вправо каждый столбец имеет фиксированную ширину, за исключением последнего столбца. Он отделяется разделителем строк.|  
|**аутпутколумнвидс**|Укажите значение, которое будет храниться как количество байтов. Для файлов в кодировке Юникод это будет соответствовать количеству символов. В задаче потока данных это значение используется для задания ширины выходных столбцов для источника неструктурированного файла.<br /><br /> Примечание. В объектной модели это свойство имеет имя MaximumWidth.|  
|**DataType**|Выберите из списка доступных типов данных. Дополнительные сведения см. в разделе [Integration Services Data Types](data-flow/integration-services-data-types.md).|  
|**тексткуалифиед**|Указывает, окружены ли текстовые данные символами-квалификаторами текста, такими как символы кавычек. Допустимые значения:<br /><br /> **True**: текстовые данные в неструктурированном файле являются полными.<br /><br /> **False**: текстовые данные в неструктурированном файле не являются полными.|  
|**Название**|Введите описательное имя столбца. Если не вводить имя, службы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] автоматически создадут его в формате «Столбец 0», «Столбец 1» и так далее.|  
|**Масштабирование**|Укажите масштаб числовых данных. Масштаб представляет собой количество разрядов в числе. Дополнительные сведения см. в разделе [Integration Services Data Types](data-flow/integration-services-data-types.md).|  
|**ColumnDelimiter**|Выберите из списка допустимых разделителей столбцов. Выберите разделители, которые не могут встретиться в тексте. Это значение пропускается для столбцов фиксированной ширины.<br /><br /> **{CR} {LF}**. Столбцы разделяются парой символов возврата каретки и перевода строки.<br /><br /> **{CR}**. Столбцы разделяются символом возврата каретки.<br /><br /> **{LF}**. Столбцы разделяются символом перевода строки.<br /><br /> **Точка с запятой {;}**. Столбцы разделяются символом точки с запятой.<br /><br /> **Двоеточие {:}**. Столбцы разделяются символом двоеточия.<br /><br /> **Запятая {,} **. Столбцы разделяются символом запятой.<br /><br /> **Tab {t}**. Столбцы разделяются символом табуляции.<br /><br /> **Вертикальная черта {&#124;}**. Столбцы разделяются символом вертикальной черты.|  
|**Точность с точностью**|Укажите точность числовых данных. Точность представляет собой число разрядов. Дополнительные сведения см. в разделе [Integration Services Data Types](data-flow/integration-services-data-types.md).|  
|**инпутколумнвидс**|Укажите значение, которое будет храниться как количество байтов; для файлов в кодировке Юникод это будет отображаться как количество символов. Это значение пропускается для столбцов, ограниченных разделителями.<br /><br /> **Примечание** . В объектной модели имя этого свойства — Колумнвидс.|  
  
 **Создать**  
 Добавьте новый столбец, нажав кнопку **Создать**. По умолчанию, кнопка **Создать** добавляет новый столбец в конец списка. Эта кнопка также имеет следующие параметры, доступные в раскрывающемся списке.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Добавление столбца.**|Добавить новый столбец в конец списка.|  
|**Вставить до**|Вставить новый столбец перед выделенным столбцом.|  
|**Вставить после**|Вставить новый столбец после выделенного столбца.|  
  
 **Удаление**  
 Выберите столбец и затем удалите его, нажав кнопку **Удалить**.  
  
 **Предложить типы**  
 Используйте диалоговое окно **Предлагаемые типы столбцов** , чтобы оценить образец данных в файле и получить предложения для типа данных и длины каждого столбца. Дополнительные сведения см. в разделе [Диалоговое окно "Предложение типов столбцов" справочника по пользовательскому интерфейсу](connection-manager/suggest-column-types-dialog-box-ui-reference.md).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор диспетчера соединений с неструктурированными файлами &#40;страница "Общие"&#41;](general-page-of-integration-services-designers-options.md)   
 [Редактор диспетчера соединений с неструктурированными файлами &#40;столбцы&#41;](../../2014/integration-services/flat-file-connection-manager-editor-columns-page.md)   
 [Редактор диспетчера соединений с неструктурированными файлами &#40;страница предварительного просмотра&#41;](../../2014/integration-services/flat-file-connection-manager-editor-preview-page.md)  
  
  
