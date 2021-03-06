---
title: Задача 17. Просмотр проекта очистки DQS, созданного с помощью пакета служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: fc6cc258-72f5-4593-8edb-9f5bc66de9db
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 285eae7ea20d5919fa73bd0d514c755fe73d9de0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484713"
---
# <a name="task-17-reviewing-dqs-cleansing-project-created-by-the-ssis-package"></a>Задача 17. Обзор проекта очистки данных DQS, созданного пакетом служб SSIS
  В этой задаче вы откроете проект служб DQS, созданный пакетом служб SSIS в клиенте DQS, просмотрите результаты очистки и при желании выполните интерактивную очистку и экспортируете результаты.  
  
1.  Запустите **Data Quality Client**.  
  
2.  Щелкните **мониторинг активности** в области **Администрирование** .  
  
3.  Отсортируйте список на основе **времени начала действия** , чтобы просмотреть последнюю запись.  
  
4.  Обратите внимание, что имя проекта отображается в следующем формате: **CleanseAndCurate. Очистка данных поставщика. GUID**.  
  
     ![Проект очистки DQS, созданный пакетом SSIS](../../2014/tutorials/media/et-reviewingdqscpcreatedbythessispackage.jpg "Проект очистки DQS, созданный пакетом SSIS")  
  
5.  Обратите внимание, что значение **в поле активно** . ****  
  
6.  Щелкните вкладку **профилировщик** в нижней области, чтобы просмотреть статистику профилировщика для действия Очистка, выполненного пакетом служб SSIS.  
  
7.  Нажмите кнопку **Закрыть** , чтобы закрыть экран **Администрирование** .  
  
8.  На главной странице **клиента DQS**щелкните **Открыть проект качества данных** в области **проекты качества данных** .  
  
9. В списке проектов выберите проект, созданный компонентом «Очистка данных DQS» пакета служб SSIS. Имя проекта должно быть в формате: **CleanseAndCurate. Очистка данных поставщика. GUID (красный цвет)**. Возможно, потребуется отсортировать список на основе столбца **Date Created** и найти последнюю запись.  
  
10. Щелкните **Далее**.  
  
11. Страница " **Управление результатами" и "Просмотр результатов** " должна быть знакома с интерактивной очистки, которая выполнялась ранее в этом учебнике.  
  
12. Просмотрите результаты очистки. Вы также можете провести интерактивную очистку и экспортировать результаты в файл Excel или в базу данных на следующей странице.  
  
13. Щелкните **Далее**. На этой странице **экспорта** можно экспортировать результаты в файл Excel, в CSV-файл или в базу данных SQL.  
  
14. Нажмите кнопку **Готово** , чтобы завершить работу.  
  
15. На главной странице **клиента DQS**щелкните **мониторинг активности** в области **Администрирование** .  
  
16. Обратите внимание, что **значение поля "** штат \" для проекта **завершено** .  
  
## <a name="next-step"></a>Дальнейшее действие  
 [Заключение](../../2014/tutorials/conclusion.md)  
  
  
