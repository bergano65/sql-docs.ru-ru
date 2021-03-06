---
title: Интерфейсы на уровне вызовов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], CLI
- CLI [ODBC], using CLI
- sending SQL statements to DBMS [ODBC]
- SQL [ODBC], CLI
- call-level interface [ODBC], using call-level interface
ms.assetid: 42257bb6-0bf1-4533-a4ef-4a6dd2aecb18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c6c37084ad91a931c4479ecf826c5cb554765412
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135667"
---
# <a name="call-level-interfaces"></a>Интерфейсы уровня вызова
Последний способ отправки инструкций SQL в СУБД — через интерфейс уровня вызовов (CLI). Интерфейс уровня вызовов предоставляет библиотеку функций СУБД, которые могут вызываться программой приложения. Таким образом, вместо того, чтобы смешивать SQL с другим языком программирования, интерфейс на уровне вызовов аналогичен библиотекам подпрограмм, которые большинство программистов привыкли использовать, например строки, операции ввода-вывода или математические библиотеки на языке C. Обратите внимание, что СУБД, поддерживающие внедренный SQL, уже имеют интерфейс уровня вызова, вызовы, создаваемые предварительной компилятором. Однако эти вызовы не документированы и могут быть изменены без предварительного уведомления.  
  
 Интерфейсы уровня вызова обычно используются в архитектурах клиент-сервер, в которых программа приложения (клиент) находится на одном компьютере, а СУБД (сервер) находится на другом компьютере. Приложение вызывает функции CLI в локальной системе, и эти вызовы отправляются по сети СУБД для обработки.  
  
 Интерфейс уровня вызова аналогичен динамическому SQL, в котором инструкции SQL передаются СУБД для обработки во время выполнения, но она отличается от внедренного SQL в целом в том, что нет внедренных инструкций SQL и предварительная компилятор не требуется.  
  
 Использование интерфейса уровня вызовов обычно включает следующие шаги:  
  
1.  Приложение вызывает функцию CLI для подключения к СУБД.  
  
2.  Приложение создает инструкцию SQL и помещает ее в буфер. Затем он вызывает одну или несколько функций интерфейса командной строки для отправки инструкции СУБД для подготовки и выполнения.  
  
3.  Если инструкция является инструкцией SELECT, приложение вызывает функцию CLI для возврата результатов в буферы приложения. Как правило, эта функция возвращает по одной строке или по одному столбцу данных за раз.  
  
4.  Приложение вызывает функцию CLI для отключения от СУБД.
