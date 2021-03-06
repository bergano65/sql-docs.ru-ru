---
title: Глобальные параметры (Tester) (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4acc0f2a-85ba-4c99-856a-89030f5c418e
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: f7e421774d3a09622835b181d5c053c994e905ee
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68264413"
---
# <a name="global-settings-tester-oracletosql"></a>Глобальные параметры (средство тестирования) (OracleToSQL)
Страница «испытатель» диалогового окна « **глобальные параметры** » используется для указания параметров для тестера SSMA.  
  
Чтобы получить доступ к параметрам тестера, в меню **Сервис** выберите **глобальные параметры**и щелкните **Тестер** в нижней части левой панели.  
  
## <a name="options"></a>Параметры  
**Тестовый анализ объектов**  
Этот параметр указывает, следует ли выполнять анализ тестируемых объектов. Выберите **Да** , если вы хотите, чтобы тест-инженер SSMA проанализировал и автоматически проверит зависимые объекты. Параметр по умолчанию имеет значение **Да**.  
  
Для этого параметра доступны следующие параметры:  
  
1.  Да  
  
2.  нет  
  
**Режим сохранения вспомогательных таблиц**  
Этот параметр указывает, как сохранять внутренние вспомогательные таблицы, созданные во время выполнения тестового случая. Для этого конкретного параметра можно задать следующие параметры:  
  
1.  Всегда удалять  
  
2.  Всегда сохранять  
  
3.  Сохранить при сбое сравнения таблиц  
  
4.  Запрашивать пользователя, если произошел сбой при сравнении таблиц  
  
Параметр по умолчанию имеет значение: **всегда удалять**.  
  
**Выполнение отката данных**  
Этот параметр указывает, следует ли выполнять операцию отката после выполнения каждого тестового случая. Параметр по умолчанию имеет значение **No**.  
  
Для этого параметра доступны следующие параметры:  
  
1.  Да  
  
2.  нет  
  
**Прерывать выполнение теста после первого сбоя**  
Этот параметр указывает, следует ли прерывать текущий выполняющийся тестовый случай, если во время выполнения произошла ошибка. Параметр по умолчанию имеет значение **Да**.  
  
Для этого параметра доступны следующие параметры:  
  
1.  Да  
  
2.  нет  
  
## <a name="see-also"></a>См. также:  
[Завершение подготовки тестового случая &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
  
