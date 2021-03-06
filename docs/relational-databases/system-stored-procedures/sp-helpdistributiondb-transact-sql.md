---
title: sp_helpdistributiondb (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributiondb_TSQL
- sp_helpdistributiondb
helpviewer_keywords:
- sp_helpdistributiondb
ms.assetid: a2917020-26d1-4011-99f8-9212d120fd2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 90dee1076743ae54201248c808b04c6197d42198
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68770934"
---
# <a name="sp_helpdistributiondb-transact-sql"></a>sp_helpdistributiondb (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает свойства указанной базы данных распространителя. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistributiondb [ [ @database= ] 'database_name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @database = ] 'database_name'`Имя базы данных, для которой возвращаются свойства. Аргумент *database_name* имеет тип **sysname**и значение по **%** умолчанию для всех баз данных, связанных с распространителем, и у пользователя есть разрешения.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя базы данных распространителя.|  
|**min_distretention**|**int**|Минимальный срок хранения транзакций перед удалением (в часах).|  
|**max_distretention**|**int**|Максимальный срок хранения транзакций перед удалением (в часах).|  
|**history retention**|**int**|Количество часов, в течение которых будет храниться журнал.|  
|**history_cleanup_agent**|**имеет sysname**|Имя агента очистки журнала.|  
|**distribution_cleanup_agent**|**имеет sysname**|Имя агента очистки распространителя.|  
|**состояние**|**int**|Только для внутреннего применения.|  
|**data_folder**|**nvarchar(255)**|Имя каталога, используемого для хранения файлов базы данных.|  
|**data_file**|**nvarchar(255)**|Имя файла базы данных.|  
|**data_file_size**|**int**|Исходный размер файла данных в мегабайтах.|  
|**log_folder**|**nvarchar(255)**|Имя каталога, в котором размещается файл журнала базы данных.|  
|**log_file**|**nvarchar(255)**|Имя файла журнала.|  
|**log_file_size**|**int**|Исходный размер файла журнала в мегабайтах.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpdistributiondb** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Члены предопределенной роли базы данных **db_owner** или роли **replmonitor** в базе данных распространителя и пользователи из списка доступа к публикации публикации с помощью базы данных распространителя могут выполнять **sp_helpdistributiondb** для возврата сведений, относящихся к файлу. Члены роли **Public** могут выполнять **sp_helpdistributiondb** для возврата сведений, не относящихся к файлам, для баз данных распространителя, к которым у них есть доступ.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств распространителя и издателя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [sp_adddistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql.md)   
 [sp_changedistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
