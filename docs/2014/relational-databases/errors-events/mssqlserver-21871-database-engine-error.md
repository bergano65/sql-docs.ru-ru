---
title: MSSQLSERVER_21871 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 832ee3caa23a034f1c228d01ff8ec2ceda32de06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62915126"
---
# <a name="mssqlserver_21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21871|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum21871|  
|Текст сообщения|Издатель %s базы данных %s не перенаправлен.|  
  
## <a name="explanation"></a>Объяснение  
 `sp_validate_replica_hosts_as_publishers` проверяет таблицу MSredirected_publishers в базе данных распространителя, пытаясь найти запись идентифицированного издателя и базы данных издателя.  
  `sp_validate_replica_hosts_as_publishers` возвращает ошибку 21871, если запись не будет найдена.  
  
## <a name="user-action"></a>Действие пользователя  
 
  `sp_validate_replica_hosts_as_publishers` относится только к перенаправляемым издателям. Если база данных издателя является членом группы доступности, воспользуйтесь хранимой процедурой `sp_redirect_publisher`, чтобы связать издателя и базу данных издателя с именем прослушивателя группы доступности соответствующей группы доступности.  
  
  
