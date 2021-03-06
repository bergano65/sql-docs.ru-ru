---
title: sp_refresh_log_shipping_monitor (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_refresh_log_shipping_monitor
- sp_refresh_log_shipping_monitor_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_refresh_log_shipping_monitor
ms.assetid: edefb912-31c5-4d99-9aba-06629afd0171
author: stevestein
ms.author: sstein
ms.openlocfilehash: c19f9b99173ca04e6ce15862e22a25f8a2bf06e5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68002507"
---
# <a name="sp_refresh_log_shipping_monitor-transact-sql"></a>sp_refresh_log_shipping_monitor (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данная хранимая процедура обновляет удаленные таблицы мониторинга последними данными с указанного сервера-источника или сервера-получателя для указанного агента отправки журналов. Эта процедура запускается только на сервере-источнике или сервере-получателе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_refresh_log_shipping_monitor  
[ @agent_id = ] 'agent_id',  
[ @agent_type = ] 'agent_type'  
[ @database = ] 'database'  
[ @mode ] n  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @agent_id = ] 'agent_id'`Основной идентификатор резервной копии или вторичный идентификатор для копирования или восстановления. *agent_id* имеет тип **uniqueidentifier** и не может иметь значение null.  
  
`[ @agent_type = ] 'agent_type'`Тип задания доставки журналов.  
  
 0 = резервирование;  
  
 1 = копирование;  
  
 2 = восстановление.  
  
 *agent_type* имеет тип **tinyint** и не может иметь значение null.  
  
`[ @database = ] 'database'`Первичная или вторичная база данных, используемая для ведения журнала агентами резервного копирования или восстановления.  
  
`[ @mode ] n`Указывает, следует ли обновлять данные монитора или очищать их. Тип данных *m* — tinyint, а поддерживаемые значения:  
  
 1 = обновление (значение по умолчанию);  
  
 2 = удаление (delete);  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Нет.  
  
## <a name="remarks"></a>Remarks  
 **sp_refresh_log_shipping_monitor** обновляет таблицы **log_shipping_monitor_primary**, **log_shipping_monitor_secondary**, **log_shipping_monitor_history_detail**и **log_shipping_monitor_error_detail** с использованием сведений о сеансе, которые еще не были переданы. Это позволяет синхронизировать сервер мониторинга с сервером-источником или сервером-получателем, если в течение некоторого времени синхронизация не выполнялась. В дополнение к этому в случае необходимости разрешается очистка контрольных данных на сервере мониторинга.  
  
 **sp_refresh_log_shipping_monitor** должны запускаться из базы данных **master** на основном или вторичном сервере.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
