---
title: sys. dm_pdw_request_steps (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: cc563e88-0d34-436e-b914-b60d6ee0d50b
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 260b822d111f94fc567704cd908cb5632e3bdcaf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73240773"
---
# <a name="sysdm_pdw_request_steps-transact-sql"></a>sys. dm_pdw_request_steps (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит сведения обо всех шагах, составляющих данный запрос или запрос в [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]. В нем отображается одна строка для каждого шага запроса.  
  
|Имя столбца|Тип данных|Description|Диапазонный индекс|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar (32)**|request_id и step_index сделать ключ для этого представления.<br /><br /> Уникальный числовой идентификатор, связанный с запросом.|См. раздел request_id в [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|step_index|**int**|request_id и step_index сделать ключ для этого представления.<br /><br /> Расположение этого шага в последовательности шагов, составляющих запрос.|от 0 до (n – 1) для запроса с n шагами.|  
|operation_type|**nvarchar (35)**|Тип операции, представленной этим шагом.|**Операции с планом запросов DMS:** "ReturnOperation", "PartitionMoveOperation", "MoveOperation", "BroadcastMoveOperation", "ShuffleMoveOperation", "TrimMoveOperation", "CopyOperation", "Дистрибутерепликатедтаблемовеоператион"<br /><br /> **Операции плана запроса SQL:** "OnOperation", "RemoteOperation"<br /><br /> **Другие операции плана запроса:** "Метадатакреатеоператион", "Рандомидоператион"<br /><br /> **Внешние операции для операций чтения:** "Хадупшуффлеоператион", "Хадупраундробиноператион", "Хадупброадкастоператион"<br /><br /> **Внешние операции для MapReduce:** "Хадупжобоператион", "Хдфсделетеоператион"<br /><br /> **Внешние операции записи:** "Екстерналекспортдистрибутедоператион", "Екстерналекспортрепликатедоператион", "Екстерналекспортконтролоператион"<br /><br /> Дополнительные сведения см [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. в разделе «Основные сведения о планах запросов» в. <br /><br />  На план запроса также могут повлиять параметры базы данных.  Проверьте [Параметры ALTER DATABASE SET](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql-set-options?toc=/azure/sql-data-warehouse/toc.json&bc=/azure/sql-data-warehouse/breadcrumb/toc.json&view=azure-sqldw-latest) для получения дополнительных сведений.|  
|distribution_type|**nvarchar (32)**|Тип распространения, который будет подвергнут этому шагу.|"AllNodes", "Аллдистрибутионс", "Аллкомпутенодес", "ComputeNode", "Distribution", "Субсетнодес", "Distribution", "Unspecified"|  
|location_type|**nvarchar (32)**|Место выполнения шага.|"COMPUTE", "Control", "DMS"|  
|status|**nvarchar (32)**|Состояние этого шага.|Ожидание, выполнение, завершение, сбой, Ундофаилед, Пендингканцел, отменено, Отмена, прервано|  
|error_id|**nvarchar (36)**|Уникальный идентификатор ошибки, связанной с этим шагом, если таковой имеется.|См. раздел error_id из [sys. dm_pdw_errors &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md). Значение NULL, если ошибка не возникла.|  
|start_time|**datetime**|Время начала выполнения этапа.|Меньше или равно текущему времени и больше или равно end_compile_time запроса, к которому относится этот шаг. Дополнительные сведения о запросах см. в разделе [sys. dm_pdw_exec_requests &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-requests-transact-sql.md).|  
|end_time|**datetime**|Время, когда выполнение этого шага было завершено, было отменено или завершилось сбоем.|Меньше или равно текущему времени и больше или равно start_time. Задайте значение NULL для шагов, выполняемых в данный момент или в очереди.|  
|total_elapsed_time|**int**|Общее количество времени выполнения шага запроса (в миллисекундах).|Между 0 и разностью между end_time и start_time. 0 для шагов в очереди.<br /><br /> Если total_elapsed_time превышает максимальное значение для целого числа, total_elapsed_time будет продолжать быть максимальным значением. Это условие выдаст предупреждение "превышено максимальное значение".<br /><br /> Максимальное значение в миллисекундах эквивалентно 24,8 дням.|  
|row_count|**bigint**|Общее число строк, измененных или возвращенных этим запросом.|0 для шагов, которые не изменяют или возвращают данные. В противном случае число затронутых строк.|  
|command|**nvarchar (4000)**|Содержит полный текст команды этого шага.|Любая допустимая строка запроса для шага. Значение NULL, если операция имеет тип Метадатакреатеоператион. Усекается, если длиннее 4000 символов.|  
  
 Сведения о максимальном объеме строк, хранящихся в этом представлении, см [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]. в разделе Максимальное значение системного представления раздела "минимальное и максимальное значения" в.  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления хранилища данных SQL и параллельного хранилища данных &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
