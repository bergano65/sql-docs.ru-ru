---
title: Отключение регулятора ресурсов | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, disabling
ms.assetid: 2c2d2db0-34a5-4f50-b783-17693e3ce3f1
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 3b746c7ed116627f8fe57cdb43724c619eeb5dd4
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "72903931"
---
# <a name="disable-resource-governor"></a>Отключение регулятора ресурсов
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Регулятор ресурсов можно отключить в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью Transact-SQL.  
  
-   **Перед началом работы**  [ограничения](#LimitationsRestrictions), [разрешения](#Permissions)  
  
-   **Отключение Resource Governor с использованием:**  [обозревателя объектов](#RGOffObjEx), [свойств Resource Governor](#RGOffProp), [Transact-SQL](#RGOffTSQL)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
 В результате отключения регулятора ресурсов происходит следующее.  
  
-   Функция-классификатор не выполняется.  
  
-   Все новые соединения в результате классификации автоматически попадают в группу рабочей нагрузки по умолчанию.  
  
-   Инициированные системой запросы попадают во внутреннюю группу рабочей нагрузки.  
  
-   Все существующие параметры групп рабочей нагрузки и пулов ресурсов сбрасываются в значения по умолчанию. В этом случае при достижении ограничений не возникает никаких событий.  
  
-   Обычное наблюдение за системой не затрагивается.  
  
-   Изменения конфигурации можно вносить, но эти изменения не вступят в силу, пока не будет включен регулятор ресурсов.  
  
-   После перезапуска SQL Server регулятор ресурсов не будет загружать конфигурацию, а вместо этого будет иметь только применяемые по умолчанию внутренние группы рабочей нагрузки и пулы ресурсов.  
  
###  <a name="LimitationsRestrictions"></a> Ограничения  
 В пользовательской транзакции регулятор ресурсов нельзя отключить с помощью инструкции **ALTER RESOURCE GOVERNOR** .  
  
###  <a name="Permissions"></a> Permissions  
 Для отключения регулятора ресурсов требуется разрешение CONTROL SERVER.  
  
##  <a name="RGOffObjEx"></a> Отключение регулятора ресурсов с помощью обозревателя объектов  
 **Отключение регулятора ресурсов с помощью обозревателя объектов**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните элемент **Resource Governor**правой кнопкой мыши и выберите команду **Отключить**.  

##  <a name="RGOffProp"></a> Отключение регулятора ресурсов с помощью свойств регулятора ресурсов  
 **Отключение регулятора ресурсов с помощью страницы «Свойства регулятора ресурсов»**  
  
1.  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]откройте обозреватель объектов и рекурсивно разверните узел **Управление** вплоть до узла **Регулятор ресурсов**.  
  
2.  Щелкните правой кнопкой мыши **Регулятор ресурсов** и выберите пункт **Свойства**, после чего откроется страница **Свойства регулятора ресурсов** .  
  
3.  Щелкните флажок **Включить регулятор ресурсов** , убедитесь в том, что этот флажок не выбран, и нажмите кнопку **ОК**.  
  
##  <a name="RGOffTSQL"></a> Отключение регулятора ресурсов с помощью Transact-SQL  
 **Отключение регулятора ресурсов с помощью Transact-SQL**  
  
1.  Выполните инструкцию **ALTER RESOURCE GOVERNOR DISABLE** .  
  
### <a name="example-transact-sql"></a>Пример (Transact-SQL)  
 В следующем примере показано включение регулятора ресурсов.  
  
```  
ALTER RESOURCE GOVERNOR DISABLE;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [регулятор ресурсов](../../relational-databases/resource-governor/resource-governor.md)   
 [Активация регулятора ресурсов](../../relational-databases/resource-governor/enable-resource-governor.md)   
 [Пул ресурсов регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-resource-pool.md)   
 [Группа рабочей нагрузки регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-workload-group.md)   
 [Функция-классификатор регулятора ресурсов](../../relational-databases/resource-governor/resource-governor-classifier-function.md)   
 [ALTER RESOURCE GOVERNOR (Transact-SQL)](../../t-sql/statements/alter-resource-governor-transact-sql.md)  
  
  
