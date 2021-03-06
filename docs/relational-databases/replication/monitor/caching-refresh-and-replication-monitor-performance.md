---
title: Кэширование, обновление и производительность монитора репликации
description: Сведения о кэшировании, обновлении и оптимизации производительности монитора репликации в SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server replication], Replication Monitor
- cache [SQL Server], replication
- Replication Monitor, caching
- refreshing data
- Replication Monitor, refreshing
ms.assetid: a2d8b666-ed41-4f86-b2b8-c8e118416ab7
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 45cad9f38fadd8280b6cb155c0e44643448ac4bf
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76286354"
---
# <a name="caching-refresh-and-replication-monitor-performance"></a>Кэширование, обновление и производительность монитора репликации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Монитор репликации [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предназначен для эффективного наблюдения за большим количеством компьютеров в рабочей системе. Запросы, которые монитор репликации использует для выполнения вычислений и сбора данных, периодически кэшируются и обновляются. Кэширование уменьшает количество запросов и вычислений, необходимых для просмотра разных страниц в мониторе репликации и позволяет вести наблюдение за несколькими пользователями.  
  
 Обновление кэша обрабатывается заданием агента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] — **Обновитель монитора репликации для распространения**. Задание выполняется постоянно, однако расписание обновления кэша основано на определенном времени ожидания после предыдущего обновления:  
  
-   Если с момента последнего создания кэша происходили изменения в истории агента, время ожидания устанавливается по меньшему из следующих периодов: 4 секунды или длительность создания предыдущей версии кэша.  
  
-   Если с момента последнего создания кэша не было изменений в истории агента (допускаются другие изменения), время ожидания устанавливается по большему из следующих периодов: 30 секунд или длительность создания предыдущей версии кэша.  
  
## <a name="refreshing-the-replication-monitor-user-interface"></a>Обновление пользовательского интерфейса монитора репликации  
 Пользовательский интерфейс монитора репликации может обновляться следующими способами:  
  
-   Главное окно монитора репликации (включая все вкладки) по умолчанию обновляется автоматически каждые пять секунд. Автоматические обновления не выполняют принудительного обновления кэша. Пользовательский интерфейс отображает самую последнюю версию данных из кэша. Настроить частоту обновлений, используемую для всех окон, связанных с издателем, можно с помощью редактирования параметров издателя. Можно также отключить автоматические обновления для издателя.  
  
-   Окна сведений, запускаемые из монитора репликации (за исключением окон, связанных с синхронизируемыми подписками слиянием), не обновляются по умолчанию автоматически. Если указать, что окна сведений должны обновляться автоматически, они будут обновляться в соответствии с тем же расписанием, что и главное окно монитора репликации.  
  
-   Все окна можно обновлять вручную. Для этого следует нажать клавишу F5 или щелкнуть правой кнопкой мыши узел в дереве монитора репликации и выбрать **Обновить**. Обновления, осуществляемые вручную, выполняют принудительное обновление кэша.  
  
 Дополнительные сведения об обновлении данных в мониторе репликации см. в [этой статье](../../../relational-databases/replication/monitor/refresh-data-in-replication-monitor.md).  
  
## <a name="performance-considerations"></a>Вопросы производительности  
 Хотя монитор репликации разработан так, чтобы обеспечивать эффективную работу, необходимо придерживаться следующих правил:  
  
-   При наличии большого числа публикаций или подписок рассмотрите возможность установки расписания с более редкими автоматическими обновлениями пользовательского интерфейса.  
  
-   Избегайте одновременного запуска нескольких экземпляров монитора репликации.  
  
-   Избегайте регистрации большого числа распространителей и установки монитора репликации для автоматического подключения к ним.  
  
## <a name="see-also"></a>См. также:  
 [Запуск задания по обслуживанию репликаций (среда SQL Server Management Studio)](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md)   
 [Наблюдение за репликацией](../../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
