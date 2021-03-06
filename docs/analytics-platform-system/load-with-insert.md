---
title: Загрузка данных с помощью INSERT
description: Использование инструкции T-SQL INSERT для загрузки данных в распределенную или реплицированную таблицу параллельного хранилища данных (PDW).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: bbcf1a8bd16d7446841bb6d7dd86bd1ad350280d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401023"
---
# <a name="load-data-with-insert-into-parallel-data-warehouse"></a>Загрузка данных с помощью инструкции INSERT в хранилище Parallel Data Warehouse

Инструкцию TSQL INSERT можно использовать для загрузки данных в распределенную или реплицированную таблицу SQL Server Parallel Data Warehouse (PDW). Дополнительные сведения о INSERT см. в разделе [INSERT](../t-sql/statements/insert-transact-sql.md). Для реплицированных таблиц и всех столбцов, не относящихся к распространителю, в распределенной таблице PDW использует SQL Server для неявного преобразования значений данных, указанных в инструкции, в тип данных целевого столбца. Дополнительные сведения о правилах преобразования данных SQL Server см. в разделе [Преобразование типов данных для SQL](../t-sql/data-types/data-type-conversion-database-engine.md). Однако для столбцов распределения PDW поддерживает только подмножество неявных преобразований, поддерживаемых SQL Server. Поэтому при использовании инструкции INSERT для загрузки данных в столбец распределения исходные данные должны быть указаны в одном из форматов, определенных в следующих таблицах.  
  
  
## <a name="InsertingLiteralsBinary"></a>Вставка литералов в двоичные типы  
В следующей таблице определены допустимые типы литералов, формат и правила преобразования для вставки литерального значения в столбец распределения типа **binary** (*n*) или **varbinary**(*n*).  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Двоичный литерал|0x*hexidecimal_string*<br /><br />Пример: 0x12Ef|Двоичные литералы должны иметь префикс 0x.<br /><br />Длина источника данных не может превышать число байтов, указанное для данного типа данных.<br /><br />Если длина источника данных меньше, чем размер **двоичного** типа данных, то данные добавляются справа от нуля, чтобы достичь размера типа данных.|  
  
## <a name="InsertingLiteralsDateTime"></a>Вставка литералов в типы даты и времени  
Литералы даты и времени представлены с помощью символьных значений в конкретных форматах, заключенных в одинарные кавычки. В следующих таблицах определяются допустимые типы литералов, формат и правила преобразования для вставки литерала даты или времени в столбец распределения SQL Server PDW типа **DateTime**, **smalldatetime**, **Date**, **time**, **DateTimeOffset**или **datetime2**.  
  
### <a name="datetime-data-type"></a>тип данных даты и времени  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **DateTime**. Любая пустая строка ("") преобразуется в значение по умолчанию "1900-01-01 12:00:00.000". Строки, содержащие только пробелы (""), вызывают ошибку.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **DateTime**|"Гггг-мм-дд чч: мм: СС [. nnn]"<br /><br />Пример: "2007-05-08 12:35:29.123"|При вставке значения недостающие цифры задаются равными 0. Например, литерал "2007-05-08 12:35" вставляется как "2007-05-08 12:35:00.000".|  
|Строковый литерал в формате **smalldatetime**|' Гггг-мм-дд чч: мм '<br /><br />Пример: "2007-05-08 12:35"|Секунды и оставшиеся дробные цифры устанавливаются в 0 при вставке значения.|  
|Строковый литерал в формате **даты**|"ГГГГ-ММ-ДД"<br /><br />Пример: "2007-05-08"|Значения времени (часы, минуты, секунды и дроби) устанавливаются в значение 12:00:00.000 при вставке значения.|  
|Строковый литерал в формате **datetime2**|"Гггг-мм-дд чч: мм: СС. ннннннн"<br /><br />Пример: "2007-05-08 12:35:29.1234567"|Исходные данные не могут превышать три цифры дробной части. Например, литерал "2007-05-08 12:35:29.123" будет вставлен, но значение "2007-05-08 12:35:29.1234567" приведет к ошибке.|  
  
### <a name="smalldatetime-data-type"></a>smalldatetime - тип данных  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **smalldatetime**. Любая пустая строка ("") преобразуется в значение по умолчанию "1900-01-01 12:00". Строки, содержащие только пробелы (""), вызывают ошибку.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **smalldatetime**|"Гггг-мм-дд чч: мм" или "гггг-мм-дд чч: мм: 00"<br /><br />Пример: "2007-05-08 12:00" или "2007-05-08 12:00:00"|Исходные данные должны иметь значения "год", "месяц", "Дата", "час" и "минута". Секунды являются необязательными и, если они есть, должны быть установлены в значение 00. Любое другое значение приводит к ошибке.|  
|Строковый литерал в формате **даты**|"ГГГГ-ММ-ДД"<br /><br />Пример: "2007-05-08"|Значения времени (часы, минуты, секунды и дроби) устанавливаются в 0 при вставке значения.|  
  
