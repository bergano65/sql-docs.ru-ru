---
title: sys. systypes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.systypes_TSQL
- systypes_TSQL
- sys.systypes
- systypes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.systypes compatibility view
- systypes system table
ms.assetid: 1b0b1d0c-5f7b-470b-bd52-8bfa922d7889
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5533e521ba28c0190a5be57ed7637632213d7447
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68018080"
---
# <a name="syssystypes-transact-sql"></a>sys.systypes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по одной строке для каждого из системных и определяемых пользователем типов данных, определенных в базе данных.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя типа данных.|  
|**xtype**|**tinyint**|Тип физического хранилища.|  
|**состояние**|**tinyint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**xusertype**|**smallint**|Расширенный пользовательский тип. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**length**|**smallint**|Физическая длина типа данных.|  
|**xprec**|**tinyint**|Внутренняя точность, используемая сервером. Не для использования в запросах.|  
|**xscale**|**tinyint**|Внутренний масштаб, используемый сервером. Не для использования в запросах.|  
|**tdefault**|**int**|Идентификатор хранимой процедуры, содержащей проверку целостности для этого типа данных.|  
|**поддомен**|**int**|Идентификатор хранимой процедуры, содержащей проверку целостности для этого типа данных.|  
|**uid**|**smallint**|Идентификатор схемы владельца типа.<br /><br /> Для баз данных, обновленных из предыдущих версий [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Идентификатор схемы эквивалентен идентификатору владельца.<br /><br /> ** \* \* Важно \* !** При использовании любой из следующих [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] инструкций DDL необходимо использовать представление каталога [sys. types](../../relational-databases/system-catalog-views/sys-types-transact-sql.md) вместо **sys. systypes**.<br /><br /> ALTER AUTHORIZATION ON TYPE<br /><br /> CREATE TYPE<br /><br /> Вызывает переполнение или возвращает значение NULL, если количество пользователей и ролей превышает 32 767.|  
|**процессу**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**коллатионид**|**int**|Если на основе символов, **коллатионид** является идентификатором параметров сортировки текущей базы данных; в противном случае он имеет значение NULL.|  
|**usertype**|**smallint**|Идентификатор пользовательского типа. Вызывает переполнение или возвращает значение NULL, если количество типов данных превышает 32 767.|  
|**variable**|**bit**|Тип данных с переменной длиной.<br /><br /> 1 = True<br /><br /> 0 = False.|  
|**allownulls**|**bit**|Указывает для этого типа данных возможность принимать значения NULL по умолчанию. Это значение по умолчанию переопределяется, если допустимость значений NULL задана с помощью [CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md) или [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md).|  
|**type**|**tinyint**|Тип данных физического хранилища.|  
|**printfmt**|**varchar (255)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**прек**|**smallint**|Уровень точности для этого типа данных.<br /><br /> -1 = **XML** или типы больших значений.|  
|**Измените**|**tinyint**|Масштаб для этого типа данных на основе точности.<br /><br /> NULL = данные не числовые.|  
|**параметры сортировки**|**имеет sysname**|Если на основе символов **Параметры сортировки** являются параметрами сортировки текущей базы данных; в противном случае он имеет значение NULL.|  
  
## <a name="see-also"></a>См. также:  
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)  
  
  
