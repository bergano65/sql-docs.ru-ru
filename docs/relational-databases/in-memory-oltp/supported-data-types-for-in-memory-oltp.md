---
title: Поддерживаемые типы данных для выполняющейся в памяти OLTP | Документация Майкрософт
ms.custom: ''
ms.date: 06/19/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: daa05543715f81511aa0faa8467fc78819999404
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68075892"
---
# <a name="supported-data-types-for-in-memory-oltp"></a>Поддерживаемые типы данных для выполняющейся в памяти OLTP
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  В этой статье перечислены типы данных, которые не поддерживаются для компонентов выполняющейся в памяти OLTP:  
  
-   Таблицы, оптимизированные для памяти  
  
-   Модули, скомпилированные в собственном коде T-SQL  
  
## <a name="unsupported-data-types"></a>Неподдерживаемые типы данных  
 Следующие типы данных не поддерживаются:  
  
||||  
|-|-|-|  
|[datetimeoffset (Transact-SQL)](../../t-sql/data-types/datetimeoffset-transact-sql.md)|[geography (Transact-SQL)](../../t-sql/spatial-geography/spatial-types-geography.md)|[geometry (Transact-SQL)](../../t-sql/spatial-geometry/spatial-types-geometry-transact-sql.md)|  
|[hierarchyid (Transact-SQL)](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)|[rowversion (Transact-SQL)](../../t-sql/data-types/rowversion-transact-sql.md)|[xml (Transact-SQL)](../../t-sql/xml/xml-transact-sql.md)|  
|[sql_variant (Transact-SQL)](../../t-sql/data-types/sql-variant-transact-sql.md)|Определяемые пользователем типы|.|  
  
## <a name="notable-supported-data-types"></a>Важные поддерживаемые типы данных  
 Большинство типов данных поддерживаются компонентами выполняющейся в памяти OLTP. Обратите внимание на следующие компоненты:  
  
|Строковые и двоичные типы|Дополнительные сведения|  
|-----------------------------|--------------------------|  
|binary и varbinary*|[binary и varbinary (Transact-SQL)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)|  
|char и varchar*|[char и varchar (Transact-SQL)](../../t-sql/data-types/char-and-varchar-transact-sql.md)|  
|nchar и nvarchar*|[nchar и nvarchar (Transact-SQL)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)|  
  
Для предшествующих строковых и двоичных типов данных, начиная с SQL Server 2016:  
  
- Отдельная оптимизированная для памяти таблица может также содержать несколько столбцов типа long, например `nvarchar(4000)`, даже если их совокупная длина превысит размер физической строки 8060 байт.  
  
- Оптимизированная для памяти таблица может содержать строковые и двоичные столбцы с максимальной длиной таких типов данных, например `varchar(max)`.  


### <a name="identify-lobs-and-other-columns-that-are-off-row"></a>Определение LOB-столбцов и других столбцов вне строки

Начиная с SQL Server 2016, оптимизированные для памяти таблицы поддерживают [хранение столбцов вне строки](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md), что позволяет одной табличной строке иметь размер более 8060 байт. Следующая инструкция Transact-SQL SELECT возвращает все столбцы вне строки для таблиц, оптимизированных для памяти. Обратите внимание на следующее.

- Все ключевые столбцы индекса сохранены в строке.
  - Теперь ключи неуникальных индексов могут включать столбцы со значениями NULL в таблицах, оптимизированных для памяти.
  - Индексы могут быть объявлены как UNIQUE для таблицы, оптимизированной для памяти.
- Все столбцы LOB хранятся вне строки.
- max_lengthax_length со значением -1 означает столбец большого объекта (LOB).


```sql
SELECT
        OBJECT_NAME(m.object_id) as [table],
        c.name                   as [column],
        c.max_length
    FROM
             sys.memory_optimized_tables_internal_attributes AS m
        JOIN sys.columns                                     AS c
                ON  m.object_id = c.object_id
                AND m.minor_id  = c.column_id
    WHERE
        m.type = 5;
```


### <a name="other-data-types"></a>Прочие типы данных


|Другие типы|Дополнительные сведения|  
|-----------------|--------------------------|  
|табличные типы|[Основные сведения о табличных переменных, оптимизированных для памяти](../../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)|  
  
## <a name="see-also"></a>См. также:  
 [Поддержка Transact-SQL для In-Memory OLTP](../../relational-databases/in-memory-oltp/transact-sql-support-for-in-memory-oltp.md)   
 [Реализация SQL_VARIANT в таблице, оптимизированной для памяти](../../relational-databases/in-memory-oltp/implementing-sql-variant-in-a-memory-optimized-table.md)  
 [Размер строки и таблицы для таблиц, оптимизированных для памяти](../../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)  
  
  