### <a name="date-data-type"></a>тип данных даты  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **Date**. Любая пустая строка ("") преобразуется в значение по умолчанию "1900-01-01". Строки, содержащие только пробелы (""), вызывают ошибку.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **даты**|"ГГГГ-ММ-ДД"<br /><br />Пример: "2007-05-08"|Это единственный принятый формат.|  
  
### <a name="time-data-type"></a>тип данных времени  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **time**. Любая пустая строка ("") преобразуется в значение по умолчанию "00:00:00.0000". Строки, содержащие только пробелы (""), вызывают ошибку.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **времени**|"чч: мм: СС. ннннннн"<br /><br />Пример: "12:35:29.1234567"|Если значение в источнике данных меньше или равно точности (число цифр дробной части), чем точность типа данных **time** , данные добавляются справа от нуля. Например, литеральное значение "12:35:29.123" вставляется как "12:35:29.1230000".<br /><br />Значение с большей точностью, чем у целевого типа данных, отклоняется.|  
  
### <a name="datetimeoffset-data-type"></a>datetimeoffset - тип данных  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **DateTimeOffset** (*n*). Формат по умолчанию: "гггг-мм-дд чч: мм: СС. ннннннн {+ |-} чч: мм". Пустая строка ("") преобразуется в значение по умолчанию "1900-01-01 12:00:00.0000000 + 00:00". Строки, содержащие только пробелы (""), вызывают ошибку. Количество цифр дробной части зависит от определения столбца. Например, столбец, определенный как **DateTimeOffset** (2), будет содержать две дробные цифры.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **DateTime**|"Гггг-мм-дд чч: мм: СС [. nnn]"<br /><br />Пример: "2007-05-08 12:35:29.123"|Отсутствующие дробные цифры и значения смещения задаются в 0 при вставке значения. Например, литерал "2007-05-08 12:35:29.123" вставляется как "2007-05-08 12:35:29.1230000 + 00:00".|  
|Строковый литерал в формате **smalldatetime**|' Гггг-мм-дд чч: мм '<br /><br />Пример: "2007-05-08 12:35"|Секунды, оставшиеся цифры дробной части и значения смещения задаются равными 0 при вставке значения.|  
|Строковый литерал в формате **даты**|"ГГГГ-ММ-ДД"<br /><br />Пример: "2007-05-08"|Значения времени (часы, минуты, секунды и дроби) устанавливаются в 0 при вставке значения. Например, литерал "2007-05-08" вставляется как "2007-05-08 00:00:00.0000000 + 00:00".|  
|Строковый литерал в формате **datetime2**|"Гггг-мм-дд чч: мм: СС. ннннннн"<br /><br />Пример: "2007-05-08 12:35:29.1234567"|Исходные данные не могут превышать указанное количество долей секунды в столбце DateTimeOffset. Если источник данных имеет меньшее или равное количество долей секунды, то данные добавляются справа от нуля. Например, если тип данных — DateTimeOffset (5), литеральное значение "2007-05-08 12:35:29.123 + 12:15" вставляется как "12:35:29.12300 + 12:15".|  
|Строковый литерал в формате **DateTimeOffset**|"Гггг-мм-дд чч: мм: СС. ннннннн {+&#124;-} чч: мм"<br /><br />Пример: "2007-05-08 12:35:29.1234567 + 12:15"|Исходные данные не могут превышать указанное количество долей секунды в столбце DateTimeOffset. Если источник данных имеет меньшее или равное количество долей секунды, то данные добавляются справа от нуля. Например, если тип данных — DateTimeOffset (5), литеральное значение "2007-05-08 12:35:29.123 + 12:15" вставляется как "12:35:29.12300 + 12:15".|  
  
