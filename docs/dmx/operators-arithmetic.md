---
title: Арифметические операторы (расширения интеллектуального анализа данных) | Документация Майкрософт
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: e78241252733e8298c0bc727f9c45dd6df2768ac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68008212"
---
# <a name="operators---arithmetic"></a>Операторы — арифметические
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Арифметические операторы можно использовать в расширениях интеллектуального анализа данных (DMX) для арифметических вычислений в [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], включая сложение, вычитание, умножение и деление.  
  
 В следующей таблице даны арифметические операторы, поддерживаемые расширениями интеллектуального анализа данных.  
  
|Оператор|Description|  
|--------------|-----------------|  
|[+ &#40;Добавление&#41; &#40;расширений интеллектуального анализа данных&#41;](../dmx/add-dmx.md)|Складывает два числа.|  
|[-&#40;вычитание&#41; &#40;расширений интеллектуального анализа данных&#41;](../dmx/subtract-dmx.md)|Вычитает одно число из другого.|  
|[&#42; &#40;умножение&#41; &#40;DMX&#41;](../dmx/multiply-dmx.md)|Умножает одно число на другое.|  
|[&#40;разделение&#41; &#40;DMX&#41;](../dmx/divide-dmx.md)|Делит одно число на другое.|  
  
 Следующие правила определяют очередность выполнения арифметических операторов в выражении расширений интеллектуального анализа данных:  
  
-   Если в выражении присутствует несколько арифметических операторов, умножение и деление выполняются в первую очередь, затем — вычитание и сложение.  
  
-   Если все арифметические операторы в выражении имеют одинаковую очередность, они выполняются слева направо.  
  
-   Выражения, находящиеся внутри скобок, имеют наибольший приоритет.  
  
## <a name="see-also"></a>См. также:  
 [Расширения интеллектуального анализа данных &#40;Справочник по DMX&#41;](../dmx/data-mining-extensions-dmx-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по функциям DMX&#41;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Ссылки на операторы расширений интеллектуального анализа данных &#40;DMX&#41;](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Расширения интеллектуального анализа данных &#40;Справочник по инструкции DMX&#41;](../dmx/data-mining-extensions-dmx-statements.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические обозначения&#41; DMX](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Расширения интеллектуального анализа данных &#40;синтаксические&#41; DMX-элементы](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Выражения &#40;DMX&#41;](../dmx/expressions-dmx.md)   
 [Общие прогнозирующие функции &#40;&#41;расширений интеллектуального анализа данных](../dmx/general-prediction-functions-dmx.md)   
 [Операторы &#40;&#41;расширений интеллектуального анализа данных](../dmx/operators-dmx.md)   
 [Структура и использование прогнозирующих запросов расширений интеллектуального анализа данных](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Общие сведения об инструкции расширения интеллектуального анализа данных SELECT](../dmx/understanding-the-dmx-select-statement.md)  
  
  
