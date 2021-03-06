---
title: sysdac_history_internal (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdac_history_internal
- sysdac_history_internal_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysdac_history_internal
ms.assetid: 774a1678-0b27-42be-8adc-a6d7a4a56510
author: stevestein
ms.author: sstein
ms.openlocfilehash: cc058fea8e2ce86584c19a7a93018734f4782f69
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084763"
---
# <a name="data-tier-application-tables---sysdac_history_internal"></a>Таблицы приложений уровня данных — sysdac_history_internal
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения о действиях, предпринятых для управления приложениями уровня данных (DAC). Эта таблица хранится в схеме **dbo** базы данных **msdb** .  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**action_id**|**int**|Идентификатор действия|  
|**sequence_id**|**int**|Идентифицирует шаг действия.|  
|**instance_id**|**UNIQUEIDENTIFIER**|Идентификатор экземпляра DAC. Этот столбец может быть присоединен к столбцу **instance_id** в [dbo. sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md).|  
|**action_type**|**tinyint**|Идентификатор типа действия:<br /><br /> **0** = развернуть<br /><br /> **1** = создать<br /><br /> **2** = переименовать<br /><br /> **3** = отсоединить<br /><br /> **4** = удалить|  
|**action_type_name**|**varchar (19)**|Имя типа действия:<br /><br /> **повторно**<br /><br /> **создания**<br /><br /> **имени**<br /><br /> **соединил**<br /><br /> **удален**|  
|**dac_object_type**|**tinyint**|Идентификатор типа объекта, на который влияет действие:<br /><br /> **0** = DACPAC<br /><br /> **1** = имя входа<br /><br /> **2** = база данных|  
|**dac_object_type_name**|**varchar (8)**|Имя типа объекта, на который влияет действие:<br /><br /> **DACPAC** = экземпляр DAC<br /><br /> **пользователей**<br /><br /> **database**|  
|**action_status**|**tinyint**|Код, отображающий текущее состояние действия:<br /><br /> **0** = ожидание<br /><br /> **1** = успешное завершение<br /><br /> **2** = сбой|  
|**action_status_name**|**varchar (11)**|Текущее состояние действия:<br /><br /> **состоянии**<br /><br /> **загрузоч**<br /><br /> **Cчетчик**|  
|**Обязательно**|**bit**|Используется компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] при откате операции DAC.|  
|**dac_object_name_pretran**|**имеет sysname**|Имя объекта до транзакции, содержащей действие, выделено. Используется только для баз данных и имен входа.|  
|**dac_object_name_posttran**|**имеет sysname**|Имя объекта после транзакции, содержащей действие, выделено. Используется только для баз данных и имен входа.|  
|**sqlscript**|**nvarchar(max)**|Скрипт [!INCLUDE[tsql](../../includes/tsql-md.md)], выполняющий действие над базой данных или именем входа.|  
|**полезных данных**|**varbinary(max)**|Определение пакета DAC, сохраненное в строке, закодированной двоичным кодом.|  
|**Комментарии**|**varchar(max)**|Записывает имя входа пользователя, который подтвердил свое согласие с возможной потерей данных при обновлении DAC.|  
|**error_string**|**nvarchar(max)**|Если действие выполняется с ошибкой, выдается сообщение.|  
|**created_by**|**имеет sysname**|Имя входа, запустившее действие, создавшее данную запись.|  
|**date_created**|**datetime**|Дата и время создания записи.|  
|**date_modified**|**datetime**|Дата и время последнего изменения записи.|  
  
## <a name="remarks"></a>Remarks  
 Управляющие действия DAC, такие как развертывание или удаление DAC, создают несколько этапов. Каждому из действий присваивается идентификатор действия. Каждому шагу присваивается порядковый номер и строка в **sysdac_history_internal**, где записывается состояние шага. Каждая строка создается при запуске этапа действия и обновляется по мере необходимости для отражения состояния операции. Например, действие Deploy DAC может быть назначено **action_id** 12 и получать четыре строки в **sysdac_history_internal**:  
  
|||||  
|-|-|-|-|  
|**action_id**|**sequence_id**|**action_type_name**|**dac_object_type_name**|  
|12|0|create|пакет DAC|  
|12|1|create|login|  
|12|2|create|База данных|  
|12|3|переименовать|База данных|  
  
 Операции DAC, такие как DELETE, не удаляют строки из **sysdac_history_internal**. Можно выполнить следующий запрос, чтобы вручную удалить строки для тех DAC, которые больше не развернуты в экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)]:  
  
```sql  
DELETE FROM msdb.dbo.sysdac_history_internal  
WHERE instance_id NOT IN  
   (SELECT instance_id  
    FROM msdb.dbo.sysdac_instances_internal);  
```  
  
 Удаление строк для активных DAC не влияет на операции DAC, за исключением того, что у вас не будет полного журнала для DAC.  
  
> [!NOTE]  
>  В настоящее время отсутствует механизм удаления **sysdac_history_internal** строк [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)].  
  
## <a name="permissions"></a>Разрешения  
 Требует членства в предопределенной роли сервера sysadmin. Доступ только для чтения к этому представлению доступен всем пользователям с разрешениями на подключение к базе данных master.  
  
## <a name="see-also"></a>См. также:  
 [Приложения уровня данных](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [dbo. sysdac_instances &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-tier-application-views-dbo-sysdac-instances.md)   
 [sysdac_instances_internal &#40;Transact-SQL&#41;](../../relational-databases/system-tables/data-tier-application-tables-sysdac-instances-internal.md)  
  
  