### <a name="datetime2-data-type"></a>datetime2 - тип данных  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **datetime2** (*n*). Формат по умолчанию: "гггг-мм-дд чч: мм: СС. ннннннн". Пустая строка ("") преобразуется в значение по умолчанию "1900-01-01 12:00:00". Строки, содержащие только пробелы (""), вызывают ошибку. Количество цифр дробной части зависит от определения столбца. Например, столбец, определенный как **datetime2** (2), будет содержать две дробные цифры.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в формате **DateTime**|"Гггг-мм-дд чч: мм: СС [. nnn]"<br /><br />Пример: "2007-05-08 12:35:29.123"|Доли секунды являются необязательными и задаются в 0 при вставке значения.<br /><br />Значение, которое содержит больше цифр дробной части, чем конечный тип данных, отклоняется.|  
|Строковый литерал в формате **smalldatetime**|' Гггг-мм-дд чч: мм '<br /><br />Пример: "2007-05-08 12"|При вставке значения необязательные секунды и оставшиеся десятичные цифры устанавливаются в 0.|  
|Строковый литерал в формате **даты**|"ГГГГ-ММ-ДД"<br /><br />Пример: "2007-05-08"|Значения времени (часы, минуты, секунды и дроби) устанавливаются в 0 при вставке значения. Например, литерал "2007-05-08" вставляется как "2007-05-08 12:00:00.0000000".|  
|Строковый литерал в формате **datetime2**|"Гггг-мм-дд чч: мм: СС: ннннннн"<br /><br />Пример: "2007-05-08 12:35:29.1234567"|Если источник данных содержит компоненты данных и времени, которые меньше или равны значению, указанному в **datetime2**(*n*), данные вставляются. в противном случае возникает ошибка.|  
  
## <a name="InsertLiteralsNumeric"></a>Вставка литералов в числовые типы  
В следующих таблицах определяются принятые форматы и правила преобразования для вставки литерального значения в SQL Server PDW столбец распределения, использующий числовой тип.  
  
### <a name="bit-data-type"></a>bit, тип данных  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **bit**. Пустая строка ("") или строка, содержащая только пробелы (""), преобразуются в 0.  
  
|Литеральный тип|format|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в **целочисленном** формате|"нннннннннн"<br /><br />Пример: "1" или "321"|Целочисленное значение, отформатированное в виде строкового литерала, не может содержать отрицательное значение. Например, значение "-123" приводит к ошибке.<br /><br />Значение, большее 1, преобразуется в 1. Например, значение "123" преобразуется в 1.|  
|Строковый литерал|"TRUE" или "FALSE"<br /><br />Пример: "true"|Значение "TRUE" преобразуется в 1; значение FALSE преобразуется в 0.|  
|Целочисленный литерал|nnnnnnnn<br /><br />Пример: 1 или 321|Значение, большее 1 или меньшее 0, преобразуется в 1. Например, значения 123 и-123 преобразуются в 1.|  
|Десятичный литерал|nnnnn. nnnn<br /><br />Пример: 1234,5678|Значение, большее 1 или меньшее 0, преобразуется в 1. Например, значения 123,45 и-123,45 преобразуются в 1.|  
  
### <a name="decimal-data-type"></a>тип данных decimal  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **Decimal** (*p, s*). Правила преобразования данных те же, что и для SQL Server. Дополнительные сведения см. в разделе [Преобразование типов данных](../t-sql/data-types/data-type-conversion-database-engine.md) в MSDN.  
  
|Литеральный тип|Формат|  
|----------------|----------|  
|Строковый литерал в **целочисленном** формате|"нннннннннннн"<br /><br />Пример: "321312313123"|  
|Строковый литерал в **десятичном** формате|"нннннн. nnnnn"<br /><br />Пример: "123344,34455"|  
|Целочисленный литерал|нннннннннннн<br /><br />Пример: 321312313123|  
|Десятичный литерал|нннннн. nnnnn<br /><br />Пример: "123344,34455"|  
  
### <a name="float-and-real-data-types"></a>типы данных float и Real  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **float** или **Real**. Правила преобразования данных те же, что и для SQL Server. Дополнительные сведения см. в разделе [Преобразование типов данных](../t-sql/data-types/data-type-conversion-database-engine.md) в MSDN.  
  
|Литеральный тип|Формат|  
|----------------|----------|  
|Строковый литерал в **целочисленном** формате|"нннннннннннн"<br /><br />Пример: "321312313123"|  
|Строковый литерал в **десятичном** формате|"нннннн. nnnnn"<br /><br />Пример: "123344,34455"|  
|Строковый литерал в формате **с плавающей запятой**|"n. Ннннне + NN"<br /><br />Пример: "3.12323 E + 14"|  
|Целочисленный литерал|нннннннннннн<br /><br />Пример: 321312313123|  
|Десятичный литерал|нннннн. nnnnn<br /><br />Пример: 123344,34455|  
|Литерал с плавающей запятой|n. Ннннне + NN<br /><br />Пример: 3.12323 E + 14|  
  
### <a name="int-bigint-tinyint-smallint-data-types"></a>типы данных int, bigint, tinyint, smallint  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **int**, **bigint**, **tinyint**или **smallint**. Источник данных не может превышать допустимый диапазон для данного типа данных. Например, диапазон для **tinyint** — от 0 до 255, а диапазон для **int** — от-2 147 483 648 до 2 147 483 647.  
  
