---
title: Конструктор SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 18827d05bc5567b4566eaa006d88c249874132cf
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67971089"
---
# <a name="sqlserverexception-constructor-javalangstring-javalangstring-int-javalangthrowable"></a>Конструктор SQLServerException (java.lang.String, java.lang.String, int, java.lang.Throwable)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Инициализирует новый экземпляр класса [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) по полученным объектам **string**, **string**, значению **int** и объекту **throwable**.

## <a name="syntax"></a>Синтаксис  
  
```  
public SQLServerException(java.lang.String errText,
            SQLState errState,
            int errNum,
            java.lang.Throwable cause)
            
```  
  
#### <a name="parameters"></a>Параметры  
 *errText*  
  
 Строка, содержащая текст ошибки.
  
 *errState*  
  
 Строка, содержащая состояние ошибки.
 
 *errNum*  
  
 Значение int, которое содержит код ошибки для исключения.
 
 *cause*  
  
 Объект с атрибутом throwable, который содержит причину исключения.
  
## <a name="see-also"></a>См. также:  
 [Конструкторы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-constructors.md)   
 [Элементы SQLServerException](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [Класс SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
  
