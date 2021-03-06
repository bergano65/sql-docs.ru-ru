---
title: fn_syscollector_get_execution_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_syscollector_get_execution_stats
- fn_syscollector_get_execution_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_syscollector_get_execution_stats function
ms.assetid: 793ad72c-a992-4a8d-8584-bcb6b3b476f1
author: rothja
ms.author: jroth
ms.openlocfilehash: 71a070de7c74d353be395628566c0bd3f63fd99a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68042742"
---
# <a name="fn_syscollector_get_execution_stats-transact-sql"></a>fn_syscollector_get_execution_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Возвращает подробную статистику о наборе элементов сбора или пакете, включая число ошибочных строк, зарегистрированных задачей потока данных пакета. Задача потока данных является компонентом служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], обрабатывающим данные. Эти данные имеют реляционный формат, поэтому данная задача имеет входные и выходные данные, состоящие из строк.  
  
 Статистика вычисляется по записям представления syscollector_execution_stats.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_syscollector_get_execution_stats ( log_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *log_id*  
 Локальный уникальный идентификатор для журнала выполнения. *log_id* имеет **тип int**.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|avg_row_count_in|**int**|Среднее количество строк, введенных задачами потока данных пакета.<br /><br /> Примечание. задача потока данных — это [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] компонент, обрабатывающий данные. Эти данные имеют реляционный формат, поэтому у данной задачи входной набор данных состоит из строк. Это строки, обрабатываемые задачей. После преобразования данных они выводятся в виде результирующего набора, состоящего из строк. Задача потока данных преобразует данные и выводит результирующий набор, состоящий из строк. Эти выходные данные — строки, вышедшие из задачи.|  
|min_row_count_in|**int**|Минимальное количество строк, введенных задачами потока данных пакета.|  
|max_row_count_in|**int**|Максимальное количество строк, введенных задачами потока данных пакета.|  
|avg_row_count_out|**int**|Среднее количество строк, выведенных задачами потока данных пакета.|  
|min_row_count_out|**int**|Минимальное количество строк, выведенных задачами потока данных пакета.|  
|max_row_count_out|**int**|Максимальное количество строк, выведенных задачами потока данных пакета.|  
|avg_duration|**int**|Среднее время (в миллисекундах), затраченное компонентом потока данных пакета.|  
|min_duration|**int**|Минимальное время (в миллисекундах), затраченное компонентом потока данных пакета.|  
|max_duration|**int**|Максимальное время (в миллисекундах), затраченное компонентом потока данных пакета.|  
  
## <a name="permissions"></a>Разрешения  
 Для **dc_operator**требуется SELECT.  
  
## <a name="see-also"></a>См. также:  
 [syscollector_execution_stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
