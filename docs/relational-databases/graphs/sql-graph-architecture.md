---
title: Архитектура SQL Graph | Документация Майкрософт
ms.custom: ''
ms.date: 09/24/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: language-reference
helpviewer_keywords:
- SQL graph
- SQL graph, architecture
ms.assetid: ''
author: shkale-msft
ms.author: shkale
monikerRange: =azuresqldb-current||>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 79a85515322d492d4356d47f78da4b79489a223e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68811106"
---
# <a name="sql-graph-architecture"></a>Архитектура SQL Graph  
[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

Узнайте о проектировании SQL Graph. Знание основ облегчит понимание других статей SQL Graph.
 
## <a name="sql-graph-database"></a>База данных SQL Graph
Пользователи могут создать один график для каждой базы данных. Граф — это коллекция узлов и граничных таблиц. Таблицы node или ребра могут быть созданы в любой схеме базы данных, но все они принадлежат к одному логическому графу. Таблица узлов представляет собой коллекцию узлов такого же типа. Например, таблица узлов Person содержит все узлы Person, принадлежащие графу. Аналогичным образом, краевая таблица представляет собой коллекцию схожих типов краев. Например, пограничная таблица друзья содержит все грани, соединяющие человека с другим лицом. Поскольку узлы и края хранятся в таблицах, большинство операций, поддерживаемых в обычных таблицах, поддерживаются в таблицах node и EDGE. 
 
 
![Архитектура SQL-Graph](../../relational-databases/graphs/media/sql-graph-architecture.png "Архитектура базы данных SQL Graph")   

Рис. 1. Архитектура базы данных SQL Graph
 
## <a name="node-table"></a>Таблица node
Таблица узлов представляет сущность в схеме графа. При каждом создании таблицы узлов вместе с определяемыми пользователем столбцами создается неявный `$node_id` столбец, который однозначно идентифицирует данный узел в базе данных. Значения в `$node_id` создаются автоматически и являются сочетанием `object_id` этой таблицы узлов и созданного внутренним значением bigint. Однако при выборе `$node_id` столбца выводится вычисляемое значение в виде строки JSON. Кроме того `$node_id` , является псевдо-столбцом, который сопоставляется с внутренним именем и шестнадцатеричной строкой. При выборе `$node_id` из таблицы имя столбца отображается как `$node_id_<hex_string>`. Использование имен псевдо-столбцов в запросах является рекомендуемым способом запроса к внутреннему `$node_id` столбцу и использования внутреннего имени с шестнадцатеричной строкой.

Рекомендуется, чтобы пользователи создавали уникальное ограничение или индекс для `$node_id` столбца во время создания таблицы node, но если он не создан, автоматически создается уникальный некластеризованный индекс по умолчанию. Однако любой индекс в псевдо-столбце на диаграмме создается в базовых внутренних столбцах. То есть индекс, созданный для `$node_id` столбца, будет отображаться во внутреннем `graph_id_<hex_string>` столбце.   


## <a name="edge-table"></a>Краевая таблица
Краевая таблица представляет связь в графе. Края всегда направляются и соединяются с двумя узлами. Краевая таблица позволяет пользователям моделировать связи «многие ко многим» в графе. Краевая таблица может содержать или не иметь определяемых пользователем атрибутов. При каждом создании граничной таблицы вместе с определяемыми пользователем атрибутами в граничной таблице создаются три неявные столбцы:

|Имя столбца    |Description  |
|---   |---  |
|`$edge_id`   |Уникально идентифицирует заданное ребро в базе данных. Это созданный столбец, а значение — это сочетание object_id краевой таблицы и созданное внутренним значением типа bigint. Однако при выборе `$edge_id` столбца выводится вычисляемое значение в виде строки JSON. `$edge_id`— Это псевдо-столбец, который сопоставляется с внутренним именем и шестнадцатеричной строкой. При выборе `$edge_id` из таблицы имя столбца отображается как `$edge_id_\<hex_string>`. Использование имен псевдо-столбцов в запросах является рекомендуемым способом запроса к внутреннему `$edge_id` столбцу и использования внутреннего имени с шестнадцатеричной строкой. |
|`$from_id`   |`$node_id` Хранит узел, с которого поступила сторона.  |
|`$to_id`   |`$node_id` Хранит узел, в котором заканчивается граница. |

Узлы, к которым может подключаться данная граница, управляются данными, `$from_id` вставленными в `$to_id` столбцы и. В первом выпуске невозможно определить ограничения для граничной таблицы, чтобы ограничить ее соединением двух типов узлов. То есть ребро может соединять любые два узла в графе, независимо от их типов.

Как и в `$node_id` случае со столбцом, рекомендуется, чтобы пользователи создавали уникальный индекс или ограничение `$edge_id` на столбец во время создания граничной таблицы, но если она не создана, для этого столбца автоматически создается уникальный, некластеризованный индекс по умолчанию. Однако любой индекс в псевдо-столбце на диаграмме создается в базовых внутренних столбцах. То есть индекс, созданный для `$edge_id` столбца, будет отображаться во внутреннем `graph_id_<hex_string>` столбце. Также рекомендуется использовать для сценариев OLTP, что пользователи создают индекс в столбцах (`$from_id`, `$to_id`) для ускорения уточняющих запросов в направлении края.  

На рис. 2 показано, как таблицы node и граничных таблиц хранятся в базе данных. 

![Person-друзья — таблицы](../../relational-databases/graphs/media/person-friends-tables.png "Пограничные таблицы узлов Person и друзей")   

Рисунок 2. представление таблицы node и ребра



## <a name="metadata"></a>Метаданные
Используйте эти представления метаданных для просмотра атрибутов узла или граничной таблицы.
 
### <a name="systables"></a>sys.tables
В SYS будут добавлены следующие новые, битовые типы. Таблице. Если `is_node` параметр имеет значение 1, то это означает, что таблица является таблицей узла, `is_edge` а если параметр имеет значение 1, то это означает, что таблица является краевой таблицей.
 
|Имя столбца |Тип данных |Description |
|--- |---|--- |
|is_node |bit |1 = это таблица узлов |
|is_edge |bit |1 = это краевая таблица |
 
### <a name="syscolumns"></a>sys.columns
`sys.columns` Представление содержит дополнительные столбцы `graph_type` и `graph_type_desc`, которое указывает тип столбца в таблицах node и ребра.
 
|Имя столбца |Тип данных |Description |
|--- |---|--- |
|graph_type |INT |Внутренний столбец с набором значений. Значения находятся в диапазоне от 1-8 для столбцов Graph и NULL для других.  |
|graph_type_desc |nvarchar(60)  |внутренний столбец с набором значений |
 
В следующей таблице перечислены допустимые значения `graph_type` столбца.

|Значение столбца  |Description  |
|---   |---   |
|1  |GRAPH_ID  |
|2  |GRAPH_ID_COMPUTED  |
|3  |GRAPH_FROM_ID  |
|4  |GRAPH_FROM_OBJ_ID  |
|5  |GRAPH_FROM_ID_COMPUTED  |
|6  |GRAPH_TO_ID  |
|7  |GRAPH_TO_OBJ_ID  |
|8  |GRAPH_TO_ID_COMPUTED  |


`sys.columns`также хранит сведения о неявных столбцах, созданных в таблицах node или ребра. Следующие сведения могут быть получены из sys. Columns, однако пользователи не могут выбирать эти столбцы из таблицы узлов или граничных таблиц. 

Неявные столбцы в таблице node

|Имя столбца    |Тип данных  |is_hidden  |Комментарий  |
|---  |---|---|---  |
|graph_id_\<hex_string> |BIGINT |1  |внутренний `graph_id` столбец  |
|$node _id_\<hex_string> |NVARCHAR   |0  |Столбец внешнего `node_id` узла  |

Неявные столбцы в граничной таблице

|Имя столбца    |Тип данных  |is_hidden  |Комментарий  |
|---  |---|---|---  |
|graph_id_\<hex_string> |BIGINT |1  |внутренний `graph_id` столбец  |
|$edge _id_\<hex_string> |NVARCHAR   |0  |внешний `edge_id` столбец  |
|from_obj_id_\<hex_string>  |INT    |1  |внутренний из узла`object_id`  |
|from_id_\<hex_string>  |BIGINT |1  |Внутренний из узла`graph_id`  |
|$from _id_\<hex_string> |NVARCHAR   |0  |внешний с узла`node_id`  |
|to_obj_id_\<hex_string>    |INT    |1  |внутренний для узла`object_id`  |
|to_id_\<hex_string>    |BIGINT |1  |Внутренний для узла`graph_id`  |
|$to _id_\<hex_string>   |NVARCHAR   |0  |внешний с узлом`node_id`  |
 
### <a name="system-functions"></a>Системные функции
Добавляются следующие встроенные функции. Это поможет пользователям извлечь информацию из созданных столбцов. Обратите внимание, что эти методы не будут проверять входные данные пользователя. Если пользователь указывает недопустимый `sys.node_id` метод, будет извлечена соответствующая часть и возвращена. Например, OBJECT_ID_FROM_NODE_ID принимает в `$node_id` качестве входных данных и возвращает object_id таблицы, к которой принадлежит этот узел. 
 
|Встроены   |Description  |
|---  |---  |
|OBJECT_ID_FROM_NODE_ID |Извлеките object_id из`node_id`  |
|GRAPH_ID_FROM_NODE_ID  |Извлеките graph_id из`node_id`  |
|NODE_ID_FROM_PARTS |Создание node_id из `object_id` и`graph_id`  |
|OBJECT_ID_FROM_EDGE_ID |Извлечь `object_id` из`edge_id`  |
|GRAPH_ID_FROM_EDGE_ID  |Извлечь удостоверение из`edge_id`  |
|EDGE_ID_FROM_PARTS |Конструкция `edge_id` из `object_id` и удостоверений  |



## <a name="transact-sql-reference"></a>Справочник по Transact-SQL 
Узнайте о [!INCLUDE[tsql-md](../../includes/tsql-md.md)] расширениях, появившихся в SQL Server и базе данных SQL Azure, которые позволяют создавать и выполнять запросы к объектам Graph. Расширения языка запросов помогают отправлять запросы и просматривать графы с помощью синтаксиса ASCII.
 
### <a name="data-definition-language-ddl-statements"></a>Инструкции языка описания данных DDL

|Задача   |Связанная статья  |Заметки
|---  |---  |---  |
|CREATE TABLE |[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-sql-graph.md)|`CREATE TABLE`теперь расширен для поддержки создания таблицы в качестве узла или в качестве границы. Обратите внимание, что у краевой таблицы могут быть определенные пользовательские атрибуты.  |
|ALTER TABLE    |[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)|Таблицы узлов и граничных таблиц могут быть изменены так же, как и реляционная таблица, с `ALTER TABLE`помощью. Пользователи могут добавлять или изменять определяемые пользователем столбцы, индексы или ограничения. Однако изменение внутренних столбцов графа, таких как `$node_id` или `$edge_id`, приведет к ошибке.  |
|CREATE INDEX   |[CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)  |Пользователи могут создавать индексы для псевдо-столбцов и определяемых пользователем столбцов в таблицах node и ребра. Поддерживаются все типы индексов, включая кластеризованные и некластеризованные индексы columnstore.  |
|СОЗДАНИЕ ОГРАНИЧЕНИЙ ГРАНИЦ    |[ОГРАНИЧЕНИЯ границ &#40;Transact-SQL&#41;](../../relational-databases/tables/graph-edge-constraints.md)  |Теперь пользователи могут создавать ограничения границ для граничных таблиц, чтобы обеспечить определенную семантику, а также поддерживать целостность данных.  |
|DROP TABLE |[DROP TABLE &#40;&#41;Transact-SQL](../../t-sql/statements/drop-table-transact-sql.md)  |Таблицы node и граничных объектов могут быть удалены так же, как реляционная таблица, с помощью `DROP TABLE`. Однако в этом выпуске нет ограничений, чтобы гарантировать, что границы не указывают на удаленный узел и каскадное удаление краев, при удалении таблицы узла или узла не поддерживается. Рекомендуется, чтобы при удалении таблицы узлов пользователи удалили все грани, подключенные к узлам в этой таблице узлов, вручную для поддержания целостности графа.  |


### <a name="data-manipulation-language-dml-statements"></a>Инструкции языка обработки данных DML

|Задача   |Связанная статья  |Заметки
|---  |---  |---  |
|INSERT |[INSERT (Transact-SQL)](../../t-sql/statements/insert-sql-graph.md)|Вставка в таблицу узлов не отличается от вставки в реляционную таблицу. Значения `$node_id` столбца создаются автоматически. Попытка вставить значение в `$node_id` столбец или `$edge_id` приведет к ошибке. Пользователи должны указать значения для `$from_id` столбцов `$to_id` и при вставке в краевую таблицу. `$from_id`и `$to_id` — это `$node_id` значения узлов, к которым подключается данный ребр.  |
|DELETE | [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)|Данные из таблиц узлов и краев могут быть удалены таким же образом, как и при удалении из реляционных таблиц. Однако в этом выпуске нет ограничений, чтобы гарантировать, что границы не указывают на удаленный узел и каскадное удаление краев, при удалении узла не поддерживается. Рекомендуется, чтобы при каждом удалении узла также удалялись все соединяющие его узлы, чтобы обеспечить целостность графа.  |
|UPDATE |[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)  |Значения в определяемых пользователем столбцах можно обновлять с помощью инструкции UPDATE. Обновление внутренних столбцов графа, `$node_id` `$edge_id`, `$from_id` и `$to_id` запрещено.  |
|MERGE |[&#41;Transact-SQL &#40;MERGE](../../t-sql/statements/merge-transact-sql.md)  |`MERGE`оператор поддерживается в таблице узлов или граничных таблиц.  |


### <a name="query-statements"></a>Инструкции запроса

|Задача   |Связанная статья  |Заметки
|---  |---  |---  |
|SELECT |[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)|Узлы и грани внутренне хранятся как таблицы, поэтому большинство операций, поддерживаемых в таблице в SQL Server или базе данных SQL Azure, поддерживаются в таблицах node и EDGE.  |
|MATCH  | [СООТВЕТСТВИЕ &#40;&#41;Transact-SQL](../../t-sql/queries/match-sql-graph.md)|Встроена встроенная поддержка сопоставления шаблонов и обхода графа.  |



## <a name="limitations-and-known-issues"></a>Ограничения и известные проблемы  
В этом выпуске существуют определенные ограничения на таблицы node и граничных таблиц:
* Локальные или глобальные временные таблицы не могут быть таблицами узлов или граничных таблиц.
* Табличные типы и табличные переменные не могут объявляться в качестве узлов или граничных таблиц. 
* Таблицы узлов и граничных таблиц не могут быть созданы как темпоральной таблицы с системным управлением версиями.   
* Таблицы узлов и граничных таблиц не могут быть оптимизированными для памяти таблицами.  
* Пользователи не могут обновлять `$from_id` столбцы `$to_id` и пограничных элементов с помощью инструкции UPDATE. Чтобы обновить узлы, к которым подключается ребро, пользователям придется вставить новый ребро, указывающее на новые узлы, и удалить предыдущее.
* Запросы между базами данных на объектах графа не поддерживаются. 


## <a name="next-steps"></a>Next Steps
Чтобы приступить к работе с новым синтаксисом, см. [Пример базы данных SQL Graph](./sql-graph-sample.md) .
 

