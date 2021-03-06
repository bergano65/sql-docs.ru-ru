---
title: Системные базовые таблицы | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- system base tables [SQL Server]
- hobt [SQL Server]
- base tables
ms.assetid: 31f2df90-651f-4699-8067-19f59b60904f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 43f5e96a280614d3f69472c7d794489bf1a5ba58
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68029557"
---
# <a name="system-base-tables"></a>Системные базовые таблицы
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Системные базовые таблицы — это основные таблицы, в которых хранятся метаданные определенной базы данных. В этом отношении база данных **master** является особой, так как она содержит некоторые дополнительные таблицы, не найденные в других базах данных. Эти таблицы содержат устойчивые метаданные, областью которых является весь сервер.  
  
> [!IMPORTANT]  
>  Системные базовые таблицы используются только компонентом [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] и не предназначены для большинства пользователей. Они подвержены изменению, и совместимость не гарантируется.  
  
## <a name="system-base-table-metadata"></a>Метаданные системной базовой таблицы  
 Участник, имеющий разрешение CONTROL, ALTER или VIEW DEFINITION на базу данных, может видеть метаданные системной базовой таблицы в представлении каталога **sys. Objects** . Получатель прав может также разрешить имена и идентификаторы объектов системных базовых таблиц с помощью встроенных функций, таких как [object_name](../../t-sql/functions/object-name-transact-sql.md) и [object_id](../../t-sql/functions/object-id-transact-sql.md).  
  
 Чтобы открыть системную базовую таблицу, необходимо подключиться к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] через выделенное административное соединение (dedicated administrative connection, DAC). При попытке выполнить запрос SELECT из системной базовой таблицы без DAC-соединения выдается сообщение об ошибке.  
  
> [!IMPORTANT]  
>  Доступ к системным базовым таблицам с помощью DAC предназначен [!INCLUDE[msCoName](../../includes/msconame-md.md)] только для персонала и не является поддерживаемым сценарием клиента.  
  
## <a name="system-base-tables"></a>Системные базовые таблицы  
 Следующая таблица содержит имена и описания всех системных базовых таблиц в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
