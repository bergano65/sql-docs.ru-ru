---
title: sys. transmission_queue (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- transmission_queue
- sys.transmission_queue_TSQL
- sys.transmission_queue
- transmission_queue_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.transmission_queue catalog view
ms.assetid: f3515d1a-be8f-4a27-8058-8865f0919838
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7bd461a677a7bfab145846baaf09c0a8a62d6f8b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68022606"
---
# <a name="systransmission_queue-transact-sql"></a>sys.transmission_queue (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Данное представление каталога содержит по одной строке для каждого сообщения в очереди передачи, как показано в следующей таблице:  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**conversation_handle**|**UNIQUEIDENTIFIER**|Идентификатор диалога, которому принадлежит данное сообщение. Не допускает значения NULL.|  
|**to_service_name**|**nvarchar(256)**|Имя службы, которой было послано сообщение. Допускает значение NULL.|  
|**to_broker_instance**|**nvarchar(128**|Идентификатор брокера, содержащего службу, которой было послано сообщение. Допускает значение NULL.|  
|**from_service_name**|**nvarchar(256)**|Имя службы, отправившей сообщение. Допускает значение NULL.|  
|**service_contract_name**|**nvarchar(256)**|Имя контракта, которому следует диалог этого сообщения. Допускает значение NULL.|  
|**enqueue_time**|**datetime**|Время поступления сообщения в очередь. Это значение использует формат UTC независимо от местного часового пояса экземпляра. Не допускает значения NULL.|  
|**message_sequence_number**|**bigint**|Порядковый номер сообщения. Не допускает значения NULL.|  
|**message_type_name**|**nvarchar(256)**|Имя типа сообщения. Допускает значение NULL.|  
|**is_conversation_error**|**bit**|Является ли это сообщение сообщением об ошибке:<br /><br /> 0 = не является сообщением об ошибке.<br /><br /> 1 = сообщение об ошибке.<br /><br /> Не допускает значения NULL.|  
|**is_end_of_dialog**|**bit**|Является ли это сообщение сообщением о завершении диалога. Не допускает значения NULL.<br /><br /> 0 = не является сообщением о завершении диалога.<br /><br /> 1 = сообщение о завершении диалога.<br /><br /> Не допускает значения NULL.|  
|**message_body**|**varbinary(max)**|Содержимое сообщения. Допускает значение NULL.|  
|**transmission_status**|**nvarchar (4000)**|Причина, по которой сообщение было отправлено в очередь. Обычно это сообщение об ошибке, поясняющее, почему отправка сообщения закончилась неудачей. Если оно пустое, значит сообщение еще не было отослано. Допускает значение NULL.|  
|**приоритеты**|**tinyint**|Уровень приоритета, назначенный для этого сообщения. Не допускает значения NULL.|  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
  
