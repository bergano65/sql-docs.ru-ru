---
title: sp_requestpeerresponse (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_requestpeerresponse_TSQL
- sp_requestpeerresponse
helpviewer_keywords:
- sp_requestpeerresponse
ms.assetid: cbe13c22-4d7d-4a36-b194-7a13ce68ef27
author: stevestein
ms.author: sstein
ms.openlocfilehash: f8d75b208cc91d52d20fb4e94340809cd6857fa1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68129734"
---
# <a name="sp_requestpeerresponse-transact-sql"></a>sp_requestpeerresponse (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  При выполнении на узле в одноранговой топологии эта процедура запрашивает ответ от всех остальных узлов в топологии. Выполнив эту процедуру и просмотрев соответствующие ответы, пользователь может быть уверен, что все предыдущие команды были доставлены в узлы, из которых получены ответы. Эта хранимая процедура выполняется в запрашивающем узле в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_requestpeerresponse [ @publication = ] 'publication'  
    [ , [ @description = ] 'description'  
    [ , [ @request_id = ] request_id OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации в одноранговой топологии, для которой проверяется состояние. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @description = ] 'description'`Определяемые пользователем данные, которые можно использовать для определения отдельных запросов состояния. *Description* имеет тип **nvarchar (4000)** и значение по умолчанию NULL.  
  
`[ @request_id = ] request_id`Возвращает идентификатор нового запроса. *request_id* имеет **тип int** и является выходным параметром. Это значение можно использовать при выполнении [sp_helppeerresponses &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerresponses-transact-sql.md) для просмотра всех ответов на запрос состояния.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_requestpeerresponse** используется в одноранговой репликации транзакций.  
  
 **sp_requestpeerresponse** используется, чтобы убедиться, что все команды были получены всеми другими узлами перед восстановлением базы данных, опубликованной в одноранговой топологии. Эта процедура используется, если при репликации изменений языка DDL, выполненных, когда узел был в режиме «вне сети», необходимо оценить, когда эти изменения переданы на другие узлы.  
  
 **sp_requestpeerresponse** не может быть выполнена в пользовательской транзакции.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_requestpeerresponse**.  
  
## <a name="see-also"></a>См. также:  
 [sp_deletepeerrequesthistory &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-deletepeerrequesthistory-transact-sql.md)   
 [sp_helppeerrequests &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppeerrequests-transact-sql.md)  
  
  
