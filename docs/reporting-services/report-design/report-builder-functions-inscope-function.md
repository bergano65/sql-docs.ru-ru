---
title: Функция InScope (построитель отчетов) | Документация Майкрософт
ms.date: 03/08/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: a8cd209a-e5d3-4dce-ab2d-f271f6c54955
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 02ba83e15f22e28d3378996c98af4468ae425366
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "77081257"
---
# <a name="report-builder-functions---inscope-function"></a>Функции построителя отчетов — функция InScope
  Указывает, входит ли текущий экземпляр элемента в указанную область.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Синтаксис  
  
```  
InScope(scope)  
```  
  
#### <a name="parameters"></a>Параметры  
 *область*  
 (**String**) Имя набора данных, области данных или группы, определяющей область.  
  
## <a name="return-type"></a>Тип возвращаемых данных  
 Возвращает **Boolean**.  
  
## <a name="remarks"></a>Remarks  
 Функция **InScope** проверяет область текущего экземпляра элемента отчета на членство в области, указанной параметром *scope*.  
  
 Значением*Scope* не может быть выражение.  
  
 Обычно функция **InScope** применяется в областях данных с динамическим определением области действия. Например, функция **InScope** может использоваться в ссылке детализации в ячейках области данных, чтобы предоставить другое название отчета и другие наборы параметров в зависимости от выбранной ячейки. Далее приведен пример.  
  
-   Следующее выражение, используемое в качестве названия отчета в ссылке детализации, открывает отчет `ProductDetail` , если выбранная ячейка находится в группе `Month` , и отчет `ProductSummary` — в противном случае.  
  
    ```  
    =Iif(InScope("Month"), "ProductDetail", "ProductSummary")  
    ```  
  
-   Следующее выражение, используемое в свойстве **Omit** параметра детализированного отчета, передает параметр целевому отчету только в том случае, если выбранная ячейка находится в группе `Product` .  
  
    ```  
    =Not(InScope("Product"))  
    ```  
  
 Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md) и [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода показывает, находится ли данный экземпляр элемента в пределах набора данных, области данных или в области группы `Product` .  
  
```  
=InScope("Product")  
```  
  
## <a name="see-also"></a>См. также:  
 [Использование выражений в отчетах (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Примеры выражений (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Типы данных в выражениях (построитель отчетов и службы SSRS)](../../reporting-services/report-design/data-types-in-expressions-report-builder-and-ssrs.md)   
 [Область выражения для суммирования, агрегатных функций и встроенных коллекций (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
