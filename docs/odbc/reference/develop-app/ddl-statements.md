---
title: Инструкции DDL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97541c9d594b282b871cb7869d0e8c2d2224205d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076853"
---
# <a name="ddl-statements"></a>Инструкции DDL
Инструкции языка описания данных DDL отличаются невероятно между СУБД. ODBC SQL определяет инструкции для наиболее распространенных операций определения данных: создание и удаление таблиц, индексов и представлений; изменение таблиц; и предоставление и отзыв привилегий. Все остальные инструкции DDL относятся к источнику данных. Поэтому взаимодействующие приложения не могут выполнять некоторые операции определения данных. Как правило, это не проблема, так как такие операции, как правило, относятся исключительно к СУБД и лучше всего подходят для специализированного программного обеспечения администрирования базы данных, поставляемого с большинством СУБД или программой установки, поставляемой с драйвером.  
  
 Еще одна проблема в определении данных заключается в том, что имена типов данных различаются невероятно в СУБД. Вместо того, чтобы определять имена стандартных типов данных и принудительно преобразовывать их в имена СУБД, **SQLGetTypeInfo** предоставляет приложениям возможность обнаруживать имена типов данных, относящиеся к СУБД. Приложения, поддерживающие взаимодействие, должны использовать эти имена в инструкциях SQL для создания и изменения таблиц; имена, перечисленные в [приложении C: грамматика SQL](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)и [Приложение D: типы данных](../../../odbc/reference/appendixes/appendix-d-data-types.md), являются примерами.
