---
title: MSsubscription_agents (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsubscription_agents
- MSsubscription_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsubscription_agents system table
ms.assetid: 86ad5891-0bef-4963-9381-7d5b45245a0c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3354f69f92cbbbaa9d60ae8ed6352a0b3be6ab52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139789"
---
# <a name="mssubscription_agents-transact-sql"></a>MSsubscription_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsubscription_agents** таблица используется агент распространения и триггерами обновляемых подписок для наблюдения за свойствами подписки. Эта таблица хранится в базе данных подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор строки.|  
|**издателя**|**имеет sysname**|Имя издателя.|  
|**publisher_db**|**имеет sysname**|Имя базы данных публикации.|  
|**публикации**|**имеет sysname**|Имя публикации.|  
|**subscription_type**|**int**|Тип подписки:<br /><br /> 0 = принудительная<br /><br /> 1 = по запросу;<br /><br /> 2 = анонимная по запросу.|  
|**queue_id**|**имеет sysname**|Идентификатор очереди [!INCLUDE[msCoName](../../includes/msconame-md.md)] сообщений на издателе. для *queue_id* задано значение **SQL** для обновления посредством очередей на основе SQL.|  
|**update_mode**|**tinyint**|Тип обновления:<br /><br /> **0** = только для чтения.<br /><br /> **1** = немедленное обновление.<br /><br /> **2** = обновление в очереди с помощью очереди сообщений.<br /><br /> **3** = немедленное обновление с очередью обновлений как отработка отказа с помощью очереди сообщений.<br /><br /> **4** = обновление в очереди с использованием очереди SQL Server.<br /><br /> **5** = немедленное обновление с отработкой отказа обновления посредством очередей с помощью очереди SQL Server.|  
|**failover_mode**|**bit**|Если выбрано обновление с отработкой отказа, может быть выбран следующий тип отработки отказа:<br /><br /> **0** = используется немедленное обновление. Отработка отказа не включена.<br /><br /> **1** = используется обновление в очереди. Отработка отказа включена. Очередь, используемая для отработки отказа, указывается в значении *update_mode* .|  
|**spid**|**int**|Идентификатор системного процесса для подключения, используемый агентом распространителя, выполняющимся в настоящее время или только что запущенным.|  
|**login_time**|**datetime**|Дата и время подключения агента распространителя, выполняющегося в настоящее время или только что запущенного.|  
|**allow_subscription_copy**|**bit**|Указывает, допускается ли возможность копирования базы данных подписки.|  
|**attach_state**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**attach_version**|**двоичный (16)**|Уникальный идентификатор, представляющий версию вложенной подписки.|  
|**last_sync_status**|**int**|Последнее состояние выполнения агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть:<br /><br /> **1** = запущено.<br /><br /> **2** = успех.<br /><br /> **3** = выполняется.<br /><br /> **4** = бездействие.<br /><br /> **5** = повторная попытка.<br /><br /> **6** = ошибка.|  
|**last_sync_summary**|**имеет sysname**|Последнее сообщение агента распространителя, выполняющегося в настоящее время или только что запущенного. Состояние может быть:<br /><br /> **Начинать.**<br /><br /> **Успешно.**<br /><br /> **Выполняется.**<br /><br /> **Выключен.**<br /><br /> **Повторите.**<br /><br /> **Cчетчик.**|  
|**last_sync_time**|**datetime**|Дата и время обновления столбцов *last_sync_summary* и *last_sync_status* . Агенты распространителя по запросу или анонимные, выполняющиеся как задания службы агента SqlServer, не обновляют эти столбцы. Вместо этого данные журнала заносятся в таблицу журнала заданий.|  
|**queue_server**|**имеет sysname**|Только для внутреннего применения.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helppullsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)  
  
  
