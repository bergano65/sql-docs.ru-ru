---
title: Бит доверия | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3198188a-2b59-4865-9560-10f760934b8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c8e03217eef0ee9e23d6efa2bbcb8e715fe64dcb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63252731"
---
# <a name="trustworthy-bit"></a>Бит доверия
  Это правило определяет, назначена ли роль базы данных dbo предопределенной роли сервера sysadmin и установлен ли бит доверия базы данных (значение ON).  
  
 Если эти условия выполняются, привилегированный пользователь базы данных может повысить право доступа до роли sysadmin. Члены этой роли могут создавать и выполнять небезопасные сборки, которые представляют угрозу для системы.  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Сбросьте бит доверия или отмените разрешения sysadmin из роли базы данных dbo.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение с помощью управления на основе политик и принудительное применение рекомендаций с помощью управления на основе политик](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
