---
title: Настройка параметра конфигурации сервера "remote access" | Документы Майкрософт
ms.custom: ''
ms.date: 10/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: e499315b2807245a34d3ec4fe7d7616e98b76512
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62811358"
---
# <a name="configure-the-remote-access-server-configuration-option"></a>Настройка параметра конфигурации сервера remote access
  В этом разделе описываются способы настройки параметра конфигурации сервера **remote access** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **remote access** управляет выполнением хранимых процедур на локальных или удаленных серверах, на которых запущены экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение этого параметра по умолчанию равно 1. Это предоставляет разрешение на запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур с локального сервера. Значение параметра 0 предотвращает запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур на локальном сервере.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]Вместо этого используйте [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql) .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра Remote Access с помощью:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [после настройки параметра Remote Access](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Параметр **remote access** применим только к серверам, добавленным при помощи хранимой процедуры [sp_addserver](/sql/relational-databases/system-stored-procedures/sp-addserver-transact-sql), и включен только в целях обратной совместимости.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-access-option"></a>Настройка параметра remote access  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В диалоговом окне **Удаленные серверные соединения**установите или сбросьте флажок **Разрешить удаленные соединения с этим сервером** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-remote-access-option"></a>Настройка параметра remote access  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `remote access` равным `0`.  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a>Дальнейшие действия. После настройки параметра Remote Access  
 Этот параметр вступит в силу после перезапуска SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
