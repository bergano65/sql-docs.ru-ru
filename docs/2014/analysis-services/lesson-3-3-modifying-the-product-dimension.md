---
title: Изменение измерения Product | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8e3ffecd-7f40-41a8-8735-bc9858a310cb
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ff912ed43048e00f0ed77989a46b3b7d0b111cff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078843"
---
# <a name="modifying-the-product-dimension"></a>Изменение измерения Product
  При выполнении задач этого раздела будут использованы именованные вычисления, чтобы предоставить понятные имена для линий товаров, определена иерархия в измерении «Продукт» и указано имя элемента «(Все)» для иерархии. Также атрибуты будут сгруппированы в папки отображения.  
  
## <a name="adding-a-named-calculation"></a>Добавление именованного вычисления  
 К таблице в представлении источника данных может быть добавлено именованное вычисление. В следующей задаче будет создано именованное вычисление, которое отображает полное наименование линейки продуктов.  
  
#### <a name="to-add-a-named-calculation"></a>Добавление именованного вычисления  
  
1.  Чтобы открыть представление источника данных **Adventure Works DW 2012**, дважды щелкните **Adventure Works DW 2012** в папке **Представления источников данных** в обозревателе решений.  
  
2.  В нижней части панели диаграмм щелкните правой кнопкой мыши заголовок таблицы **Продукт** и выберите команду **Создать именованное вычисление**.  
  
3.  В диалоговом окне **Создание именованного вычисления** введите `ProductLineName` в поле **имя столбца** .  
  
4.  В поле **Выражение** введите или скопируйте и вставьте следующую инструкцию **CASE**:  
  
    ```  
    CASE ProductLine  
       WHEN 'M' THEN 'Mountain'  
       WHEN 'R' THEN 'Road'  
       WHEN 'S' THEN 'Accessory'  
       WHEN 'T' THEN 'Touring'  
       ELSE 'Components'  
    END  
    ```  
  
     Эта инструкция **CASE** для каждой строки товара в кубе создает понятные имена.  
  
5.  Нажмите кнопку **ОК** , чтобы `ProductLineName` создать именованное вычисление. Возможно, потребуется подождать.  
  
6.  В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="modifying-the-namecolumn-property-of-an-attribute"></a>Изменение свойства NameColumn атрибута  
  
#### <a name="to-modify-the-namecolumn-property-value-of-an-attribute"></a>Изменение значения свойства NameColumn атрибута  
  
1.  В конструкторе измерений откройте измерение Product. Для этого дважды щелкните измерение **Продукт** в узле **Измерения** обозревателя решений.  
  
2.  На панели **Атрибуты** вкладки **Структура измерения** выберите **Product Line**.  
  
3.  В окно свойств в правой части экрана щелкните поле свойства **NameColumn** в нижней части окна, а затем нажмите кнопку обзора (**...**), чтобы открыть диалоговое окно **Столбец имени** . Возможно, потребуется перейти на вкладку **Свойства** в правой части окна, чтобы открыть окно "Свойства".  
  
4.  Выберите `ProductLineName` в нижней части списка **Исходный столбец** , а затем нажмите кнопку **ОК**.  
  
     Теперь поле NameColumn содержит текст **Product.ProductLineName (WChar)**. После этого элементы иерархии атрибута **Product Line** будут содержать не сокращенное, а полное наименование линейки продуктов.  
  
5.  На панели **Атрибуты** вкладки **Структура измерения** выберите **Product Key**.  
  
6.  В окно свойств щелкните поле свойства **NameColumn** , а затем нажмите кнопку обзора (**...**), чтобы открыть диалоговое окно **Столбец имени** .  
  
7.  Выберите в списке **Исходный столбец** значение **EnglishProductName** и нажмите кнопку **ОК**.  
  
     Теперь поле NameColumn содержит текст **Product.EnglishProductName (WChar)**.  
  
8.  В окно свойств прокрутите вниз, щелкните поле свойства **имя** и введите `Product Name`.  
  
## <a name="creating-a-hierarchy"></a>Создание иерархии  
  
#### <a name="to-create-a-hierarchy"></a>Создание иерархии  
  
1.  Перетащите атрибут **Product Line** с панели **Атрибуты** на панель **Иерархии**.  
  
2.  Перетащите атрибут **Model Name** с панели **атрибуты** на ** \<новый уровень>ной** ячейки на панели **иерархии** под уровнем **продукта** .  
  
3.  Перетащите `Product Name` атрибут с панели **атрибуты** на ** \<новый уровень>ную** ячейку на панели **иерархии** под уровнем **имя модели** . («Ключ продукта» был переименован в «Имя продукта» в предыдущем разделе.)  
  
4.  На панели **иерархии** вкладки **Структура измерения** щелкните правой кнопкой мыши строку заголовка иерархии **Иерархия** , выберите команду **Переименовать**, а затем введите `Product Model Lines`.  
  
     Теперь `Product Model Lines`имя иерархии —.  
  
