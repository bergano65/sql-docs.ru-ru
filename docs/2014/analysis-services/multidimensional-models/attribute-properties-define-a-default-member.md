---
title: Определение элемента по умолчанию | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- default members
- attributes [Analysis Services], default members
- members [Analysis Services], default
- DefaultMember property
ms.assetid: db487856-ee21-49c3-aa08-d9136e193374
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 959645223eacec6c000ddbfa23615b7949d10d5a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077421"
---
# <a name="define-a-default-member"></a>Определение элемента по умолчанию
  Элемент по умолчанию иерархии атрибута предназначен для вычисления выражений в том случае, если иерархия атрибутов не включена в запрос. Этот элемент не обрабатывается, если запрос содержит иерархию атрибута или пользовательскую иерархию, в которых присутствует атрибут, являющийся источником иерархии атрибута. В этом случае используется элемент, указанный в запросе.  
  
 Элемент по умолчанию для иерархии атрибута задается указанием элемента атрибута в качестве значения свойства `DefaultMember` для иерархии атрибута. Это свойство можно задать в конструкторе измерений на вкладке «Структура измерения» или в скрипте вычисления куба на вкладке «Вычисления» в конструкторе кубов среды [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]. Можно также задать свойство `DefaultMember` для роли безопасности (переопределив элемент по умолчанию, заданный для измерения) на вкладке «Данные измерения» при определении безопасности измерения. Во избежание проблем разрешения имен следует определить элемент по умолчанию в скрипте многомерных выражений куба в следующих ситуациях: если куб ссылается на измерение базы данных более одного раза, если имя измерения в кубе отличается от имени измерения в базе данных и если в разных кубах должны быть различные элементы по умолчанию.  
  
 Элемент по умолчанию атрибута используется для оценки выражений, когда атрибут не включен в запрос. Элемент по умолчанию для атрибута указывается свойством `DefaultMember` атрибута. Когда иерархия из измерения включается в запрос, все элементы по умолчанию из атрибутов, соответствующих уровням иерархии, пропускаются. Если в запрос не включена иерархия измерения, то элементы по умолчанию используются для всех атрибутов в измерении.  
  
## <a name="resolving-the-default-member-when-no-default-member-is-specified"></a>Разрешение элемента по умолчанию при отсутствии указанного элемента по умолчанию  
 Если для иерархии атрибута не указан элемент по умолчанию и она допускает статистическую обработку (свойство `IsAggregatable` атрибута равно `True`), то элементом по умолчанию является элемент «Все». Если элемент по умолчанию не указан и атрибут не подлежит статистическому вычислению (свойство `IsAggregatable` атрибута равно `False`), то элемент по умолчанию выбирается из верхнего уровня иерархии атрибута.  
  
## <a name="specifying-the-default-member"></a>Задание элемента по умолчанию  
 Каждый атрибут в измерении в [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] имеет элемент по умолчанию, который можно указать с помощью `DefaultMember` свойства для атрибута. Эта настройка используется для оценки выражений, если атрибут не включен в запрос. Если в запросе задается иерархия в измерении, то элементы по умолчанию для атрибутов и иерархии игнорируются. Если в запросе не указана иерархия в измерении, параметры `DefaultMember` атрибутов измерения вступают в силу.  
  
 Если `DefaultMember` параметр для атрибута пуст и его `IsAggregatable` свойство имеет значение `True`, то элементом по умолчанию является элемент все. Если `IsAggregatable` свойство имеет значение `False`, элемент по умолчанию является первым элементом первого видимого уровня.  
  
 `DefaultMember` Параметр для атрибута применяется к каждой иерархии, в которой участвует атрибут. Нельзя использовать различные настройки для различных иерархий в измерении. Например, если элемент [1998] является элементом по умолчанию для атрибута [Год], то эта настройка применяется ко всем иерархиям в измерении. `DefaultMember` Параметр в этом случае не может быть [1998] в одной иерархии и [1997] в другой иерархии.  
  
 При определении элемента по умолчанию для конкретного уровня в иерархии, который не вычисляется естественным образом, необходимо определить элементы по умолчанию на всех уровнях выше этого уровня в иерархии. Например, в иерархии все страны — прогноз погоды нельзя определить элемент по умолчанию для климата, если не определен элемент по умолчанию для стран. Если это не сделано, то будут возникать ошибки во время выполнения запросов.  
  
 Когда уровни в иерархии вычисляются естественным образом, можно определить элемент по умолчанию для любого атрибута в иерархии, вне зависимости от других атрибутов в этой иерархии. Например, в иерархии страна-провинция-город можно определить элемент по умолчанию для города, например [City]. [Монреаль] без определения элемента по умолчанию для State или Country.  
  
## <a name="see-also"></a>См. также:  
 [Настройка &#40;всех уровней&#41; для иерархий атрибутов](database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)  
  
  
