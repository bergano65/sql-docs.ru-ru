---
title: Версии
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- version flags [Master Data Services], about version flags
- versions [Master Data Services]
- version flags [Master Data Services]
- versions [Master Data Services], version flags
ms.assetid: 752ec96d-53d7-4160-8ed2-92e0324645f3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 700878062dc302296dd827fb5e7db9b52c4286f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73727794"
---
# <a name="versions-master-data-services"></a>Версии (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  В среде [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]можно создать несколько версий основных данных в модели. Версии могут быть заблокированы до проведения проверки данных и будут зафиксированы после проверки данных. Зафиксированные версии образуют запись аудита об изменениях. Каждая созданная версия содержит все элементы, значения атрибутов, элементы иерархии, отношения в иерархии и коллекции для модели.  
  
## <a name="when-to-use-versions"></a>Использование версий  
 Версии используются:  
  
-   для ведения доступной для аудита записи основных данных при их изменении;  
  
-   предотвращения изменений пользователями и обеспечения допустимости данных в соответствии с бизнес-правилами;  
  
-   блокировки модели для использования системами-подписчиками;  
  
-   проверки разных иерархий без немедленной их реализации.  
  
> [!NOTE]  
>  При изменении структуры модели, например при создании новой сущности или атрибута на основе домена, это изменение применяется ко всем версиям. Если просматривается более ранняя версия модели, то сущность или атрибут отображается, но для него отсутствуют данные.  
  
## <a name="version-flags"></a>Флаги версии  
 Когда версия готова для пользователей или системы-подписчика, можно установить флаг для идентификации версии. При необходимости этот флаг можно переносить от версии к версии. Флаги помогают пользователям и системам-подписчикам определять используемую версию модели.  
  
## <a name="workflow-for-version-management"></a>Рабочий процесс для управления версией  
 Используйте следующий рабочий процесс для управления версиями:  
  
1.  Начальная версия создается автоматически при создании модели и наполнении базы данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] основными данными компании. На основании разрешений пользователи могут при необходимости вносить изменения в эту версию.  
  
2.  Когда необходимо зафиксировать версию модели, заблокируйте ее, чтобы только администраторы модели могли обновлять данные. Дополнительные сведения см. в статье [Администраторы (службы Master Data Services)](../master-data-services/administrators-master-data-services.md). Если настраиваются уведомления, то администратору модели по электронной почте направляются уведомления каждый раз, когда изменяется состояние версии. Дополнительные сведения см. в разделе [Настройка уведомления электронной почты (службы Master Data Services)](../master-data-services/configure-email-notifications-master-data-services.md).  
  
3.  Примените бизнес-правила к данным заблокированной версии и просмотрите все ошибки, обнаруженные при проверке. При необходимости можно внести отсутствующие данные или восстановить транзакции, которые привели к возникновению ошибки. Можно также разблокировать версию, чтобы пользователи могли вносить изменения.  
  
4.  После успешной проверки всех данных зафиксируйте версию и пометьте для использования системами-подписчиками. Вносить изменения в зафиксированную версию нельзя.  
  
5.  Скопируйте зафиксированную версию и уведомите пользователей, что они могут начать работать с новой версией модели.  
  
## <a name="sequential-or-simultaneous-versions"></a>Последовательные или одновременные версии  
 Можно создавать последовательные или одновременные версии модели.  
  
-   **Последовательные версии.** Каждый раз при фиксации версии можно создать новую копию и назначить версии следующий последовательный номер. Например, можно скопировать **Версию 7** модели и назвать копию **Версия 8**.  
  
-   **Одновременные версии.** При необходимости работать с одной или несколькими версиями данных одновременно создайте одновременные версии модели. Это полезно, когда в компании происходят реорганизации или слияния, которые осуществляются в ходе обычной деятельности компании, и необходимо определить, как новые основные данные подойдут к существующим структурам.  
  
    > [!NOTE]  
    >  Параметр в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] определяет возможность копирования для всех версий или только для зафиксированных. Для создания одновременных версий необходимо выполнить настройку [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , чтобы можно было скопировать все версии. Этот параметр также присутствует в таблице системных настроек. Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="related-tasks"></a>Связанные задачи  
  
|Описание задачи|Раздел|  
|----------------------|-----------|  
|Изменение имени существующей версии.|[Изменение имени версии &#40;Master Data Services&#41;](../master-data-services/change-a-version-name-master-data-services.md)|  
|Блокирование версии, чтобы изменять ее данные могли только администраторы.|[Блокировка &#40;версии Master Data Services&#41;](../master-data-services/lock-a-version-master-data-services.md)|  
|Разблокирование версии, чтобы изменять ее данные могли пользователи.|[Разблокировка версии Master Data Services &#40;&#41;](../master-data-services/unlock-a-version-master-data-services.md)|  
|Фиксирование версии после проверки всех данных.|[Фиксация &#40;версии Master Data Services&#41;](../master-data-services/commit-a-version-master-data-services.md)|  
|Создание нового флага для обозначения версии.|[Создание флага версии &#40;Master Data Services&#41;](../master-data-services/create-a-version-flag-master-data-services.md)|  
|Изменение имени для существующего флага версии.|[Измените имя флага версии &#40;Master Data Services&#41;](../master-data-services/change-a-version-flag-name-master-data-services.md)|  
|Назначение существующего флага для версии.|[Назначение флага версии &#40;Master Data Services&#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)|  
|Создание новой копии для существующей версии|[Копирование Master Data Services &#40;версии&#41;](../master-data-services/copy-a-version-master-data-services.md)|  
|Удаление существующей версии.|[Удаление &#40;версии Master Data Services&#41;](../master-data-services/delete-a-version-master-data-services.md)|  
|Очистка обратимо удаленных элементов из версии|[Очистка членов версии &#40;Master Data Services&#41;](../master-data-services/purge-version-members-master-data-services.md)|  
  
## <a name="related-content"></a>См. также  
  
-   [Отмена Master Data Services &#40;транзакций&#41;](../master-data-services/reverse-a-transaction-master-data-services.md)  
  
-   [Master Data Services &#40;уведомлений&#41;](../master-data-services/notifications-master-data-services.md)  
  
-   [Бизнес-правила &#40;Master Data Services&#41;](../master-data-services/business-rules-master-data-services.md)  
  
  
