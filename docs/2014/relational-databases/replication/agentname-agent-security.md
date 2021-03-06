---
title: Защита агента &lt;Имя_агента&gt; | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d77f8d6acb449bc9aa2298dbcba9782fd7bc07e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62722126"
---
# <a name="ltagentnamegt-agent-security"></a>Защита агента &lt;Имя_агента&gt;
  На ** \<странице Безопасность агента ажентнаме>** можно указать учетные записи, с которыми агент распространения (для репликации транзакций и репликацией моментальных снимков) или агент слияния (для репликации слиянием), и установить подключения к компьютерам в топологии репликации. Сведения о разрешениях, требуемых агентами, и об оптимальных методах защиты репликации см. в статьях [Модель безопасности агента репликации](security/replication-agent-security-model.md) и [Рекомендации по защите репликации](security/replication-security-best-practices.md).  
  
## <a name="options"></a>Параметры  
 Нажмите кнопку свойств (**...**) в строке для каждого подписчика, чтобы открыть диалоговое окно **Безопасность агента распространителя** или **Безопасность агента слияния** . Для получения дополнительных сведений о разрешениях, необходимых для учетных записей агентов, нажмите кнопку **Справка** в появившемся диалоговом окне.  
  
 После ввода параметров в одном из диалоговых окон в сетке будут отображены сведения о соединении для подписчика.  
  
 **Агент для подписчика**  
 Имя каждого подписчика.  
  
 **Соединение с распространителем**  
 Отображается для репликации транзакций и репликации моментальных снимков. Контекст, в котором устанавливается соединение с распространителем. Локальные соединения всегда создаются с помощью контекста учетной записи [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, под которой работает агент.  
  
-   Для принудительных подписок локальным подключением является подключение к распространителю, поэтому в этом поле всегда будет отображаться следующее: **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'** для принудительных подписок.  
  
-   Для подписок по запросу соединения также могут быть созданы в контексте имени входа [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В поле отображается одна из следующих строк: **Use login '\<Имя_для_входа>'**, **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выполнять соединение в контексте учетной записи Windows.  
  
 **Соединение с издателем & распространителя**  
 Отображается для репликации слиянием. Контекст, под которым созданы соединения с издателем и распространителем. Локальные соединения всегда создаются с помощью контекста учетной записи Windows, под которой работает агент.  
  
-   Для принудительных подписок локальным подключением является подключение к издателю и распространителю, поэтому в этом поле всегда будет отображаться следующее: **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'** для принудительных подписок.  
  
-   Для подписок по запросу соединения также могут быть созданы в контексте имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В поле отображается одна из следующих строк: **Use login '\<Имя_для_входа>'**, **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выполнять соединение в контексте учетной записи Windows.  
  
 **Соединение с подписчиком**  
 Контекст, в котором устанавливается соединение с подписчиком. Локальные соединения всегда создаются с помощью контекста учетной записи Windows, под которой работает агент.  
  
-   Для подписок по запросу локальным соединением является соединение с подписчиком, поэтому в этом поле всегда будет отображаться следующее: **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'** для принудительных подписок.  
  
-   Для принудительных подписок соединения также могут быть созданы в контексте имени входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . В поле отображается одна из следующих строк: **Use login '\<Имя_для_входа>'**, **Impersonate '\<Домен>\\<Имя_для_входа\>'** или **Impersonate '\<Компьютер>\\<Имя_для_входа\>'**. 
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует выполнять соединение в контексте учетной записи Windows.  
  
## <a name="see-also"></a>См. также:  
 [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)   
 [Просмотр и изменение свойств принудительной подписки](view-and-modify-push-subscription-properties.md)   
 [Управление именами входа и паролями в репликации](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication)   
 [Модель безопасности агента репликации](security/replication-agent-security-model.md)   
 [Безопасность Репликация SQL Server](security/view-and-modify-replication-security-settings.md)  
  
  
