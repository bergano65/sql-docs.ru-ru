---
title: Создание структуры интеллектуального анализа данных (SQL Server надстроек интеллектуального анализа) | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures, creating
ms.assetid: b8b1eedc-4d6d-4429-a578-e629ec573934
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ae5244110e6b95434f9008fd7dc99cee259acf8c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66086821"
---
# <a name="create-mining-structure-sql-server-data-mining-add-ins"></a>Создание структуры интеллектуального анализа данных (надстройки интеллектуального анализа данных SQL Server)
  ![Кнопка «Создать структуру интеллектуального анализа данных» на ленте «Интеллектуальный анализ данных»](media/dmc-createstruct.gif "Кнопка «Создать структуру интеллектуального анализа данных» на ленте «Интеллектуальный анализ данных»")  
  
 Используйте параметр **Дополнительно** в группе **моделирование данных** , если необходимо создать набор данных, используемый для анализа без обязательного создания модели. Это полезно, если необходимо поэкспериментировать с различными алгоритмами.  
  
 После создания структуры интеллектуального анализа данных используйте мастер [добавления модели в структуру](add-model-to-structure-data-mining-add-ins-for-excel.md) , чтобы создать модель на основе этой структуры. Новые модели также можно создавать с помощью **расширенного редактора запросов интеллектуального анализа данных**.  
  
 Этот вариант также позволяет создавать модели на основе одного из расширенных алгоритмов, поддерживаемых службами [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], но недоступных в мастере, например на основе линейной регрессии или кластеризации последовательностей либо когда используется пользовательский алгоритм.  
  
> [!NOTE]  
>  При создании структуры интеллектуального анализа данных также можно задать случайный набор проверочных данных для проверки всех моделей. Таким образом удобно сравнивать точность моделей с помощью общего набора данных. Просто выберите параметр, **Разделите данные на обучающие и проверочные наборы** и укажите соответствующий процент данных, которые необходимо зарезервировать для тестирования, обычно около 30 процентов.  
  
## <a name="use-the-wizard-to-create-a-mining-structure"></a>Использование мастера создания структуры интеллектуального анализа данных  
  
1.  На ленте **интеллектуальный анализ данных** нажмите кнопку **Дополнительно**и выберите **создать структуру**.  
  
2.  В диалоговом окне **Выбор источника данных** укажите диапазон Excel, таблицу данных Excel или внешний источник данных, содержащий данные, которые необходимо использовать для анализа.  
  
     Щелкните **Далее**.  
  
3.  В диалоговом окне **Выбор столбцов** проверьте список столбцов, доступных в выбранном источнике данных.  
  
4.  Щелкните стрелку справа от имени столбца, чтобы изменить **Использование** столбца, выбрав следующие значения:  
  
    -   **Ключ**. По крайней мере один ключ необходим для каждой модели.  
  
    -   **Ключевое время**. Этот параметр доступен только для моделей прогнозирования, в которых он является обязательным.  
  
    -   **Включить**. Указывает, что столбец должен быть доступен в структуре интеллектуального анализа данных, но не является ключевым столбцом.  
  
    -   **Не используйте**. Указывает, что столбец не может быть частью структуры интеллектуального анализа данных.  
  
     Следует помнить, что всегда можно пропустить столбцы при построении модели, а вот для добавления столбцов после построения необходимо будет выполнить повторную обработку структуры и модели.  
  
5.  Нажмите кнопку обзора **(...)** , чтобы задать тип содержимого, тип данных и флаги модели.  
  
    > [!NOTE]  
    >  Если столбец содержит числовые данные, следует открыть это диалоговое окно, чтобы убедиться, что выбран правильный тип данных. В некоторых случаях, даже если входные данные числовые, их необходимо обрабатывать как категорийную переменную или дискретные значения, а не непрерывные числа.  
    >   
    >  Например, столбец с почтовыми индексами по умолчанию может обрабатываться как непрерывный большой тип данных, однако для получения лучших результатов можно указать, что он должен обрабатываться как дискретное текстовое значение.  
    >   
    >  Дополнительные сведения см. в разделе Типы содержимого раздела [Выбор данных для интеллектуального анализа данных](choosing-data-for-data-mining.md).  
  
     Нажмите кнопку **ОК**, чтобы закрыть диалоговое окно.  
  
6.  Щелкните **Далее**.  
  
     В зависимости от типа используемых данных может потребоваться выполнить мастер после этого шага. В этом случае перейдите на страницу **Готово** , чтобы присвоить имя структуре интеллектуального анализа данных.  
  
     Для других моделей можно дополнительно создать набор проверочных данных.  
  
7.  В диалоговом окне **разбиение данных на обучающие и проверочные наборы данных** укажите, как следует секционировать данные. По умолчанию для проверки используется 30 процентов данных.  
  
     Дополнительно можно ввести максимальное число строк, используемых для проверки.  
  
     Щелкните **Далее**.  
  
8.  В диалоговом окне **Завершение** введите имя и описание для новой структуры интеллектуального анализа данных.  
  
