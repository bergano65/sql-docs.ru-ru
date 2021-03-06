---
title: Изменение порядка параметров отчета (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7a1d9413332ed19bd4db94fc60beecff85f02ac7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66106331"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a>Изменение порядка параметров отчета (построитель отчетов и службы SSRS)
  Изменять порядок параметров отчета необходимо в случае, если зависимый параметр расположен перед параметром, от которого он зависит. Порядок параметров имеет значение при наличии каскадных параметров или в случае, если необходимо показать пользователям значение по умолчанию одного параметра перед тем, как они выберут значения для других параметров. Зависимый параметр отчета ссылается (в своем запросе значений по умолчанию или в запросе допустимых значений) на параметр запроса, указывающий на параметр отчета, расположенный после него в списке параметров на панели данных отчета.  
  
 Порядок, в котором параметры отображаются на панели инструментов средства просмотра отчетов, определяется порядком параметров в области данных отчета.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a>Изменение порядка параметров отчета  
  
1.  В области данных отчета разверните узел «Параметры».  
  
2.  Щелкните параметр и используйте кнопки со стрелками вниз и вверх, расположенные на панели инструментов области данных отчета, чтобы переместить параметр выше или ниже в списке. На рисунке показана панель инструментов области данных отчета в построителе отчетов.  
  
     ![Область данных отчета](../media/reportdatapane.png "Область данных отчета")  
  
## <a name="see-also"></a>См. также:  
 [Параметры отчета (построитель отчетов и конструктор отчетов)](report-parameters-report-builder-and-report-designer.md)   
 [Построитель отчетов справки по диалоговым окнам, панелям и мастерам](../report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Добавление каскадных параметров в отчет (построитель отчетов и службы SSRS)](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [Учебник. Добавление параметра к отчету (построитель отчетов)](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Добавление фильтров набора данных, фильтров области данных и групповых фильтров (построитель отчетов и службы SSRS)](add-dataset-filters-data-region-filters-and-group-filters.md)   
 [Ссылки на коллекцию параметров (построитель отчетов и службы SSRS)](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
