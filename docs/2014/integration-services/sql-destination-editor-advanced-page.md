---
title: Редактор назначения «SQL» (страница «Дополнительно») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sqlserverdestadapter.advanced.f1
helpviewer_keywords:
- SQL Server Destination Editor
ms.assetid: 9b46bcf8-ddaf-4d7d-90a6-80bc19517e9b
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 087f32510b65d7ea505bc4bf816a5ca9edcfe82d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055463"
---
# <a name="sql-destination-editor-advanced-page"></a>Редактор назначения SQL (страница «Дополнительно»)
  Используйте страницу **Дополнительно** в диалоговом окне **Редактор назначения «SQL»** , чтобы указать дополнительные параметры массовой вставки.  
  
 Дополнительные сведения о назначении «SQL Server» см. в разделе [SQL Server Destination](data-flow/sql-server-destination.md).  
  
## <a name="options"></a>Параметры  
 **Сохранит удостоверение**  
 Укажите, должна ли задача вставлять значения в столбцы идентификаторов. Значение по умолчанию этого свойства равно `False`.  
  
 **Сохранения значений NULL**  
 Укажите, должна ли данная задача сохранять значения NULL. Значение по умолчанию этого свойства равно `False`.  
  
 **Блокировка таблицы**  
 Укажите, будет ли таблица заблокирована в ходе загрузки данных. Значение по умолчанию этого свойства равно `True`.  
  
 **Проверочные ограничения**  
 Укажите, должна ли задача проверять ограничения. Значение по умолчанию этого свойства равно `True`.  
  
 **Пожарные триггеры**  
 Укажите, будет ли массовая вставка запускать триггеры таблиц. Значение по умолчанию этого свойства равно `False`.  
  
 **Первая строка**  
 Укажите первую вставляемую строку. Значение этого свойства по умолчанию равно **-1**, что означает, что значение не было назначено.  
  
> [!NOTE]  
>  Очистите текстовое поле в **Редакторе назначения «SQL»** , чтобы показать, что этому свойству не нужно присваивать значение. Используйте значение -1 в окне **Свойства** , **Расширенном редакторе**и объектной модели.  
  
 **Последняя строка**  
 Укажите последнюю вставляемую строку. Значение этого свойства по умолчанию равно **-1**, что означает, что значение не было назначено.  
  
> [!NOTE]  
>  Очистите текстовое поле в **Редакторе назначения «SQL»** , чтобы показать, что этому свойству не нужно присваивать значение. Используйте значение -1 в окне **Свойства** , **Расширенном редакторе**и объектной модели.  
  
 **Максимальное количество ошибок**  
 Укажите допустимое максимальное число ошибок, после превышения которого происходит прекращение массовой вставки. Значение этого свойства по умолчанию равно **-1**, что означает, что значение не было назначено.  
  
> [!NOTE]  
>  Очистите текстовое поле в **Редакторе назначения «SQL»** , чтобы показать, что этому свойству не нужно присваивать значение. Используйте значение -1 в окне **Свойства** , **Расширенном редакторе**и объектной модели.  
  
 **Счетчик**  
 Укажите количество секунд ожидания, по истечении которых массовая вставка будет прекращена.  
  
 **Порядок столбцов**  
 Введите имена столбцов сортировки. Любой столбец можно сортировать в порядке возрастания или в порядке убывания. Если нужно задать несколько столбцов сортировки, используйте в качестве разделителей запятые.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор назначения "SQL" &#40;страница "Диспетчер соединений"&#41;](../../2014/integration-services/sql-destination-editor-connection-manager-page.md)   
 [Редактор назначения "SQL &#40;страниц сопоставления"&#41;](../../2014/integration-services/sql-destination-editor-mappings-page.md)   
 [Выполнение массовой загрузки данных с помощью назначения «SQL Server»](data-flow/bulk-load-data-by-using-the-sql-server-destination.md)  
  
  
