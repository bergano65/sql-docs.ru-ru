---
title: Свойство Dependencies (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- Dependencies Property (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- Dependencies property
ms.assetid: 92d54b7e-de2f-4978-b601-0196e37cbb41
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: eae8ad534ba452acd7f65e4faf66dfcf4bc73791
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63223275"
---
# <a name="dependencies-property-sqlservice-class"></a>Свойство Dependencies (класс SqlService)
  Возвращает список служб, зависимых от указанной службы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.Dependencies [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Массив значений string[], содержащий список служб, зависимых от указанной службы.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
