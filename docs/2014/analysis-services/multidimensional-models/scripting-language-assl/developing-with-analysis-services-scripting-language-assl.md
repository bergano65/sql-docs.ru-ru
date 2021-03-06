---
title: Разработка с использованием языкового скрипта Analysis Services (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: dfdce0d0db35d651d12670ffd3cb1c9437961cd1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62736522"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Разработка на языке ASSL (язык ASSL)
  Язык ASSL является расширением XML для аналитики, в котором добавлен язык определения объектов и командный язык для создания структур служб Analysis Services и управления этими структурами непосредственно на сервере. Язык ASSL можно применять в пользовательском приложении для обмена данными со службами Analysis Services по протоколу XMLA. Язык ASSL состоит из двух частей.  
  
-   Язык описания данных DDL, или язык определения объектов, который определяет и описывает экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также базы данных и объекты баз данных, находящихся в этом экземпляре.  
  
-   Командный язык, предназначенный для отправки экземпляру служб Analysis Services команд-действий, например `Create`, `Alter` или `Process`. Этот язык команд рассматривается в [справочнике по XML для аналитики &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).  
  
 Чтобы просмотреть код ASSL, описывающий многомерное решение в среде [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], можно использовать команду «Показать код» на уровне проекта. Также можно создать или изменить скрипт языка ASSL в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] с помощью редактора запросов XMLA. Построенные скрипты можно использовать для управления объектами и выполнения команд на сервере.  
  
## <a name="see-also"></a>См. также:  
 [Объекты и характеристики объектов ASSL](assl-objects-and-object-characteristics.md)   
 [XML-соглашения ASSL](assl-xml-conventions.md)   
 [Источники данных и привязки &#40;многомерные&#41;SSAS](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  