|Тип литерала|Формат|Правила преобразования|  
|------------|------|----------------|
|Строковый литерал в **целочисленном** формате|"нннннннннннннн"<br /><br />Пример: "321312313123"| None |  
|Целочисленный литерал|нннннннннннннн<br /><br />Пример: 321312313123| None|  
|Десятичный литерал|нннннн. nnnnn<br /><br />Пример: 123344,34455|Значения справа от десятичной запятой усекаются.|  
  
### <a name="money-and-smallmoney-data-types"></a>типы данных money и smallmoney  
Литеральные значения денежных единиц представляются в виде чисел с необязательным десятичным разделителем и символом валюты в качестве префикса. Источник данных не может превышать допустимый диапазон для данного типа данных. Например, диапазон для **smallmoney** — от-214 748,3648 до 214 748,3647, а диапазон **денег** — от-922 337 203 685 477,5808 до 922 337 203 685 477,5807. В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **money** или **smallmoney**.  
  
|Литеральный тип|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал в **целочисленном** формате|nnnnnnnn<br /><br />Пример: "123433"|Отсутствующие цифры после десятичной запятой задаются равными 0 при вставке значения. Например, литерал "12345" вставляется как 12345,0000.|  
|Строковый литерал в **десятичном** формате|"нннннн. nnnnn"<br /><br />Пример: "123344,34455"|Если число цифр после десятичной запятой превышает 4, значение округляется до ближайшего значения. Например, значение "123344,34455" вставляется как 123344,3446.|  
|Строковый литерал в формате **money**|"$nnnnnn. nnnn"<br /><br />Пример: "$123456,7890"|Необязательный символ валюты не вставляется со значением.<br /><br />Если число цифр после десятичной запятой превышает 4, значение округляется до ближайшего значения.|  
|Целочисленный литерал|nnnnnnnn<br /><br />Пример: 123433|Отсутствующие цифры после десятичной запятой задаются равными 0 при вставке значения. Например, литерал 12345 вставляется как 12345,0000.|  
|Десятичный литерал|нннннн. nnnnn<br /><br />Пример: 123344,34455|Если число цифр после десятичной запятой превышает 4, значение округляется до ближайшего значения. Например, значение 123344,34455 вставляется как 123344,3446.|  
|Литерал денежной суммы|$nnnnnn. nnnn<br /><br />Пример: $123456,7890|Необязательный символ валюты не вставляется со значением.<br /><br />Если число цифр после десятичной запятой превышает 4, значение округляется до ближайшего значения.|  
  
## <a name="InsertLiteralsString"></a>Вставка литералов в строковые типы  
В следующих таблицах определяются принятые форматы и правила преобразования для вставки литерального значения в SQL Server PDW столбец, использующий строковый тип.  
  
### <a name="char-varchar-nchar-and-nvarchar-data-types"></a>типы данных char, varchar, nchar и nvarchar  
В следующей таблице определены допустимые форматы и правила вставки литеральных значений в столбец распределения типа **char**, **varchar**, **nchar** и **nvarchar**. Длина источника данных не может превышать размер, указанный для типа данных. Если длина источника данных меньше, чем размер типа данных **char** или **nchar** , то данные добавляются справа с пустыми пробелами для достижения размера типа данных.  
  
|Тип литерала|Формат|Правила преобразования|  
|----------------|----------|--------------------|  
|Строковый литерал|Формат: "строка символов"<br /><br />Пример: "ABC"| None|  
|Строковый литерал в Юникоде|Формат: Н'чарактер строка "<br /><br />Пример: Н'абк '|  None |  
|Целочисленный литерал|Формат: ннннннннннн<br /><br />Пример: 321312313123| None |  
|Десятичный литерал|Формат: нннннн. ннннннн<br /><br />Пример: 12344,34455| None |  
|Литерал денежной суммы|Формат: $nnnnnn. nnnnn<br /><br />Пример: $123456,99|Символ валюты не вставляется со значением. Чтобы вставить символ валюты, вставьте значение в виде строкового литерала. Это будет соответствовать формату инструмента **dwloader** , который обрабатывает каждый литерал как строковый литерал.<br /><br />Запятые не допускаются.<br /><br />Если число цифр после десятичной запятой превышает 2, значение округляется до ближайшего значения. Например, значение 123,946789 вставляется как 123,95.<br /><br />При использовании функции CONVERT для вставки литералов Money допускается только стиль по умолчанию 0 (без запятых и 2 цифр после десятичной запятой).|  

  
## <a name="see-also"></a>См. также:  
 
[Распределенные данные](https://azure.microsoft.com/documentation/articles/sql-data-warehouse-distributed-data/)  
[INSERT](../t-sql/statements/insert-transact-sql.md)  
  
<!-- MISSING LINKS
[Grant permissions to load data](grant-permissions-to-load-data.md)  
[Metadata query examples](metadata-query-examples.md) 
-->
