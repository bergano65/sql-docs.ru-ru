---
title: sys. filegroup (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.filegroups_TSQL
- filegroups
- sys.filegroups
- filegroups_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.filegroups catalog view
ms.assetid: 9e851f72-1f8e-4515-a25d-152ebc12ed56
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 313c0b80a1bf1d2a094760198053e26426e99c36
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68005171"
---
# <a name="sysfilegroups-transact-sql"></a>sys.filegroups (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Содержит по одной строке для каждого пространства данных, занимаемого файловой группой.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**\<наследуемые столбцы>**|--|Список столбцов, наследуемых этим представлением, см. в разделе [sys. data_spaces &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md).|  
|**filegroup_guid**|**UNIQUEIDENTIFIER**|Идентификатор GUID файловой группы.<br /><br /> NULL = файловая группа PRIMARY|  
|**log_filegroup_id**|**int**|
  [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец имеет значение NULL.|  
|**is_read_only**|**bit**|1 = Файловая группа доступна только для чтения.<br /><br /> 0 = Файловая группа доступна для чтения и записи.|  
|**is_autogrow_all_files**|**bit**|**Применимо к** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] :[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (с по [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).<br /><br /> 1 = Если файл в файловой группе соответствует пороговому значению автоматического увеличения, все файлы в файловой группе увеличиваются.<br /><br /> 0 = если файл в файловой группе соответствует пороговому значению автоматического увеличения, то растет только этот файл. Это значение используется по умолчанию.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** . Дополнительные сведения см. в разделе [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Пространства данных &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/data-spaces-transact-sql.md)  
  
  
