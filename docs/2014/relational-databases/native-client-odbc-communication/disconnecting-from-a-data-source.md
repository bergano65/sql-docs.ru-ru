---
title: Отключение от источника данных | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC data sources, connections
- data sources [SQL Server Native Client]
- disconnecting [ODBC]
- ODBC applications, disconnecting
- SQLDisconnect function
- ODBC applications, data sources
- connections [SQL Server Native Client]
- SQLFreeHandle function
- ODBC data sources, disconnecting
- SQL Server Native Client ODBC driver, data sources
- ODBC functions
- SQL Server Native Client ODBC driver, connections
ms.assetid: 65b0267d-b2ab-4a59-83f2-436d90cfbf79
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43ccc784d0d8759c559e705cbbb65861040f6e8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63205679"
---
# <a name="disconnecting-from-a-data-source"></a>Отсоединение от источника данных
  Когда приложение завершило работу с источником данных, оно вызывает **SQLDisconnect**. **SQLDisconnect** освобождает все инструкции, выделенные для соединения, и отключает драйвер от источника данных. После отключения приложение может вызвать [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) , чтобы освободить маркер подключения. Перед выходом приложение также вызывает **SQLFreeHandle** , чтобы освободить обработчик среды.  
  
 После отсоединения приложение может повторно использовать выделенный дескриптор соединения, либо для соединения с другим источником данных, либо для повторного соединения с тем же. Для принятия решения о сохранении соединения или отсоединении и повторном соединении, разработчик приложения должен рассмотреть сравнительную стоимость каждого варианта. Соединение с источником данных и сохранение соединения в различных окружениях могут оказаться в разной степени затратными. Чтобы сделать выбор, следует также проанализировать вероятность и временные затраты других операций в том же источнике данных. Также приложению может потребоваться более одного соединения.  
  
## <a name="see-also"></a>См. также:  
 [Взаимодействие с SQL Server &#40;ODBC&#41;](communicating-with-sql-server-odbc.md)  
  
  
