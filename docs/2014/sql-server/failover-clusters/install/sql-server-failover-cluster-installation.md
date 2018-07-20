---
title: Установка отказоустойчивого кластера SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: c0e75a7c-85c5-423c-a218-77247bf071aa
caps.latest.revision: 7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9b11a175ddf9a7a12610c2f3588e4bbf42ac7802
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37317844"
---
# <a name="sql-server-failover-cluster-installation"></a>Установка отказоустойчивого кластера SQL Server
  Чтобы установить отказоустойчивый кластер [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо создать и настроить экземпляр отказоустойчивого кластера, запустив программу установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="installing-a-failover-cluster"></a>Установка отказоустойчивого кластера  
 Чтобы установить отказоустойчивый кластер, необходимо использовать учетную запись домена с разрешениями локального администратора с правом входа в качестве службы и действовать в составе операционной системы на всех узлах отказоустойчивого кластера. Чтобы установить отказоустойчивый кластер с помощью программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , нужно выполнить следующие шаги.  
  
1.  Для установки, настройки и обслуживания отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] применяется программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    -   Определить, какие сведения необходимы для создания экземпляра отказоустойчивого кластера (это могут быть дисковый ресурс кластера, IP-адреса и сетевое имя) и какие узлы могут быть использованы для перехода на другой отказоустойчивый кластер. Дополнительные сведения см. в следующих разделах:  
  
        -   [Подготовка к установке отказоустойчивого кластера](before-installing-failover-clustering.md)  
  
        -   [Вопросы безопасности при установке SQL Server](../../install/security-considerations-for-a-sql-server-installation.md)  
  
    -   Эти шаги по конфигурации должны быть выполнены до запуска программы установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , для их реализации необходимо использовать оснастку Windows «Администратор кластера». Для каждого экземпляра настраиваемого отказоустойчивого кластера необходимо иметь одну группу WSFC.  
  
    -   Операционная система должна соответствовать минимальным требованиям для этого продукта. Дополнительные сведения о требованиях к отказоустойчивому кластеру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] см. в разделе [Подготовка к установке отказоустойчивого кластера](before-installing-failover-clustering.md).  
  
2.  Добавление или удаление узлов из конфигурации отказоустойчивого кластера, не затрагивая другие узлы кластера. Дополнительные сведения см. на странице [Добавление и удаление узлов в отказоустойчивом кластере SQL Server (настройка)](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md).  
  
    -   Все узлы на отказоустойчивом кластере должны работать на одной платформе: либо на 32-разрядной, либо на 64-разрядной. Кроме того, на них должен работать один и тот же выпуск и версия операционной системы. Кроме того, 64-разрядные версии выпусков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должны быть установлены на 64-разрядном оборудовании, работающем под управлением 64-разрядных версий операционной системы Windows. В этой версии отсутствует поддержка WOW64 для отказоустойчивой кластеризации.  
  
3.  Указание нескольких IP-адресов для каждого экземпляра отказоустойчивого кластера. Для каждой подсети можно указать несколько IP-адресов. Если для одной подсети имеется несколько IP-адресов, то программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливает зависимость в «И». Если выполняется кластеризация узлов по нескольким подсетям, то программа установки [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] устанавливает зависимость в «ИЛИ».  
  
## <a name="includessnoversionincludesssnoversion-mdmd-failover-cluster-installation-options"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Параметры установки отказоустойчивого кластера  
  
##### <a name="option-1-integrated-installation-with-add-node"></a>Вариант 1. Интегрированная установка с добавлением узлов  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] состоит из двух шагов.  
  
1.  Создайте и настройте состоящий из одиночного узла экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . После завершения настройки узла готов полностью функциональный экземпляр отказоустойчивого кластера. В данный момент этот отказоустойчивый кластер не имеет высокого уровня готовности, поскольку в него входит только один узел.  
  
2.  На каждом узле, добавляемом к отказоустойчивому кластеру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запустите программу установки с функцией добавления узла.  
  
##### <a name="option-2-advancedenterprise-installation"></a>Вариант 2. Расширенная установка (для выпуска Enterprise)  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Расширенная установка (установка выпуска Enterprise) отказоустойчивого кластера состоит из двух шагов:  
  
1.  На каждом узле, который станет частью отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , запустите программу установки с функцией подготовки отказоустойчивого кластера. На этом шаге осуществляется подготовка узлов, предназначенных для кластеризации, но в конце шага экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не переводится в рабочий режим.  
  
2.  После завершения подготовки узлов к кластеризации запустите программу установки на узле, являющемся владельцем общего диска с функцией завершения создания отказоустойчивого кластера. На этом шаге выполняется настройка и завершается создание экземпляра отказоустойчивого кластера. После завершения этого шага появляется работающий экземпляр отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
    > [!NOTE]  
    >  Любой режим установки позволяет выполнить установку отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с несколькими узлами. После создания отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для добавления новых узлов в любом из режимов может быть использована функция добавления узлов.  
  
    > [!IMPORTANT]  
    >  Буква диска операционной системы для размещения [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] должна совпадать на всех узлах, добавленных к отказоустойчивому кластеру [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
#### <a name="ip-address-configuration-during-setup"></a>Настройка IP-адресов во время установки  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] дает возможность задать или изменить ресурсы IP-адресов при выполнении следующих действий.  
  
-   Интегрированная установка: [Создание отказоустойчивого кластера SQL Server (программа установки)](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   CompleteFailoverCluster (расширенная установка): [Создание отказоустойчивого кластера SQL Server (программа установки)](create-a-new-sql-server-failover-cluster-setup.md)  
  
-   Добавление узла: [Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
-   Удаление узла: [Добавление или удаление узлов отказоустойчивого кластера SQL Server (программа установки)](add-or-remove-nodes-in-a-sql-server-failover-cluster-setup.md)  
  
 **Примечание.** IP-адреса IPV6 не поддерживаются.  Если заданы адреса IPV4 и IPV6, то они рассматриваются как принадлежащие разным подсетям, и IPV6 подключаются первыми.  
  
##### <a name="includessnoversionincludesssnoversion-mdmd-multi-subnet-failover-cluster"></a>[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Отказоустойчивый кластер с несколькими подсетями  
 Можно задать зависимости «ИЛИ», когда узлы кластера принадлежат разным подсетям. Однако, для каждого узла отказоустойчивого кластера [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с несколькими подсетями должно быть указан хотя бы один IP-адрес возможного владельца.  
  
## <a name="see-also"></a>См. также  
 [Подготовка к установке отказоустойчивого кластера](before-installing-failover-clustering.md)   
 [Создание отказоустойчивого кластера SQL Server (программа установки)](create-a-new-sql-server-failover-cluster-setup.md)   
 [Установка SQL Server 2014 из командной строки](../../../database-engine/install-windows/install-sql-server-from-the-command-prompt.md)   
 [Обновление отказоустойчивого кластера SQL Server](../windows/upgrade-a-sql-server-failover-cluster-instance.md)  
  
  