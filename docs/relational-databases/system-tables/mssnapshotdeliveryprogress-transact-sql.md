---
title: MSsnapshotdeliveryprogress (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
author: stevestein
ms.author: sstein
ms.openlocfilehash: 638bea3db68712300ad2284e50676bf1df67c9ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68139812"
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Таблица **MSsnapshotdeliveryprogress** используется для трассировки файлов, успешно доставленных подписчику при применении моментального снимка. Эти данные используются для возобновления доставки файлов в случае, если во время сеанса агент слияния не смог успешно доставить все файлы, чтобы те же самые файлы не доставлялись повторно при следующем запуске агента слияния. Эта таблица хранится на подписчике в базе данных подписки.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|Определяет путь к папке моментального снимка, откуда файл был успешно доставлен. Для публикаций, использующих параметризованные фильтры, строка **динснап** будет добавлена к значению.|  
|**progress_token_hash**|**int**|Хэш-значение, созданное на основе значения *progress_token* , которое используется для повышения эффективности поиска по заданному *progress_tokenому* значению.|  
|**progress_token**|**nvarchar (500)**|Определяет успешно доставленный файл; значение является сочетанием имени файла и пути.|  
|**progress_timestamp**|**datetime**|Значение **типа DateTime** , указывающее, когда файл моментального снимка был успешно доставлен.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40;&#41;Transact-SQL](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации &#40;&#41;Transact-SQL](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
