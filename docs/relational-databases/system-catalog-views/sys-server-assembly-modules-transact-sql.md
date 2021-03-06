---
title: sys. server_assembly_modules (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_assembly_modules_TSQL
- sys.server_assembly_modules
- server_assembly_modules
- sys.server_assembly_modules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_assembly_modules catalog view
ms.assetid: af799e38-2d16-49b2-bcf5-6f9199af899e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 714d0ca36bc48206ee7431454a61b51d2c31afb0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68060561"
---
# <a name="sysserver_assembly_modules-transact-sql"></a>sys.server_assembly_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке о каждом модуле сборки триггеров серверного уровня типа TA. Это представление сопоставляет триггеры сборок с базовой реализацией среды CLR. Это отношение можно присоединить к **sys. server_triggers**. Сборка должна быть загружена в базу данных **master** . Ключом отношения является кортеж (object_id).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Обратная ссылка внешнего ключа (FOREIGN KEY) на объект, для которого определен данный модуль сборки.|  
|**assembly_id**|**int**|Идентификатор той сборки, откуда был создан этот модуль. Сборка должна быть загружена в базу данных master.|  
|**assembly_class**|**имеет sysname**|Имя класса, входящего в сборку и определяющего данный модуль.|  
|**assembly_method**|**имеет sysname**|Имя метода в классе, определяющем данный модуль. В случае агрегатных функций имеет значение NULL.|  
|**execute_as_principal_id**|**int**|Идентификатор сервера-участника, входящего в предложение EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> ИДЕНТИФИКАТОР указанного участника, если он выполняется как \<основной>.<br /><br /> -2 = EXECUTE AS OWNER.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)  
  
  
