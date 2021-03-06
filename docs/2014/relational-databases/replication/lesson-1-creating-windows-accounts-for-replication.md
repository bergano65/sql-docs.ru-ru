---
title: Занятие 1. Создание учетных записей Windows для репликации | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
- replication [SQL Server], administering
ms.assetid: 65c3816b-47f0-448c-a4a4-ebd3e2a58820
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: a1457a6d407b2b20c28e93c0ed681ab1dc8109d4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62721158"
---
# <a name="lesson-1-creating-windows-accounts-for-replication"></a>Занятие 1. Создание учетных записей Windows для репликации
  На этом занятии будут созданы учетные записи Windows для запуска агентов репликации. На локальном сервере будут созданы отдельные учетные записи Windows для следующих агентов:  
  
|Агент|Location|Имя учетной записи|  
|-----------|--------------|------------------|  
|агент моментальных снимков|Издатель|\<*machine_name*> \ repl_snapshot|  
|Агент чтения журнала.|Издатель|\<*machine_name*> \ repl_logreader|  
|Агент распространителя|Издатель и подписчик|\<*machine_name*> \ repl_distribution|  
|Агент слияния.|Издатель и подписчик|\<*machine_name*> \ repl_merge|  
  
> [!NOTE]  
>  В учебниках по репликации издатель и распространитель совместно используют один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Издатель и подписчик могут совместно использовать один и тот же экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], но это не является обязательным. Если издатель и подписчик совместно используют один и тот же экземпляр, то не требуется выполнять шаги по созданию учетных записей на подписчике.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-publisher"></a>Создание локальных учетных записей Windows для агентов репликации на издателе  
  
1.  На издателе откройте оснастку « **Управление компьютером** » из **меню «Администрирование** » на панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши элемент **Пользователи** и выберите пункт **Новый пользователь**.  
  
4.  Введите `repl_snapshot` в поле **имя пользователя** , укажите пароль и другие важные сведения, а затем нажмите кнопку **создать** , чтобы создать учетную запись repl_snapshot.  
  
5.  Повторите предыдущий шаг, чтобы создать учетные записи repl_logreader, repl_distribution и repl_merge.  
  
6.  Щелкните **Закрыть**.  
  
### <a name="to-create-local-windows-accounts-for-replication-agents-at-the-subscriber"></a>Создание локальных учетных записей Windows для агентов репликации на подписчике  
  
1.  На подписчике откройте **оснастку «Управление компьютером** » из **меню «Администрирование** » на панели управления.  
  
2.  В оснастке **Служебные программы**разверните узел **Локальные пользователи и группы**.  
  
3.  Щелкните правой кнопкой мыши элемент **Пользователи** и выберите пункт **Новый пользователь**.  
  
4.  Введите `repl_distribution` в поле **имя пользователя** , укажите пароль и другие важные сведения, а затем нажмите кнопку **создать** , чтобы создать учетную запись repl_distribution.  
  
5.  Повторите предыдущий шаг, чтобы создать учетную запись repl_merge.  
  
6.  Щелкните **Закрыть**.  
  
## <a name="next-steps"></a>Next Steps  
 Создание учетных записей Windows для агентов репликации успешно выполнено. Далее предстоит настроить папку моментальных снимков. См. раздел [Занятие 2. Подготовка папки моментальных снимков](lesson-2-preparing-the-snapshot-folder.md).  
  
## <a name="see-also"></a>См. также:  
 [Replication Agents Overview](agents/replication-agents-overview.md)  
  
  
