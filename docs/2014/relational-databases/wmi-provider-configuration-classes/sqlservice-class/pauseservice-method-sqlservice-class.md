---
title: Метод PauseService (класс SqlService) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- PauseService Method (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- PauseService method
ms.assetid: 5c3a8feb-58b8-4385-b4c8-bf33cf4d276d
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: f4b9667f9d0018920885d4fdf7e5fce3b5a47311
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63061842"
---
# <a name="pauseservice-method-sqlservice-class"></a>Метод PauseService (класс SqlService)
  Пытается перевести службу в состояние приостановки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object  
.PauseService()  
  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 Объект [класса SqlService](sqlservice-class.md) , представляющий службу.  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Значение uint32, равное 0, если служба была успешно остановлена, равное 1, если запрос не поддерживается, и равное любому другому числу для указания ошибки.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Запуск и остановка служб](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
