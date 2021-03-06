---
title: Вызов SQLSetPos | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], SQLSetPos
- SQLSetPos function [ODBC], calling
- upgrading applications [ODBC], SQLSetPos
- backward compatibility [ODBC], SqlSetPos
- application upgrades [ODBC], SQLSetPos
ms.assetid: 846354b8-966c-4c2c-b32f-b0c8e649cedd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c64575777fc9210c36be5d417cd3def0c2c7102a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068678"
---
# <a name="calling-sqlsetpos"></a>Вызов SQLSetPos
В ODBC *2. x*указатель на массив состояния строки был аргументом для **SQLExtendedFetch**. Впоследствии массив состояния строк был обновлен с помощью вызова функции **SQLSetPos**. Некоторые драйверы полагаться на тот факт, что этот массив не меняется между **SQLExtendedFetch** и **SQLSetPos**. В ODBC *3. x*указатель на массив состояния является полем дескриптора, поэтому приложение может легко изменить его, чтобы оно указывало на другой массив. Это может быть проблемой, когда приложение ODBC *3. x* работает с драйвером ODBC *2. x* , но вызывает **SQLSetStmtAttr** для установки указателя состояния массива и вызова **SQLFetchScroll** для выборки данных. Диспетчер драйверов сопоставляет его как последовательность вызовов **SQLExtendedFetch**. В следующем коде ошибка обычно возникает, когда диспетчер драйверов сопоставляет второй вызов **SQLSetStmtAttr** при работе с драйвером ODBC *2. x* :  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStatus, 0);  
SQLFetchScroll(hstmt, fFetchType, iRow);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, rgfRowStat1, 0);  
SQLSetPos(hstmt, iRow, fOption, fLock);  
```  
  
 Эта ошибка возникает, если невозможно изменить указатель состояния строки в ODBC *2. x* между вызовами **SQLExtendedFetch**. Вместо этого диспетчер драйверов выполняет следующие действия при работе с драйвером ODBC *2. x* :  
  
1.  Инициализирует внутренний флаг диспетчера драйверов *фсетпосеррор* в значение true.  
  
2.  Когда приложение вызывает **SQLFetchScroll**, диспетчер драйверов устанавливает *фсетпосеррор* в значение false.  
  
3.  Когда приложение вызывает **SQLSetStmtAttr** для установки SQL_ATTR_ROW_STATUS_PTR, диспетчер драйверов устанавливает *Фсетпосеррор* равным тотруе.  
  
4.  Когда приложение вызывает функцию **SQLSetPos**с параметром *фсетпосеррор* , равным true, диспетчер драйверов создает SQL_ERROR с параметром SQLSTATE HY011 (атрибут не может быть установлен сейчас), чтобы указать, что приложение попыталось вызвать функцию **SQLSetPos** после изменения указателя состояния строки, но до вызова **SQLFetchScroll**.
