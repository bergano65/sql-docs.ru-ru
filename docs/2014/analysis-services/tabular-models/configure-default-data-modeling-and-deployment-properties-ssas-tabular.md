---
title: Настройка моделирования данных по умолчанию и свойств развертывания (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.deployment.f1
- VS.TOOLSOPTIONSPAGES.ANALYSIS_SERVICES.DATA_MODELING
- sql12.asvs.bidtoolset.asoptions.f1
- VS.TOOLSOPTIONSPAGES.ANALYSIS_SERVICES.DEPLOYMENT
ms.assetid: 140d0c4e-943c-4387-a8d2-6e066c7e4e75
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e1246119b72890bc80125034c8ee23bcd0c221b5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66067584"
---
# <a name="configure-default-data-modeling-and-deployment-properties-ssas-tabular"></a>Настройка моделирования данных по умолчанию и свойств развертывания (табличные службы SSAS)
  В этом разделе описано, как настроить свойство уровня совместимости по умолчанию, свойства базы данных развертывания и рабочей области, для которых можно указать предопределенные значения во всех новых проектах табличных моделей, создаваемых в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. После создания нового проекта эти свойства в конкретной модели по-прежнему можно изменить в зависимости от определенных требований.  
  
#### <a name="to-configure-the-default-compatibility-level-property-setting-for-new-model-projects"></a>Настройка свойства уровня совместимости по умолчанию для новых проектов модели  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите в меню **Сервис** пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните раздел **Конструкторы табличных моделей служб Analysis Services**и нажмите кнопку **Уровень совместимости**.  
  
3.  Настройте следующие свойства:  
  
    |Свойство|Значение по умолчанию|Description|  
    |--------------|---------------------|-----------------|  
    |**Уровень совместимости по умолчанию для новых проектов**|SQL Server 2012 (1100)|Этот параметр задает уровень совместимости по умолчанию, используемый при создании нового проекта табличной модели. Вы можете выбрать SQL Server 2012 RTM (1100) при развертывании на экземпляре служб Analysis Services без примененного пакета обновлений 1 (SP1) или SQL Server 2012 с пакетом обновления 1 (SP1), если экземпляр развертывания используется с пакетом обновления 1 (SP1) или SQL Server 2014. Дополнительные сведения см. в разделе [уровень совместимости &#40;табличный пакет обновления 1 (SP1)&#41;](compatibility-level-for-tabular-models-in-analysis-services.md).|  
    |**Параметры уровня совместимости**|Все выбранные|Определяет параметры уровня совместимости для новых проектов табличной модели и при развертывании на другом экземпляре служб Analysis Services.|  
  
#### <a name="to-configure-the-default-deployment-server-property-setting-for-new-model-projects"></a>Настройка параметров свойства сервера развертывания по умолчанию для новых проектов модели  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите в меню **Сервис** пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните пункт **Конструкторы табличных моделей служб Analysis Services**и нажмите кнопку **Развертывание**.  
  
3.  Настройте следующие свойства:  
  
    |Свойство|Значение по умолчанию|Description|  
    |--------------|---------------------|-----------------|  
    |**Сервер развертывания по умолчанию**|localhost|Этот параметр определяет сервер по умолчанию для использования при развертывании модели. Для просмотра доступных для использования серверов служб Analysis Services локальной сети можно щелкнуть стрелку вниз или ввести имя удаленного сервера.|  
  
    > [!NOTE]  
    >  Изменение параметров свойств сервера развертывания по умолчанию не влияет на существующие проекты, созданные до внесения изменения.  
  
###  <a name="bkmk_conf_default"></a>Настройка параметров свойств базы данных рабочей области по умолчанию для новых проектов модели  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите в меню **Сервис** пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните пункт **Конструкторы табличных моделей служб Analysis Services**и нажмите кнопку **База данных рабочей области**.  
  
3.  Настройте следующие свойства:  
  
    |Свойство|Значение по умолчанию|Description|  
    |--------------|---------------------|-----------------|  
    |**Сервер рабочей области по умолчанию**|**localhost**|Это свойство определяет сервер по умолчанию, на котором будет размещена база данных рабочей области во время разработки модели в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. В списке отображаются все доступные экземпляры служб Analysis Services, запущенные на локальном компьютере.<br /><br /> Примечание. Рекомендуется всегда указывать в качестве сервера рабочей области локальный сервер служб Analysis Services. Если базы данных рабочей области находятся на удаленном сервере, то импорт данных из PowerPivot не поддерживается, локальное резервное копирование данных недоступно, а пользовательский интерфейс во время выполнения запросов может работать медленно.|  
    |**Хранение базы данных рабочей области после закрытия модели**|**Не используйте базы данных рабочей области на диске, но выгрузите из памяти**|Указывает, как база данных рабочей области должна сохраняться после закрытия модели. База данных рабочей области содержит метаданные модели, данные, импортированные в модель, а также учетные данные олицетворения (в зашифрованном виде). В некоторых случаях база данных рабочей области может иметь очень большой размер и, соответственно, занимать значительный объем памяти. По умолчанию базы данных рабочей области удаляются из памяти. При изменении этого параметра важно учитывать объем доступных ресурсов памяти, а также предполагаемую частоту работы с этой моделью. Возможны следующие варианты значения этого параметра.<br /><br /> Не **отображать рабочие области в памяти** — указывает, что рабочие области сохраняются в памяти после закрытия модели. Этот параметр ведет к использованию дополнительных ресурсов памяти. Однако при открытии модели в [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]потребляется меньшее количество ресурсов и рабочая область загружается быстрее.<br /><br /> **Синхронизировать базы данных рабочей области на диске, но выгрузить из памяти** — указывает, что база данных рабочей области сохраняется на диске, но больше не находится в памяти после закрытия модели. При выборе этого варианта используется меньше памяти, однако при открытии модели в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]потребляются дополнительные ресурсы, а модель будет загружаться медленнее, чем в случае, если база данных рабочей области сохраняется в памяти. Этот вариант следует использовать в случае, если ресурсы памяти ограниченны, или при работе с дистанционно расположенной базой данных рабочей области.<br /><br /> **Удалить рабочую область** — указывает удалить базу данных рабочей области из памяти и не сохранит базу данных рабочей области на диске после закрытия модели. При выборе этого параметра используется меньше памяти и пространства в хранилище, однако при открытии модели в среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]потребляются дополнительные ресурсы и модель будет загружаться медленнее, чем в случае, когда база данных рабочей области сохраняется в памяти или на диске. Применяйте этот вариант для моделей, которые используются относительно редко.|  
    |**Резервное копирование данных**|**Выполнять резервное копирование данных на диске**|Указывает, сохраняется ли резервная копия данных модели в файле резервной копии. Возможны следующие варианты значения этого параметра.<br /><br /> **Резервное копирование данных на диске** . указывает, что резервная копия данных модели хранится на диске. При сохранении модели данные также будут сохранены в файле резервной копии (ABF). При выборе этого параметра время сохранения и загрузки модели может увеличиться.<br /><br /> **Не удерживать резервную копию на диске** . указывает, что не следует создавать резервные копии данных модели на диске. Этот параметр сведет к минимуму время сохранения и загрузки модели.|  
  
> [!NOTE]  
>  Изменения параметров модели по умолчанию не затронут свойства существующих моделей, созданных до внесения изменения.  
  
## <a name="see-also"></a>См. также:  
 [Свойства проекта &#40;табличные&#41;SSAS](properties-ssas-tabular.md)   
 [Свойства модели &#40;табличных&#41;SSAS](model-properties-ssas-tabular.md)   
 [Уровень совместимости &#40;табличных SP1 SSAS&#41;](compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  