5.  В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="specifying-folder-names-and-all-member-names"></a>Определение имен папок и имени элемента «Все»  
  
#### <a name="to-specify-the-folder-and-member-names"></a>Указание имен папок и элементов  
  
1.  На панели **Атрибуты** выберите следующие атрибуты (щелкните каждый из них, удерживая нажатой клавишу CTRL):  
  
    -   **Class**  
  
    -   **Color**  
  
    -   **Days To Manufacture**  
  
    -   **Reorder Point**  
  
    -   **Safety Stock Level**  
  
    -   **Размер**  
  
    -   **Size Range**  
  
    -   **Стиль**  
  
    -   **Вес**  
  
2.  В поле свойства **AttributeHierarchyDisplayFolder** в окно свойств введите `Stocking`.  
  
     Атрибуты сгруппированы в единую папку отображения.  
  
3.  На панели **Атрибуты** выберите следующие атрибуты:  
  
    -   **Dealer Price**  
  
    -   **List Price**  
  
    -   **Standard Cost**  
  
4.  В ячейке свойства **AttributeHierarchyDisplayFolder** в окно свойств введите `Financial`.  
  
     Атрибуты сгруппированы во вторую папку отображения.  
  
5.  На панели **Атрибуты** выберите следующие атрибуты:  
  
    -   **Дата окончания**  
  
    -   **Дата начала**  
  
    -   **Состояние**  
  
6.  В ячейке свойства **AttributeHierarchyDisplayFolder** в окно свойств введите `History`.  
  
     Атрибуты сгруппированы в третью папку отображения.  
  
7.  Выберите `Product Model Lines` иерархию на панели **иерархии** , а затем измените свойство **AllMemberName** в окно свойств на `All Products`.  
  
8.  Щелкните открытую область панели **иерархии** , а затем измените свойство **AttributeAllMemberName** в верхней части окно свойств на `All Products`.  
  
     Щелкнув рабочую область, можно изменять свойства самого измерения Product. Также можно щелкнуть значок измерения **Продукт** в начале списка атрибутов на панели **Атрибуты**.  
  
9. В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="defining-attribute-relationships"></a>Определение связей атрибутов  
 Необходимо определять связи между атрибутами, если базовые данные это поддерживают. Определение связей между атрибутами ускоряет обработку измерений, секций и запросов. Дополнительные сведения см. в разделах [Определение связей атрибутов](multidimensional-models/attribute-relationships-define.md) и [Связи атрибутов](multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md).  
  
#### <a name="to-define-attribute-relationships"></a>Определение связей атрибутов  
  
1.  В окне **Конструктор измерений** для измерения Product откройте вкладку **Связи атрибутов**.  
  
2.  На диаграмме щелкните правой кнопкой мыши атрибут **имя модели** и выберите команду **создать связь атрибутов**.  
  
3.  В диалоговом окне **Создание связи атрибутов** поле **Исходный атрибут** имеет значение **Имя модели**. Задайте для поля **Связанный атрибут** значение **Линейка продуктов**.  
  
     В списке **Тип связи** оставьте выбранным тип **Гибкая**, так как связи между элементами могут измениться с течением времени. Например, модель товара со временем могла быть перенесена в другую линию товаров.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  В меню **Файл** выберите команду **Сохранить все**.  
  
## <a name="reviewing-product-dimension-changes"></a>Просмотр изменений в измерении Product  
  
#### <a name="to-review-the-product-dimension-changes"></a>Просмотр изменений в измерении Product  
  
1.  В меню **Построение** среды [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]выберите команду **Развернуть Analysis Services Tutorial**.  
  
2.  Получив сообщение **Развертывание выполнено успешно**, перейдите на вкладку **Браузер** окна **Конструктор измерений** для измерения **Продукт** и нажмите на панели инструментов кнопку повторного соединения.  
  
3.  Убедитесь, `Product Model Lines` что в списке **Иерархия** выбрано значение, а `All Products`затем разверните.  
  
     Обратите внимание, что имя элемента **все** отображается как `All Products`. Это связано с тем, что свойство **AllMemberName** для иерархии было изменено на `All Products` более раннее занятие. Кроме того, все элементы уровня **Product Line** теперь имеют понятные имена, а не однобуквенные сокращения.  
  
## <a name="next-task-in-lesson"></a>Следующая задача занятия  
 [Изменение измерения Date](lesson-3-4-modifying-the-date-dimension.md)  
  
## <a name="see-also"></a>См. также:  
 [Определение именованных вычислений в представлении источника данных &#40;Analysis Services&#41;](multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)   
 [Создание определяемых пользователем иерархий](multidimensional-models/user-defined-hierarchies-create.md)   
 [Настройка &#40;всех уровней&#41; для иерархий атрибутов](multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
