---
title: Изменение статистики | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6f34bf5db992f1d7062f9def1805996701eda5f
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72906210"
---
# <a name="modify-statistics"></a>Изменение статистики
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Существующую статистику в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] можно изменить с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Безопасность](#Security)  
  
-   **Для изменения статистики используются:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Должны выполняться следующие требования.  
  
-   пользователь должен иметь разрешение ALTER на таблицу или представление;  
  
-   пользователь должен быть владельцем таблицы или индексированного представления или членом одной из следующих ролей: предопределенная роль сервера **sysadmin** , предопределенная роль базы данных **db_owner** или предопределенная роль базы данных **db_ddladmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-modify-statistics"></a>Изменение статистики  
  
1.  В **обозревателе объектов**щелкните значок «плюс», чтобы развернуть базу данных, в которой нужно изменить статистику.  
  
2.  Чтобы развернуть папку **Таблицы** , щелкните значок «плюс».  
  
3.  Щелкните значок «плюс», чтобы развернуть таблицу, в которой нужно изменить статистику.  
  
4.  Щелкните значок «плюс», чтобы развернуть папку **Статистика** .  
  
5.  Щелкните правой кнопкой мыши объект статистики, который нужно изменить, и выберите пункт **Свойства**.  
  
6.  В диалоговом окне **Свойства статистики —** *имя_статистики* на странице **Общие** нажмите кнопку **Добавить**, **Удалить**, **Переместить вверх**, **Переместить вниз** либо любое их сочетание, чтобы изменить свойства статистики. Имейте в виду, что положение столбца в сетке **Столбцы статистики** может оказывать значительное влияние на полезность статистики.  
  
7.  Нажмите кнопку **ОК**.  

##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
 **Изменение статистики**  
  
 Эту задачу нельзя выполнить с помощью инструкций Transact-SQL. Чтобы изменить статистику с помощью Transact-SQL, нужно удалить существующую статистику и создать ее повторно с новыми атрибутами.  
  
 Дополнительные сведения см. в статьях [DROP STATISTICS (Transact-SQL)](../../t-sql/statements/drop-statistics-transact-sql.md) и [CREATE STATISTICS (Transact-SQL)](../../t-sql/statements/create-statistics-transact-sql.md).  
  
  
