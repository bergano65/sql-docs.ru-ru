---
title: Определение свойств измерения куба | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], characteristics
- properties [Analysis Services], dimensions
ms.assetid: 9314e749-0918-4862-abaf-a21692188122
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ecf47eff045aa379a8e67332a82b2045a8569a2a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66075692"
---
# <a name="define-cube-dimension-properties"></a>Определение свойств измерения куба
  Измерение куба представляет собой экземпляр измерения базы данных в пределах куба. Измерение базы данных может быть использовано в нескольких кубах, а измерения нескольких кубов могут быть основаны на одном измерении базы данных. В следующей таблице описаны свойства измерения куба.  
  
|Свойство|Description|  
|--------------|-----------------|  
|`AllMemberAggregationUsage`|Управляет тем, как агрегаты создаются конструктором статистических [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]схем в. Это свойство может иметь следующие значения:<br /><br /> **Full**: каждый агрегат для куба должен включать элемент «все».<br /><br /> **None**: ни один агрегат для куба не может включать элемент "все". Это значение по умолчанию.<br /><br /> Без **ограничений**: в конструкторе статистических схем не накладываются никакие ограничения.<br /><br /> **По умолчанию**: те же функциональные возможности, что и Unrestricted.|  
|`Description`|Представляет описательное имя уровня.|  
|`DimensionID`|Содержит уникальный идентификатор (ID) измерения базы данных.|  
|`HierarchyUniqueNameStyle`|Определяет правила формирования уникальных имен для иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> 
  `IncludeDimensionName`: имя измерения включается в качестве части имени иерархии. Это значение по умолчанию.<br /><br /> 
  `ExcludeDimensionName`: имя измерения не включается в качестве части имени иерархии.|  
|`ID`|Содержит уникальный идентификатор измерения куба.|  
|`MemberUniqueNameStyle`|Определяет правила формирования уникальных имен для элементов иерархий, содержащихся в измерении куба. Это свойство может иметь следующие значения:<br /><br /> 
  `Native`: службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] автоматически определяют уникальные имена элементов. Это значение по умолчанию.<br /><br /> 
  `NamePath`: службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] формируют составное имя, содержащее имя каждого уровня и заголовок элемента.|  
|`Name`|Содержит понятное имя измерения куба. По умолчанию имя измерения куба является таким же, как и имя измерения базы данных, если только уже не определено измерение куба с таким же именем.|  
|`Visible`|Определяет, является ли измерение куба видимым. По умолчанию используется значение `True`.|  
  
## <a name="see-also"></a>См. также:  
 [Измерения &#40;Analysis Services многомерных данных&#41;](../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)  
  
  
