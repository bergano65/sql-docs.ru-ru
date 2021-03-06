---
title: Сообщения об ошибках
description: Сообщения об ошибках параллельного хранилища данных (PDW) сообщают об ошибках и проблемах, возникших в компонентах PDW, и могут также включать SQL Server ошибки, выданные с помощью PDW. Эти сообщения об ошибках используют единообразный синтаксис для представления информации. Понимание этого синтаксиса позволит выявление и устранение проблем.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2d89e80a89df53e85ef8d2bf53c369d9e4dc0d49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74401167"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Сообщения об ошибках в параллельном хранилище данных

Сообщения об ошибках параллельного хранилища данных (PDW) сообщают об ошибках и проблемах, возникших в компонентах PDW, и могут также включать SQL Server ошибки, выданные с помощью PDW. Эти сообщения об ошибках используют единообразный синтаксис для представления информации. Понимание этого синтаксиса позволит выявление и устранение проблем в SQL Server PDW.  
  
## <a name="Basics"></a>Основные сведения о сообщении об ошибке  
Возвращаемые сообщения об ошибках следуют тем же синтаксису.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Это возможные значения для каждого поля:  
  
|Поле|Description|Пример|  
|---------|---------------|-----------|  
|*Error_Indicator*|Слово «ошибка» или другой текст предупреждает пользователя о проблеме.|ОШИБКА|  
|*SQL_State_Code*|Код состояния SQL в соответствии со спецификацией ODBC. Драйвер создает соответствующий код состояния SQL всякий раз, когда он возвращает сообщение в приложение. Текст "Microsoft" указывает на источник ошибки.|42000|  
|*Driver_Details*|Сведения, зависящие от драйвера, например тип используемого драйвера.|Драйвер параллельного хранилища данных ODBC SQL Server 2008 R2|  
|*QueryID*|Уникальный идентификатор запроса. Это значение используется для поиска дополнительных сведений, связанных с обработкой запроса. Например, сведения о выполнении запроса можно найти в консоли администрирования, используя идентификатор запроса. Дополнительные сведения см. [в разделе мониторинг устройства с помощью консоли администрирования](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Если QueryID неприменимо, то пользователю возвращается текст «internal».|QID2377|  
|*Message_String*|Понятное описание ошибки или проблемы. При возврате SQL Server ошибок это SQL Server текст сообщения.|В списке SET инструкции UPDATE может присутствовать только равное присваивание.|  
  
Эти примеры значений будут представлены пользователю следующим образом:  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>См. также:  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Основные сведения об оповещениях консоли администрирования](understanding-admin-console-alerts.md)  
  
