---
title: sys. dm_os_memory_cache_clock_hands (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 783f985810b44673c6a6566caa6e89ff655670e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68265794"
---
# <a name="sysdm_os_memory_cache_clock_hands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает состояние каждой стрелки указанных часов кэша.  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] из [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]или, используйте имя **sys. dm_pdw_nodes_os_memory_cache_clock_hands**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|Адрес кэша, связанного с часами. Не допускает значение NULL.|  
|**name**|**nvarchar(256)**|Имя кэша. Не допускает значение NULL.|  
|**type**|**nvarchar (60)**|Тип кэша. Допускается наличие нескольких экземпляров кэша одного типа. Не допускает значение NULL.|  
|**clock_hand**|**nvarchar (60)**|Тип стрелки. Возможны следующие варианты.<br /><br /> Внешний<br /><br /> Внутренний<br /><br /> Не допускает значение NULL.|  
|**clock_status**|**nvarchar (60)**|Состояние часов. Возможны следующие варианты.<br /><br /> Suspended<br /><br /> Запущен<br /><br /> Не допускает значение NULL.|  
|**rounds_count**|**bigint**|Число проходов по кэшу для удаления элементов. Не допускает значение NULL.|  
|**removed_all_rounds_count**|**bigint**|Число элементов, удаленных при всех проходах. Не допускает значение NULL.|  
|**updated_last_round_count**|**bigint**|Число элементов, обновленных во время последнего прохода. Не допускает значение NULL.|  
|**removed_last_round_count**|**bigint**|Число элементов, удаленных во время последнего прохода. Не допускает значение NULL.|  
|**last_tick_time**|**bigint**|Время последнего перемещения стрелки часов (в миллисекундах). Не допускает значение NULL.|  
|**round_start_time**|**bigint**|Время предыдущего прохода (в миллисекундах). Не допускает значение NULL.|  
|**last_round_start_time**|**bigint**|Общее время выполнения предыдущего цикла часов (в миллисекундах). Не допускает значение NULL.|  
|**pdw_node_id**|**int**|**Применимо к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор узла, на котором находится данное распределение.|  
  
## <a name="permissions"></a>Разрешения  

В [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]необходимо `VIEW SERVER STATE` разрешение.   
На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Premium требуется `VIEW DATABASE STATE` разрешение в базе данных. На [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] уровнях Standard и Basic требуется **Администратор сервера** или учетная запись **администратора Azure Active Directory** .   
  
## <a name="remarks"></a>Remarks  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] хранит сведения в структуре памяти, которая называется кэшем памяти. В качестве сведений, хранящихся в этом кэше, могут выступать данные, индексные записи, скомпилированные планы выполнения процедур и множество других типов сведений [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Чтобы избежать повторного создания сведений, они извлекаются из кэша памяти возможное число раз и обычно удаляются из кэша в случае их сильного устаревания или в том случае, если область памяти требуется для записи новых данных. Процесс, который удаляет устаревшие сведения из памяти, называется «чистильщиком памяти». Чистильщик памяти используется регулярно, но не непрерывно. Очисткой кэша памяти управляет временной алгоритм. Каждый таймер времени временного алгоритма может управлять несколькими чистильщиками памяти, которые называются «руками». Рука таймера чистильщика времени — это текущее место расположения одной из рук чистильщика памяти.  

## <a name="see-also"></a>См. также:  
 [SQL Server динамические административные представления, связанные с операционной системой &#40;&#41;Transact-SQL](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys. dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

