---
title: Настройка почты агента SQL Server на использование компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3c2f5f0be09e9a60997308efd72c360348efc60
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289212"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>Настройка почты агента SQL Server на использование компонента Database Mail
  В этом разделе описывается настройка в агенте [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использования компонента Database Mail для отправки уведомлений и предупреждений в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
-   **Перед началом работы**  
  
-   [Предварительные требования](#Prerequisites)  
  
-   [Безопасность](#Security)  
  
-   [Настройка агент SQL Server для использования Database Mail с помощью SQL Server Management Studio](#SSMSProcedure)  
  
-   [Задачи дальнейших действий](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Включить компонент Database Mail.  
  
-   Создать учетную запись компонента Database Mail для агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Создайте профиль Database Mail для используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи службы агента и добавьте пользователя к **роли DatabaseMailUserRole** в базе данных **msdb** .  
  
-   Сделать профиль используемым по умолчанию в базе данных **msdb** .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Пользователь, создающий учетные записи профилей и выполняющий хранимые процедуры, должен быть членом предопределенной роли сервера sysadmin.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
 **Настройка агент SQL Server для использования Database Mail**  
  
-   Разверните экземпляр сервера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в обозревателе объектов.  
  
-   Щелкните правой кнопкой мыши **агент SQL Server**, затем выберите **Свойства**.  
  
-   Нажмите **Система предупреждений**.  
  
-   Выберите **Включить почтовый профиль**.  
  
-   В списке **Почтовая система** выберите **Компонент Database Mail**.  
  
-   В **Списке почтовых профилей**выберите почтовый профиль для компонента Database Mail.  
  
-   Перезапустите агент SQL Server.  
  
##  <a name="Follow_Up"></a>Задачи дальнейших действий  
 Следующие задачи необходимо выполнить для завершения конфигурации агента на отправку предупреждений и уведомлений.  
  
-   [видны узлы](../../ssms/agent/alerts.md)  
  
     Предупреждения могут быть настроены на уведомление оператора о возникновении в базе данных определенного события или о формировании в операционной системе определенных условий.  
  
-   [Операторы](../../ssms/agent/operators.md)  
  
     Операторы — это псевдонимы для людей или групп, которые могут получать электронные уведомления.  
  
  
