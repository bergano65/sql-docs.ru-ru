---
title: OpeningPeriod (многомерные выражения) | Документация Майкрософт
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 07f94c3ed850af10120b1de7d95941bc5c90e826
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68088220"
---
# <a name="openingperiod-mdx"></a>OpeningPeriod (многомерные выражения)


  Возвращает первый элемент с общим родителем из потомков заданного уровня, необязательно заданного элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
OpeningPeriod( [ Level_Expression [ , Member_Expression ] ] )  
```  
  
## <a name="arguments"></a>Аргументы  
 *Level_Expression*  
 Допустимое многомерное выражение, возвращающее уровень.  
  
 *Member_Expression*  
 Допустимое многомерное выражение, возвращающее элемент.  
  
## <a name="remarks"></a>Remarks  
 Эта функция прежде всего предназначена для использования в измерении времени, но может быть использована и для других измерений.  
  
-   Если выражение уровня задано, функция **OpeningPeriod** использует иерархию, содержащую указанный уровень, и возвращает первый элемент среди потомков элемента по умолчанию на заданном уровне.  
  
-   Если указано как выражение уровня, так и выражение элемента, функция **OpeningPeriod** возвращает первый родственный элемент среди потомков указанного элемента на заданном уровне в иерархии, содержащей указанный уровень.  
  
-   Если не указано ни выражение уровня, ни выражение элемента, функция **OpeningPeriod** использует уровень по умолчанию и элемент измерения с типом времени.  
  
> [!NOTE]  
>  Функция [ClosingPeriod](../mdx/closingperiod-mdx.md) похожа на функцию **OpeningPeriod** , за исключением того, что функция **ClosingPeriod** Возвращает последний элемент того же уровня, а не первый элемент того же уровня.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращается значение меры по умолчанию для элемента FY2002 измерения Date (измерение времени). Этот элемент возвращается, поскольку уровень Fiscal Year — первый потомок уровня «Все». Иерархия Fiscal — иерархия по умолчанию, поскольку это первая пользовательская иерархия из коллекции иерархий. Элемент FY2002 — первый элемент этой иерархии данного уровня.  
  
```  
SELECT OpeningPeriod() ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента «1 июля 2001» уровня Date.Date.Date в иерархии атрибута Date.Date. Это первый элемент уровня «Все» в иерархии атрибута Date.Date.  
  
```  
SELECT OpeningPeriod([Date].[Date].[Date]) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента January 2003, который является первым элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Calendar.  
  
```  
SELECT OpeningPeriod([Date].[Calendar].[Month],[Date].[Calendar].[Calendar Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
 В следующем примере возвращается значение меры по умолчанию для элемента July 2003, который является первым элементом из потомков элемента «2003» на уровне года в пользовательской иерархии Fiscal.  
  
```  
SELECT OpeningPeriod([Date].[Fiscal].[Month],[Date].[Fiscal].[Fiscal Year].&[2003]) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>См. также:  
 [TopCount &#40;&#41;многомерных выражений](../mdx/topcount-mdx.md)   
 [Ссылка на функцию многомерных выражений &#40;&#41;многомерных выражений](../mdx/mdx-function-reference-mdx.md)   
 [FirstSibling &#40;&#41;многомерных выражений](../mdx/firstsibling-mdx.md)  
  
  
