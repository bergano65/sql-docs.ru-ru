---
title: Приложение F. Библиотека курсоров ODBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], about cursor library
- ODBC cursor library [ODBC]
- cursor library [ODBC], about cursor library
- cursor library [ODBC]
ms.assetid: a03084df-4e48-48ef-917d-4a3fae48a605
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3bfffd95dd88b0a25be682a3df581e55825ed9ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68090836"
---
# <a name="appendix-f-odbc-cursor-library"></a>Приложение Е. Библиотека курсоров ODBC
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этой функции в новых разработках и запланируйте изменение приложений, которые в настоящее время используют эту функцию. Корпорация Майкрософт рекомендует использовать функцию курсора драйвера.  
  
 Библиотека курсоров ODBC (Odbccr32. dll) поддерживает блокирование прокручиваемых курсоров для любого драйвера, который соответствует уровню соответствия API уровня 1 и может распространяться разработчиками с приложениями или драйверами. Библиотека курсоров также поддерживает позиционированные инструкции UPDATE и DELETE для результирующих наборов, созданных инструкциями **SELECT** . Хотя он поддерживает только статические и последовательные курсоры, Библиотека курсоров удовлетворяет потребностям многих приложений. Более того, он обеспечивает хорошую производительность, особенно для небольших наборов результатов малого и среднего размера, а также для приложений, которые не имеют хорошей поддержки курсоров.  
  
 Библиотека курсоров — это библиотека динамической компоновки (DLL), которая находится между диспетчером драйверов и драйвером. Когда приложение вызывает функцию, диспетчер драйверов вызывает функцию в библиотеке курсоров, которая либо выполняет функцию, либо вызывает ее в указанном драйвере. Для данного соединения приложение указывает, используется ли библиотека курсоров всегда, используется, если драйвер не поддерживает прокручиваемые курсоры или никогда не используется.  
  
 Библиотека курсоров отображается как драйвер для диспетчера драйверов. Если библиотека курсоров находится между диспетчером драйверов и драйвером ODBC *2. x* , Библиотека курсоров отображается как драйвер ODBC *2. x* . Если библиотека курсоров находится между диспетчером драйверов и драйвером ODBC *3. x* , Библиотека курсоров отображается как драйвер ODBC *3. x* . Поведение библиотеки курсоров зависит от версии драйвера, с которым он работает, за исключением смещений привязки, которые поддерживаются драйверами ODBC *2. x* и ODBC *3. x* .  
  
 Чтобы реализовать блочные курсоры в **SQLFetch** и **SQLFetchScroll**, Библиотека курсоров многократно вызывает **SQLFetch** в драйвере. Для реализации прокрутки она кэширует полученные данные в памяти и в дисковых файлах. Когда приложение запрашивает новый набор строк, Библиотека курсоров извлекает его по мере необходимости из драйвера или из кэша.  
  
 Для реализации позиционированных инструкций UPDATE и DELETE библиотека курсоров формирует инструкцию **Update** или **Delete** с предложением **WHERE** , указывающим кэшированное значение каждого привязанного столбца в строке. При выполнении инструкции позиционированного обновления библиотека курсоров обновляет свой кэш из значений в буферах набора строк.  
  
 Дополнительные сведения о библиотеке курсоров ODBC см. в следующих разделах этого приложения:  
  
-   [Использование библиотеки курсоров ODBC](../../../odbc/reference/appendixes/using-the-odbc-cursor-library.md)  
  
-   [Выполнение инструкций позиционированного обновления и удаления](../../../odbc/reference/appendixes/executing-positioned-update-and-delete-statements.md)  
  
-   [Пример кода библиотеки курсоров](../../../odbc/reference/appendixes/cursor-library-code-example.md)  
  
-   [Примечания по реализации](../../../odbc/reference/appendixes/implementation-notes.md)  
  
-   [Коды ошибок для библиотеки курсоров ODBC](../../../odbc/reference/appendixes/odbc-cursor-library-error-codes.md)
