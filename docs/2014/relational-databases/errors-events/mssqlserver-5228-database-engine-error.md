---
title: MSSQLSERVER_5228 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dfbfa64cb61332591fadef874b8c73da3ce1e7c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62913753"
---
# <a name="mssqlserver_5228"></a>MSSQLSERVER_5228
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|5228|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_ANTIMATTER_COLUMN_DETECTED|  
|Текст сообщения|Ошибка таблицы: идентификатор объекта O_ID, идентификатор индекса I_ID, идентификатор секции PN_ID, идентификатор единицы распределения A_ID (тип TYPE), страница PG_ID, строка R_ID. При проверке DBCC обнаружен незавершенный процесс очистки после операции построения индекса в сети. (Значение виртуального столбца — VALUE.)|  
  
## <a name="explanation"></a>Объяснение  
 Для объекта *O_ID*, индекса *I_ID* и секции *PN_ID* обнаружено незавершенное построение индекса в режиме "в сети". Это подтверждается наличием виртуальных столбцов в строке *R_ID*. Виртуальный столбец используется для сверки записей из нескольких источников при построении индекса в режиме «в сети». Сообщение об ошибке также указывает на значение такого столбца.  
  
## <a name="user-action"></a>Действие пользователя  
  
### <a name="look-for-hardware-failure"></a>Поиск сбоев оборудования  
 Выполните диагностику оборудования и исправьте все найденные проблемы. Кроме того, просмотрите журнал системы [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows и журнал приложений, а также журнал ошибок [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], чтобы определить, была ли ошибка вызвана сбоем оборудования. Исправьте все неполадки оборудования, обнаруженные в журналах.  
  
 Если постоянно возникают проблемы с повреждением данных, попробуйте изменить некоторые компоненты оборудования, чтобы локализовать проблему. Убедитесь, что в системе не включено кэширование записи для контроллера дисков. Если есть подозрение, что неполадки вызваны кэшированием записи, обратитесь к поставщику оборудования.  
  
 В конце концов можно попробовать сменить оборудование. Это может включать форматирование дисков и переустановку операционной системы.  
  
### <a name="restore-from-backup"></a>Восстановление из резервной копии  
 Если неполадка не связана с оборудованием и есть безошибочная резервная копия, восстановите базу данных из этой копии.  
  
### <a name="run-dbcc-checkdb"></a>Запуск DBCC CHECKDB  
 Если безошибочной резервной копии нет, выполните инструкцию DBCC CHECKDB без предложения REPAIR, чтобы определить степень повреждения. Инструкция DBCC CHECKDB выдаст рекомендацию по тому, какое предложение REPAIR следует использовать. После этого выполните инструкцию DBCC CHECKDB с соответствующим предложением REPAIR, чтобы устранить повреждение.  
  
> [!CAUTION]  
>  Если достоверно неизвестно, к каким последствиям приведет выполнение инструкции DBCC CHECKDB с выбранным предложением REPAIR, перед выполнением этой инструкции обратитесь к вашему основному поставщику услуг технической поддержки.  
  
 Если в результате выполнения инструкции DBCC CHECKDB с одним из предложений REPAIR неполадка устранена не была, обратитесь к вашему основному поставщику услуг технической поддержки.  
  
### <a name="results-of-running-repair-options"></a>Результаты выполнения инструкции REPAIR  
 Запуск инструкции REPAIR приведет к перестроению указанного индекса и всех зависимых индексов.  
  
## <a name="see-also"></a>См. также:  
 [DBCC CHECKDB (Transact-SQL)](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