9. Нажмите кнопку **Готово**.  
  
### <a name="related-options"></a>Связанные параметры  
  
|Параметр|Комментарии|  
|------------|--------------|  
|Диалоговое окно « **Выбор источника данных** »|Если выбрать таблицу Excel, необходимо указать, имеют ли данные заголовки. Если пропустить этот шаг, первая строка данных будет использоваться в качестве заголовка столбца.<br /><br /> При использовании параметра **внешний источник данных**можно использовать любой тип данных, которые могут быть определены в источнике [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] данных. Однако диалоговое окно в надстройке для создания новых источников данных не содержит весь спектр источников данных, поддерживаемых службами Analysis Services. В силу этого рекомендуется создавать источники данных на сервере служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] заранее и затем подключать их с помощью надстроек.|  
|Диалоговое окно « **Редактор запросов источника данных** »|После подключения к указанному источнику данных можно добавить столбцы или создать собственные с помощью запроса.|  
|**Разделение данных на обучающий и проверочный наборы**|Рекомендуемое значение для обучения и проверочных наборов составляет 70% для обучения и 30% для тестирования; Однако при наличии большого объема данных можно указать максимальное количество строк для тестирования.|  
|Диалоговое окно «Завершение»|Параметры для детализации углублением доступны для определенных типов моделей и могут быть полезны, если в структуре интеллектуального анализа данных используются столбцы с подробными значениями. Например, если создается модель кластеризации, можно включить сведения, такие как имя или адрес электронной почты, для детализации, но не для анализа, чтобы упростить связь с клиентами в определенном кластере.|  
  
###  <a name="Bkmk_strctcolumn"></a>Задание использования столбцов в мастере создания структуры интеллектуального анализа данных  
 При создании новой структуры интеллектуального анализа данных можно указать, какие столбцы в источнике данных следует включать в структуру, а также то, как эти столбцы будут использоваться. Помните, что структура интеллектуального анализа данных может содержать несколько моделей интеллектуального анализа данных.  
  
|Значения|Description|  
|------------|-----------------|  
|**Относится**|Данные в этом столбце могут быть использованы только для анализа или прогнозирования.|  
|**Key**|Столбец содержит идентификатор транзакции, идентификатор ряда или другой ключ, необходимый для обработки.<br /><br /> Для всех алгоритмов требуется ключевой столбец. Однако в одних алгоритмах разрешается использовать только один ключ, а в других — несколько.<br /><br /> Если столбец содержит ключ, но не является обязательным для обработки, выберите не **использовать**.|  
|**Ключевой столбец времени**|Указывает, что столбец содержит дату или другое числовое значение, которое можно использовать для уникальной идентификации элементов во временном ряду.|  
|**Не используйте**|Указывает, что столбец обрабатываться не будет. Данные в этом столбце не будут обработаны.|  
  
 Для правильной обработки модели алгоритму должен быть известен ключевой столбец, уникальным образом идентифицирующий каждую строку; целевой столбец для создания прогнозов в случае формирования прогнозируемой модели, а также столбцы, которые следует использовать в качестве входных при создании связей для предсказания целевого столбца.  
  
-   Столбцы, заданные как не **используемые** , не будут присутствовать в структуре интеллектуального анализа данных.  
  
     Добавление столбцов, которые являются ненужными или содержат неправильные значения, может оказать неблагоприятное воздействие на результаты анализа. Поэтому в структуру следует включать только нужные столбцы. Отметим, однако, что столбцы, которые не используются в структуре интеллектуального анализа данных, для запросов будут недоступны.  
  
-   Столбцы, указанные как тип **включения** , будут включены в структуру интеллектуального анализа данных, а позднее можно будет использовать для анализа или прогнозирования в моделях интеллектуального анализа данных.  
  
     Если нет полной уверенности в том, следует ли использовать данный столбец, его всегда можно включить в структуру интеллектуального анализа данных, а затем создать модель интеллектуального анализа данных, в которой столбец не будет применяться. Например, можно включить в данные столбец с номерами телефонов для последующего обращения, но создать модель кластеризации, которая не учитывает номера телефонов. После создания кластеров можно создать запрос, который возвращает номера телефонов людей, принадлежащих определенному кластеру.  
  
-   Для всех алгоритмов требуется **ключевой** столбец. Значения в ключевом столбце должны быть уникальными. **Ключевой столбец времени** необходим только для прогнозирования или моделей временных рядов. .  
  
### <a name="requirements"></a>Требования  
 Чтобы создать структуру интеллектуального анализа данных, необходимо установить соединение с экземпляром служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. Соединение необходимо даже при работе с временными структурами. Дополнительные сведения о создании или изменении подключения см. в разделе [Подключение к источнику данных &#40;клиент интеллектуального анализа данных для Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).  
  
## <a name="see-also"></a>См. также:  
 [Создание модели интеллектуального анализа данных](creating-a-data-mining-model.md)  
  
  
