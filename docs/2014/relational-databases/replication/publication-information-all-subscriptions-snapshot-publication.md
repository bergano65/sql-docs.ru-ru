---
title: Сведения о публикации, вкладка "Все подписки" (публикация моментального снимка) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.monitor.publicationinfo.allsubscriptions.snapshot.f1
ms.assetid: 7ce656c2-6e60-4625-8955-1daff641070c
caps.latest.revision: 28
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b8c9222429848dc89aa37e924c1206296782ab76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37158135"
---
# <a name="publication-information-all-subscriptions-snapshot-publication"></a>Сведения о публикации, вкладка «Все подписки» (публикация моментальных снимков)
  На вкладке **Все подписки** отображаются сведения обо всех подписках на выбранную публикацию моментальных снимков.  
  
## <a name="options"></a>Параметры  
 Для получения дополнительных сведений о подписке и о связанных с ней задачах щелкните правой кнопкой мыши на строке с этой подпиской, а затем выберите соответствующий параметр в контекстном меню. Чтобы изменить способ отображения данных в сетке, щелкните правой кнопкой мыши сетку, а затем один из следующих параметров.  
  
-   **Сортировать**: сортировка по одному или нескольким столбцам в диалоговом окне **Сортировка столбцов** .  
  
-   **Выберите столбцы для отображения**: выбор столбцов для отображения и порядка их отображения в диалоговом окне **Выбор столбцов** .  
  
-   **Фильтр**: фильтрация строк в сетке на основании значений столбцов в диалоговом окне **Параметры фильтра** .  
  
-   **Очистить фильтр**: удаление всех параметров фильтра для сетки.  
  
 Настройки фильтра уникальны для каждой сетки. Выбор и сортировка столбцов применяются ко всем сеткам одного типа, как, например, сетка публикаций для каждого издателя.  
  
 **Показать**  
 Только для сервера[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий. Выберите состояния подписки, которые должны отображаться для выбранного типа подписки. Например, можно выбрать отображение только тех подписок, которые содержат ошибку.  
  
 **Состояние**  
 Состояние каждой подписки, определяемое состоянием агента моментальных снимков или агента распространителя (отображается состояние с более высоким приоритетом).  
  
 По умолчанию, в сетке, содержащей сведения о подписках, они сортируются по столбцу **Состояние** . В следующем списке показаны возможные значения состояния и порядок сортировки значений (например, ошибки всегда показываются в верхней части сетки).  
  
-   Ошибка  
  
-   Срок действия скоро истекает или истек (только для версии[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий)  
  
-   Неинициализированная подписка ([!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздние версии)  
  
-   Повтор последней невыполненной команды  
  
-   Синхронизация  
  
-   Нет синхронизации  
  
 Порядок сортировки также определяет отображаемое значение, если данная подписка имеет более одного состояния. Например, если подписка содержит ошибку и срок ее действия скоро истекает, в столбце **Состояние** отображается **Ошибка**.  
  
 Значения состояний **Срок действия скоро истекает или истек** и **Неинициализированная подписка** являются предупреждениями. Когда выводится предупреждение, столбец **Состояние** также отображается при запущенном агенте. Например, возможно состояние **Выполняется, срок действия скоро истекает или истек**.  
  
 Значение состояния **Срок действия скоро истекает или истек** отображается только при установленном пороге. Дополнительные сведения об установке пороговых значений см. в статье [Настройка пороговых значений и предупреждений в мониторе репликации](monitor/set-thresholds-and-warnings-in-replication-monitor.md).  
  
 **Подписка**  
 Имя каждой подписки в виде: *имя_подписчика: имя_базы_данных_подписки*.  
  
 **Последняя синхронизация**  
 Время последнего запуска агента распространителя. Если в данный момент синхронизация выполняется, то выводится сообщение **Выполняется** .  
  
## <a name="see-also"></a>См. также  
 [Запуск монитора репликации](monitor/start-the-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для подписки (монитор репликации)](monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md)   
 [Просмотр сведений и выполнение задач для агентов, связанных с подпиской (монитор репликации)](monitor/view-information-and-perform-tasks-for-subscription-agents.md)   
 [Наблюдение за репликацией](monitoring-replication.md)  
  
  