|Базовая таблица|Description|  
|----------------|-----------------|  
|**sys.sysschobjs**|Существует в каждой базе данных. Каждая строка представляет объект базы данных.|  
|**sys.sysbinobjs**|Существует в каждой базе данных. Содержит по строке на каждую сущность компонента Service Broker в базе данных. К компонентам Service Broker относятся:<br /><br /> тип сообщений;<br /><br /> контракт службы;<br /><br /> Служба<br /><br /> Для списка имен и типов используется фиксированная двоичная сортировка.|  
|**sys.sysclsobjs**|Существует в каждой базе данных. Содержит по строке на каждую сущность с общими свойствами, включая следующие:<br /><br /> Сборка<br /><br /> устройство резервного копирования;<br /><br /> Полнотекстовый каталог<br /><br /> Функция секционирования<br /><br /> Схема секционирования<br /><br /> файловая группа;<br /><br /> ключ запутывания.|  
|**sys.sysnsobjs**|Существует в каждой базе данных. Содержит по строке на каждую сущность, действующую в пространстве имен. Эта таблица используется для хранения сущностей XML-коллекции.|  
|**sys.syscolpars**|Существует в каждой базе данных. Содержит по строке на каждый столбец таблицы, представления или табличной функции. Cодержит также по строке на каждый параметр процедуры или функции.|  
|**sys.systypedsubobjs**|Существует в каждой базе данных. Содержит по строке на каждую типизированную вложенную сущность. К этой категории относятся только параметры функции секционирования.|  
|**sys.sysidxstats**|Существует в каждой базе данных. Содержит по строке на каждый индекс или статистику для таблиц и индексированных представлений.<br /><br /> Примечание. Каждый индекс (кроме кучи) связан с статистикой, имя которой совпадает с именем индекса.|  
|**sys.sysiscols**|Существует в каждой базе данных. Содержит по строке на каждый материализованный столбец индекса или статистики.|  
|**sys.sysscalartypes**|Существует в каждой базе данных. Содержит по строке на каждый системный или пользовательский тип данных.|  
|**sys.sysdbreg**|Существует только в базе данных **master** . Содержит по строке на каждую зарегистрированную базу данных.|  
|**sys.sysxsrvs**|Существует только в базе данных **master** . Содержит по строке на каждый локальный, связанный или удаленный сервер.|  
|**sys.sysrmtlgns**|Эта системная базовая таблица существует только в базе данных **master** . Содержит по строке на каждое сопоставление удаленного имени входа. Используется для сопоставления имен входа, предположительно поступивших с соответствующего сервера, с действительным локальным именем входа.|  
|**sys.syslnklgns**|Существует только в базе данных **master** . Содержит по строке на каждое сопоставление связанных имен входа. Сопоставления связанных имен входа используются для удаленного вызова процедур или распределенных запросов, идущих от локального сервера к соответствующему связанному серверу.|  
|**sys.sysxlgns**|Существует только в базе данных **master** . Содержит по строке на каждый зарегистрированный участник на уровне сервера.|  
|**sys.sysdbfiles**|Существует в каждой базе данных. Если столбец **DBID** равен нулю, строка представляет файл, принадлежащий этой базе данных. В базе данных **master** столбец **DBID** может быть ненулевым. В этом случае строка представляет главный файл.|  
|**sys.sysusermsg**|Существует только в базе данных **master** . Каждая строка представляет сообщение об ошибке, заданное пользователем.|  
|**sys.sysprivs**|Существует в каждой базе данных. Содержит по строке на каждое разрешение на уровне базы данных или сервера.<br /><br /> Примечание. разрешения уровня сервера хранятся в базе данных **master** .|  
|**sys.sysowners**|Существует в каждой базе данных. Каждая строка соответствует участнику базы данных.|  
|**sys.sysobjkeycrypts**|Существует в каждой базе данных. Содержит по строке на каждый симметричный ключ, шифр и криптографическое свойство, связанное с объектом.|  
|**sys.syscerts**|Существует в каждой базе данных. Содержит по строке на каждый сертификат в базе данных.|  
|**sys.sysasymkeys**|Существует в каждой базе данных. Каждая строка представляет асимметричный ключ.|  
|**sys.ftinds**|Существует в каждой базе данных. Содержит по строке на каждый полнотекстовый индекс в базе данных.|  
|**sys.sysxprops**|Существует в каждой базе данных. Содержит по строке на каждое расширенное свойство.|  
|**sys.sysallocunits**|Существует в каждой базе данных. Содержит по строке на каждую единицу распределения памяти.|  
|**sys.sysrowsets**|Существует в каждой базе данных. Содержит по строке на каждый набор строк секции для индекса или кучи.|  
|**sys.sysrowsetrefs**|Существует в каждой базе данных. Содержит по строке для каждой ссылки индекса на набор строк.|  
|**sys.syslogshippers**|Существует только в базе данных **master** . Содержит по строке на каждый сервер, следящий за зеркальным отображением базы данных.|  
|**sys.sysremsvcbinds**|Существует в каждой базе данных. Содержит по строке на каждую привязку удаленной службы.|  
|**sys.sysconvgroup**|Существует в каждой базе данных. Содержит по строке на каждый экземпляр службы в Service Broker.|  
|**sys.sysxmitqueue**|Существует в каждой базе данных. Содержит по строке на каждую очередь передачи в Service Broker.|  
|**sys.sysdesend**|Существует в каждой базе данных. Содержит по строке на каждую передающей конечную точку диалога Service Broker.|  
|**sys.sysdercv**|Существует в каждой базе данных. Содержит по одной строке на каждую принимающую конечную точку диалога Service Broker.|  
|**sys.sysendpts**|Существует только в базе данных **master** . Содержит по строке на каждую конечную точку, созданную на сервере.|  
|**sys.syswebmethods**|Существует только в базе данных **master** . Содержит по строке на каждый метод SOAP, заданный в конечной точке HTTP с поддержкой протокола SOAP, которая создана на сервере.|  
|**sys.sysqnames**|Существует в каждой базе данных. Содержит по строке на каждое пространство имен или полное имя 4-байтового идентификационного токена.|  
|**sys.sysxmlcomponent**|Существует в каждой базе данных. Каждая строка представляет компонент XML-схемы.|  
|**sys.sysxmlfacet**|Существует в каждой базе данных. Содержит по строке на каждый из аспектов (ограничений) определения типа XML.|  
|**sys.sysxmlplacement**|Существует в каждой базе данных. Содержит по строке на каждое XML-размещение для компонентов XML.|  
|**sys.syssingleobjrefs**|Существует в каждой базе данных. Содержит по строке на каждую ссылку типа N-1.|  
|**sys.sysmultiobjrefs**|Существует в каждой базе данных. Содержит по строке на каждую ссылку типа N-N.|  
|**sys.sysobjvalues**|Существует в каждой базе данных. Содержит по строке на каждое общее свойство сущности.|  
|**sys.sysguidrefs**|Существует в каждой базе данных. Содержит по строке на каждую ссылку типа GUID.|  
  
  
