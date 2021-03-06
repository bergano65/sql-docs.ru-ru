---
title: Динамическая трассировка | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- tracing options [ODBC], dynamic
- dynamic tracing [ODBC]
ms.assetid: ebe58a83-a7b0-4747-86c8-2af2940471ef
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8420589761a1f8cb1f9cf8a3022842863fd30758
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046890"
---
# <a name="dynamic-tracing"></a>Динамическая трассировка
Трассировку можно включить или отключить в любой точке выполнения приложения. Это позволяет приложению отслеживать любое количество вызовов функций.  
  
 Переменная **одбкшаредтрацефлаг** настроена на динамическое включение трассировки. Эта переменная является общей для всех выполняющихся копий диспетчера драйверов. Если какое-либо приложение задает эту переменную, трассировка включается для всех приложений ODBC, работающих в данный момент. Чтобы отключить трассировку при включенной динамической трассировке, приложение вызывает **SQLSetConnectAttr** , чтобы задать для SQL_ATTR_TRACE значение SQL_TRACE_OFF. Этот вызов отключает трассировку только для этого приложения. Приложения, связанные с библиотеками odbc32. lib, могут изменять использование этой переменной. Данные трассировки могут отображаться в окне в режиме реального времени, а не в файле трассировки, который должен быть открыт после сеанса ODBC. Элементы управления можно добавлять на экран приложения для включения или отключения трассировки.  
  
 Библиотека DLL трассировки, поставляемая с ODBC 3 *. x* , не является потокобезопасной. Не гарантируется, что файл журнала будет записан правильно, если включена Глобальная трассировка (переменная **одбкшаредтрацефлаг** установлена) и несколько приложений одновременно записывают в файл трассировки. Это условие не возвращает ошибку.
