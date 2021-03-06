---
title: ЗАДАТЬ точную команду | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXACT command [ODBC]
ms.assetid: 9533d3e0-e7c1-49de-a3a3-0cc4373a91cb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 686ecc89f44bac4b219b760e55160f451a15c503
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67997726"
---
# <a name="set-exact-command"></a>Команда SET EXACT
Задает правила сравнения двух строк разной длины.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET EXACT ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Указывает, что выражения должны соответствовать символу, чтобы символ был эквивалентен. Для сравнения все замыкающие пробелы в выражениях игнорируются. Для сравнения более короткие два выражения добавляются справа с пробелами, чтобы соответствовать длине длинного выражения.  
  
 OFF  
 (По умолчанию.) Указывает, что выражение должно соответствовать символу для символа, пока не будет достигнут конец выражения с правой стороны.  
  
## <a name="remarks"></a>Remarks  
 Параметр Задать точную настройку не действует, если обе строки имеют одинаковую длину.  
  
## <a name="string-comparisons"></a>Сравнения строк  
 Visual FoxPro имеет два реляционных оператора, которые проверяют на равенство.  
  
 Оператор = выполняет сравнение двух значений одного типа. Этот оператор подходит для сравнения символов, числовых, дат и логических данных.  
  
 Однако при сравнении символьных выражений с оператором = результаты могут отличаться от предполагаемых. Символьные выражения — это сравниваемый символ слева направо, пока одно из выражений не равно значению другого, пока не будет достигнут конец выражения справа от оператора = (задать точную отметку) или пока не будут выполнены концы обоих выражений. достигнуто (задайте точное значение ON).  
  
 Оператор = = можно использовать, если требуется точное сравнение символьных данных. Если два символьных выражения сравниваются с оператором = =, выражения на обеих сторонах оператора = = должны содержать одни и те же символы, включая пробелы, чтобы считаться равными. Параметр Задать точную настройку игнорируется, если символьные строки сравниваются с помощью = =.  
  
 В следующей таблице показано, как выбор оператора и точной настройки влияют на сравнения. (Символ подчеркивания представляет пробел.)  
  
|Сравнение|= ТОЧНАЯ ОТКЛЮЧАЕТСЯ|= ТОЧНОЕ ЗНАЧЕНИЕ ON|= = Точное включение или отключение|  
|----------------|------------------|-----------------|--------------------------|  
|"ABC" = "ABC"|Соответствует|Соответствует|Соответствует|  
|"AB" = "ABC"|Нет совпадений|Нет совпадений|Нет совпадений|  
|"ABC" = "AB"|Соответствует|Нет совпадений|Нет совпадений|  
|"ABC" = "ab_"|Нет совпадений|Нет совпадений|Нет совпадений|  
|"AB" = "ab_"|Нет совпадений|Соответствует|Нет совпадений|  
|"ab_" = "AB"|Соответствует|Соответствует|Нет совпадений|  
|"" = "AB"|Нет совпадений|Нет совпадений|Нет совпадений|  
|"AB" = ""|Соответствует|Нет совпадений|Нет совпадений|  
|"__" = ""|Соответствует|Соответствует|Нет совпадений|  
|"" = "___"|Нет совпадений|Соответствует|Нет совпадений|  
|TRIM ("___") = ""|Соответствует|Соответствует|Соответствует|  
|"" = TRIM ("___")|Соответствует|Соответствует|Соответствует|  
  
## <a name="see-also"></a>См. также:  
 [Команда SET ANSI](../../odbc/microsoft/set-ansi-command.md)
