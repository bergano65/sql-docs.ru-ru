---
title: sp_databases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_databases_TSQL
- sp_databases
dev_langs:
- TSQL
helpviewer_keywords:
- sp_databases
ms.assetid: 2a83b92a-9ecc-43c4-8ff4-e91e3a940b5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: c338fb8057c2d58727f18e0bb69e2fa825e71559
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108336"
---
# <a name="sp_databases-transact-sql"></a>sp_databases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Выдает список баз данных, которые размещаются в экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или доступны через шлюз базы данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_databases  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**DATABASE_NAME**|**имеет sysname**|Имя базы данных. [!INCLUDE[ssDE](../../includes/ssde-md.md)]В этот столбец представляет имя базы данных, хранящееся в представлении каталога **sys. databases** .|  
|**DATABASE_SIZE**|**int**|Размер базы данных в килобайтах.|  
|**Примечания**|**varchar (254)**|Для компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] это поле всегда возвращает значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 Возвращаемые имена баз данных могут использоваться в качестве параметров в инструкции USE для изменения текущего контекста базы данных.  
  
 **sp_databases** не имеет эквивалента в открытом подключении к базе данных (ODBC).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CREATE DATABASE, ALTER ANY DATABASE или VIEW ANY DEFINITION; кроме того, должно быть разрешение на доступ к базе данных. Разрешение VIEW ANY DEFINITION не может быть запрещено.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует выполнение процедуры `sp_databases`.  
  
```sql  
USE master;  
GO  
EXEC sp_databases;  
```  
  
## <a name="see-also"></a>См. также:  
 [sys. databases &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [HAS_DBACCESS &#40;Transact-SQL&#41;](../../t-sql/functions/has-dbaccess-transact-sql.md)  
  
  
