---
title: DB_NAME (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DB_NAME
- DB_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- database names [SQL Server], DB_NAME
- names [SQL Server], databases
- viewing database names
- displaying database names
- DB_NAME function
ms.assetid: e21fb33a-a3ea-49b0-bb6b-8f789a675a0e
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5aa5e2a60189a82fb60cd416b7f87b35824e236f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68118982"
---
# <a name="db_name-transact-sql"></a>DB_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

Эта функция возвращает имя указанной базы данных.
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DB_NAME ( [ database_id ] )  
```  
  
## <a name="arguments"></a>Аргументы  
*database_id*  

Идентификационный номер базы данных, имя которой вернет функция `DB_NAME`. Если в вызове `DB_NAME` аргумент *database_id* не указан, функция `DB_NAME` возвращает имя текущей базы данных.
  
## <a name="return-types"></a>Типы возвращаемых данных
**nvarchar(128)**
  
## <a name="permissions"></a>Разрешения  

Если участник, вызывающий `DB_NAME`, не является владельцем конкретной базы данных, отличной от базы данных **master** или **tempdb**, то минимальными разрешениями, необходимыми для просмотра соответствующей строки `ALTER ANY DATABASE`, являются разрешения уровня сервера `VIEW ANY DATABASE` или `DB_ID`. Для базы данных **master** функция `DB_ID` требует по крайней мере разрешения `CREATE DATABASE`. База данных, к которой подключается вызывающий участник, всегда отображается в представлении **sys.databases**.
  
> [!IMPORTANT]  
>  По умолчанию общедоступная роль имеет разрешение `VIEW ANY DATABASE`, что позволяет всем именам для входа просматривать информацию в базе данных. Чтобы имя для входа не могло обнаруживать базу данных, отзовите общедоступное разрешение `REVOKE` с помощью инструкции `VIEW ANY DATABASE` или отмените разрешение `DENY` для отдельных имен для входа с помощью инструкции `VIEW ANY DATABASE`.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-current-database-name"></a>A. Возврат имени текущей базы данных  
В приведенном ниже примере возвращается имя текущей базы данных.
  
```sql
SELECT DB_NAME() AS [Current Database];  
GO  
```  
  
### <a name="b-returning-the-database-name-of-a-specified-database-id"></a>Б. Возврат имени базы данных с указанным идентификатором базы данных  
В приведенном ниже примере возвращается имя базы данных с идентификатором `3`.
  
```sql
USE master;  
GO  
SELECT DB_NAME(3)AS [Database Name];  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-return-the-current-database-name"></a>В. Получение имени текущей базы данных  
  
```sql
SELECT DB_NAME() AS [Current Database];  
```  
  
### <a name="d-return-the-name-of-a-database-by-using-the-database-id"></a>Г. Получение имени базы данных по ее идентификатору  
В приведенном ниже примере возвращаются имя и идентификатор каждой базы данных.
  
```sql
SELECT DB_NAME(database_id) AS [Database], database_id  
FROM sys.databases;  
```  
  
## <a name="see-also"></a>См. также раздел
[DB_ID (Transact-SQL)](../../t-sql/functions/db-id-transact-sql.md)  
[Функции метаданных (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)  
[sys.databases (Transact-SQL)](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)
  
  

