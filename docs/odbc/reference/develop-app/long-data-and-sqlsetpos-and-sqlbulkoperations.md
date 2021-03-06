---
title: Long Data, SQLSetPos и SQLBulkOperations | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- long data [ODBC]
- SQLSetPos function [ODBC], long data and SQLBulkOperations
- data updates [ODBC], long data
- updating data [ODBC], long data
- SQLBulkOperations function [ODBC], long data
ms.assetid: e2fdf842-5e4c-46ca-bb21-4625c3324f28
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 578c85331a65c15cb25b5d9b75b7156ab509e910
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036410"
---
# <a name="long-data-and-sqlsetpos-and-sqlbulkoperations"></a>Данные типа Long Data и функции SQLSetPos и SQLBulkOperations
Как и в случае с параметрами в инструкциях SQL, длинные данные можно отправлять при обновлении строк с помощью **SQLBulkOperations** или **SQLSetPos** или при вставке строк с помощью **SQLBulkOperations**. Данные отправляются частями с несколькими вызовами **SQLPutData**. Столбцы, для которых данные отправляются во время выполнения, называются *столбцами данных на этапе выполнения*.  
  
> [!NOTE]  
>  Приложение фактически может отправлять данные любого типа во время выполнения с помощью **SQLPutData**, хотя части могут отправляться только символьные и двоичные данные. Однако если данные достаточно малы для размещения в одном буфере, обычно нет причин использовать **SQLPutData**. Гораздо проще привязать буфер и позволить драйверу получать данные из буфера.  
  
 Так как длинные столбцы данных обычно не привязаны, приложение должно привязать столбец перед вызовом **SQLBulkOperations** или **SQLSetPos** и отменить привязку после вызова **SQLBulkOperations** или **SQLSetPos**. Столбец должен быть привязан, поскольку **SQLBulkOperations** или **SQLSetPos** работает только с связанными столбцами и должен быть несвязанным, чтобы **SQLGetData** можно было использовать для получения данных из столбца.  
  
 Для отправки данных во время выполнения приложение выполняет следующие действия.  
  
1.  Помещает 32-разрядное значение в буфер набора строк вместо значения данных. Это значение будет возвращено приложению позже, поэтому приложение должно задать для него осмысленное значение, например номер столбца или маркер файла, содержащего данные.  
  
2.  Задает значение в буфере длины или индикатора в результате выполнения макроса SQL_LEN_DATA_AT_EXEC (*length*). Это значение указывает драйверу, что данные для параметра будут отправляться с помощью **SQLPutData**. Значение *длины* используется при отправке длинных данных в источник данных, который должен определять, сколько байт данных будет отправлено, чтобы можно было предварительно выделить место. Чтобы определить, требуется ли для источника данных это значение, приложение вызывает **SQLGetInfo** с параметром SQL_NEED_LONG_DATA_LEN. Все драйверы должны поддерживать этот макрос; Если для источника данных длина байта не требуется, драйвер может проигнорировать его.  
  
3.  Вызывает **SQLBulkOperations** или **SQLSetPos**. Драйвер обнаруживает, что буфер длины или индикатора содержит результат выполнения макроса SQL_LEN_DATA_AT_EXEC (*length*) и возвращает SQL_NEED_DATA в качестве возвращаемого значения функции.  
  
4.  Вызывает **метод SQLParamData** в ответ на возвращаемое значение SQL_NEED_DATA. Если необходимо отправить данные типа Long, **метод SQLParamData** возвращает SQL_NEED_DATA. В буфере, на который указывает аргумент *валуептрптр* , драйвер возвращает уникальное значение, помещенное приложением в буфер набора строк. Если имеется более одного столбца данных в ходе выполнения, приложение использует это значение для определения столбца, для которого отправляются данные. драйвер не требуется для запроса данных для столбцов, выполняющих данные в каком-либо определенном порядке.  
  
5.  Вызывает **SQLPutData** для отправки данных столбца в драйвер. Если данные столбца не умещаются в одном буфере, то, как это часто происходит с длинными данными, приложение вызывает **SQLPutData** несколько раз для отправки данных в части; для сборки данных используется драйвер и источник данных. Если приложение передает строковые данные, заканчивающиеся нулем, драйвер или источник данных должен удалить символ завершения, заканчивающийся нулем, как часть процесса пересборки.  
  
6.  Вызывает **метод SQLParamData** еще раз, чтобы указать, что он отправил все данные для столбца. Если имеются столбцы данных, для которых данные не были отправлены, драйвер возвращает SQL_NEED_DATA и уникальное значение для следующего столбца Data-on-Execution. приложение вернется к шагу 5. Если данные были отправлены для всех столбцов данных в ходе выполнения, данные для строки отправляются в источник данных. Затем **метод SQLParamData** возвращает SQL_SUCCESS или SQL_SUCCESS_WITH_INFO и может возвращать любое значение SQLSTATE, которое может вернуть **SQLBulkOperations** или **SQLSetPos** .  
  
 После того как **SQLBulkOperations** или **SQLSetPos** возвращает SQL_NEED_DATA и до того, как данные были полностью отправлены для последнего столбца Data-on-Execution, инструкция находится в состоянии "требуется данные". В этом состоянии приложение может вызывать только **SQLPutData**, **метод SQLParamData**, **SQLCancel**, **SQLGetDiagField**или **SQLGetDiagRec**; все остальные функции возвращают SQLSTATE HY010 (ошибка последовательности функций). Вызов **SQLCancel** отменяет выполнение инструкции и возвращает его в предыдущее состояние. Дополнительные сведения см. в [приложении б: таблицы переходов состояния ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).
