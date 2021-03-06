---
title: Задать Active Directory пароль
description: Задайте Active Directory узлов пароль администратора в режиме восстановления служб каталогов в системе аналитики (ТД).
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 6bbbf42106602a25b03072a9c9abfb04f04d3c49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400334"
---
# <a name="set-admin-password-for-logging-on-to-ad-nodes-in-directory-services-restore-mode-dsrm---analytics-platform-system"></a>Настройка пароля администратора для входа на узлы AD в режиме восстановления служб каталогов (DSRM) — система платформы аналитики
Режим восстановления служб каталогов (DSRM) — это режим загрузки для восстановления или восстановления домен Active Directory служб (AD DS). Он используется для входа на узлы AD устройств после сбоя AD DS или при необходимости восстановления AD DS. Пароль для DSRM был инициализирован во время настройки устройства на сайте поставщика оборудования и должен быть изменен администратором устройства. Система аналитики платформы имеет два AD DS (контроллеры домена); ** _appliance_domain_-AD01** и ** _appliance_domain_-AD02**. Для каждого узла AD устройства Active Directory измените пароль DSRM, выполнив следующие действия.  
  
## <a name="HowToDSRM"></a>Сброс пароля администратора  
  
1.  Откройте окно командной строки на узле AD устройства <strong> _appliance_domain_-AD_xx_</strong>виртуальной машине.  
  
2.  В командной строке выполните следующую команду: `ntdsutil`.  
  
3.  В командной строке **ntdsutil** введите `set dsrm password`.  
  
4.  В командной строке **Сброс пароля администратора:** введите `reset password on server null`.  
  
5.  В командной строке введите новый пароль.  
  
6.  Повторите шаги 1-5 выше для каждой виртуальной машины устройства AD.  
  
    > [!WARNING]  
    > Система аналитики платформы не поддерживает знак доллара ($) в паролях администратора домена или локального администратора. Пароль, содержащий знак доллара, будет проверяться и быть пригодным для использования, но может блокировать операции обновления и обслуживания.  
  
> [!NOTE]  
> Если службы домен Active Directory или виртуальная машина повреждены для конкретной виртуальной машины AD, то рекомендуется выполнить действия по исправлению, запустив **реплацевм** для затронутой ВИРТУАЛЬНОЙ машины AD. Обратитесь в службу поддержки пользователей.  
  
## <a name="see-also"></a>См. также:  
[&#40;&#41;системы аналитики для сброса пароля](password-reset.md)  
  
