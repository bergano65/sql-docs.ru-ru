---
title: Уровни изоляции транзакций | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- locking [SQL Server], hints
- isolation levels [SQL Server], metadata access
- hints [SQL Server], locking
ms.assetid: 02bb71fa-1e92-4782-a9cf-6e256cc1f3ea
author: rothja
ms.author: jroth
ms.openlocfilehash: 28a8de0654fe6e083b52e83d85653a0d9856d351
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68072204"
---
# <a name="transaction-isolation-levels"></a>Уровни изоляции транзакций
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не дает гарантии того, что указания блокировки будут соблюдаться в запросах, осуществляющих доступ к метаданным через представления каталога, представления совместимости, представления информационной схемы и встроенные функции, создающие метаданные.  
  
 Внутри системы компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использует для доступа к метаданным только уровень изоляции READ COMMITTED. Если у трансляции есть уровень изоляции, например SERIALIZABLE, а внутри транзакции делается попытка осуществления доступа к метаданным при помощи представления каталога или встроенных функций, создающих метаданные, то эти запросы будут выполняться до завершения выполнения как READ COMMITTED. Однако в изоляции моментальных снимков доступ к метаданным будет запрещен из-за одновременных операций DDL. Это происходит из-за несоответствия версий метаданных. Таким образом, доступ в изоляции моментальных снимков может быть запрещен из-за:  
  
-   Представления каталога  
  
-   представлений совместимости;  
  
-   Представления информационной схемы  
  
-   встроенных функций, создающих метаданные;  
  
-   групп хранимых процедур **sp_help**;  
  
-   процедур каталога Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)];  
  
-   динамических административных представлений и функций.  
  
 Дополнительные сведения об уровнях изоляции см. в разделе [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
 В следующей таблице приведена сводка доступов к метаданным в различных уровнях изоляции.  
  
|Уровень изоляции|Поддерживается|Соблюдается|  
|---------------------|---------------|-------------|  
|READ UNCOMMITTED|нет|Не гарантируется|  
|READ COMMITTED|Да|Да|  
|REPEATABLE READ|нет|нет|  
|SNAPSHOT ISOLATION|нет|нет|  
|SERIALIZABLE|нет|нет|  
  
  
