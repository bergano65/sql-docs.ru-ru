---
title: sys. server_audit_specification_details (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 04/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_audit_specification_details
- sys.server_audit_specification_details_TSQL
- server_audit_specification_details_TSQL
- sys.server_audit_specification_details
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_audit_specification_details catalog view
ms.assetid: 792724dc-402e-4b17-9f2c-029d910bf88e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43f5a4ca7dbad88fe98734576fd23368cc280fa2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68125022"
---
# <a name="sysserver_audit_specification_details-transact-sql"></a>sys.server_audit_specification_details (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит сведения об элементах (действиях) спецификации аудита сервера в подсистеме аудита [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на экземпляре сервера. Дополнительные сведения см. в статье [Подсистема аудита SQL Server (ядро СУБД)](../../relational-databases/security/auditing/sql-server-audit-database-engine.md). Чтобы получить список всех audit_action_id и их имена, запросите представление [sys. dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|server_specification_id|**int**|Идентификатор спецификации аудита сервера|  
|audit_action_id|**int**|Идентификатор действия аудита|  
|audit_action_name|**имеет sysname**|Имя группы или имя действия аудита|  
|класс|**tinyint**|Reserved|  
|class_desc|**nvarchar (60)**|Reserved|  
|major_id|**int**|Reserved|  
|minor_id|**int**|Reserved|  
|audited_principal_id|**int**|Reserved|  
|audited_result|**nvarchar (60)**|Результат аудита:<br /><br /> - SUCCESS AND FAILURE<br /><br /> - SUCCESS<br /><br /> - FAILURE|  
|is_group|**bit**|Является ли группой объект, прошедший аудит:<br /><br /> 0 — не группа;<br /><br /> 1 — группа.|  
  
## <a name="permissions"></a>Разрешения  
 Участники с разрешением **ALTER ANY SERVER AUDIT** или **View ANY DEFINITION** имеют доступ к этому представлению каталога. Кроме того, участнику не должно быть запрещено разрешение **View ANY DEFINITION** .  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога безопасности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [Создание аудита сервера &#40;Transact-SQL&#41;](../../t-sql/statements/create-server-audit-transact-sql.md)   
 [ALTER SERVER AUDIT &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-audit-transact-sql.md)   
 [Удаление аудита сервера &#40;Transact-SQL&#41;](../../t-sql/statements/drop-server-audit-transact-sql.md)   
 [Создание спецификации аудита сервера &#40;&#41;Transact-SQL](../../t-sql/statements/create-server-audit-specification-transact-sql.md)   
 [ALTER SERVER AUDIT SPECIFICATION &#40;&#41;Transact-SQL](../../t-sql/statements/alter-server-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИю аудита сервера &#40;&#41;Transact-SQL](../../t-sql/statements/drop-server-audit-specification-transact-sql.md)   
 [Создание спецификации аудита базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/create-database-audit-specification-transact-sql.md)   
 [&#40;Transact-SQL&#41;спецификации ALTER DATABASE AUDIT](../../t-sql/statements/alter-database-audit-specification-transact-sql.md)   
 [УДАЛИТЬ СПЕЦИФИКАЦИю аудита базы данных &#40;&#41;Transact-SQL](../../t-sql/statements/drop-database-audit-specification-transact-sql.md)   
 [ALTER AUTHORIZATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-authorization-transact-sql.md)   
 [sys. fn_get_audit_file &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-get-audit-file-transact-sql.md)   
 [sys. server_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audits-transact-sql.md)   
 [sys. server_file_audits &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-file-audits-transact-sql.md)   
 [sys. server_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-audit-specifications-transact-sql.md)   
 [sys. database_audit_specifications &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specifications-transact-sql.md)   
 [sys. database_audit_specification_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-audit-specification-details-transact-sql.md)   
 [sys. dm_server_audit_status &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-audit-status-transact-sql.md)   
 [sys. dm_audit_actions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-actions-transact-sql.md)   
 [sys. dm_audit_class_type_map &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-audit-class-type-map-transact-sql.md)   
 [Создание аудита сервера и спецификации аудита сервера](../../relational-databases/security/auditing/create-a-server-audit-and-server-audit-specification.md)  
  
  
