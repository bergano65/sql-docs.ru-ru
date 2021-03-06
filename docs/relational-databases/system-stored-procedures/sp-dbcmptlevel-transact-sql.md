---
title: sp_dbcmptlevel (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbcmptlevel
- sp_dbcmptlevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbcmptlevel
ms.assetid: 508c686d-2bd4-41ba-8602-48ebca266659
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0f6ffcb7a43fbfc2a840cbbbeb95de4bbb875cbe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108212"
---
# <a name="sp_dbcmptlevel-transact-sql"></a>sp_dbcmptlevel (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Определяет поведение конкретных баз данных для совместимости с указанной версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Используйте вместо него [уровень совместимости ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbcmptlevel [ [ @dbname = ] name ]   
    [ , [ @new_cmptlevel = ] version ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @dbname = ] name`Имя базы данных, для которой необходимо изменить уровень совместимости. Имена баз данных должны соответствовать правилам для идентификаторов. Аргумент *Name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @new_cmptlevel = ] version`Версия, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с которой должна быть совместима база данных. *версия* имеет тип **tinyint**и значение по умолчанию NULL. Это должно быть одно из следующих значений.  
  
 **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]  
  
 **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 **110** = [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
 **120** = [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
 **130** = [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Если параметры не указаны или параметр *Name* не указан, **sp_dbcmptlevel** возвращает ошибку.  
  
 Если *имя* указано без *версии*, то [!INCLUDE[ssDE](../../includes/ssde-md.md)] возвращается сообщение, отображающее текущий уровень совместимости указанной базы данных.  
  
## <a name="remarks"></a>Remarks  
 Описание уровней совместимости см. в разделе [уровень совместимости ALTER database &#40;&#41;Transact-SQL ](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только владелец базы данных, члены предопределенной роли сервера **sysadmin** и предопределенная роль базы данных **db_owner** (если вы изменяете текущую базу данных).  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [&#41;Transact-SQL ALTER DATABASE &#40;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Зарезервированные ключевые слова &#40;&#41;Transact-SQL](../../t-sql/language-elements/reserved-keywords-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
