---
title: Свойства базы данных (страница "Доставка журналов транзакций") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.f1
ms.assetid: 72c4e539-fe11-4d57-b977-65b418d5916f
caps.latest.revision: 20
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9ac02b81f80194c307e34ef385b332512c2c10d3
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37175941"
---
# <a name="database-properties-transaction-log-shipping-page"></a>Свойства базы данных (страница «Доставка журналов транзакций»)
  Используйте эту страницу, чтобы настроить и изменить свойства доставки журналов базы данных.  
  
 Основные сведения о доставке журналов изложены в статье [Сведения о доставке журналов (SQL Server)](../../database-engine/log-shipping/about-log-shipping-sql-server.md).  
  
## <a name="options"></a>Параметры  
 **Включить эту базу данных в качестве источника в конфигурацию доставки журналов**  
 Включает эту базу данных в качестве источника для доставки журналов. Выберите этот пункт и затем настройте остальные параметры на этой странице. Если снять этот флажок, конфигурация доставки журналов для этой базы данных будет сброшена.  
  
 **Параметры копирования**  
 Нажмите кнопку **Параметры копирования** , чтобы настроить параметры расписания резервного копирования, расположения, предупреждений и архивирования.  
  
 **Расписание копирования**  
 Показывает выбранное в настоящий момент расписание резервного копирования для базы данных-источника. Нажмите кнопку **Параметры копирования** , чтобы изменить эти настройки.  
  
 **Последняя резервная копия создана**  
 Указывает время и дату создания последней резервной копии журнала транзакций базы данных-источника.  
  
 **Экземпляры сервера-получателя и базы данных**  
 Перечисляет настроенные в настоящий момент серверы-получатели и базы данных-получатели для этой базы данных-источника. Выделите базу данных, а затем нажмите кнопку вызова диалогового окна, обозначенную многоточием **...** , чтобы изменить параметры, связанные с этой базой данных-получателем.  
  
 **Добавить**  
 Нажмите кнопку **Добавить** , чтобы добавить базу данных-получатель в конфигурацию доставки журналов для этой базы данных-источника.  
  
 **Удалить**  
 Удаляет выбранную базу данных из этой конфигурации доставки журналов. Сначала выберите базу данных, а затем нажмите кнопку **Удалить**.  
  
 **Использовать экземпляр сервера мониторинга**  
 Устанавливает экземпляр сервера мониторинга для этой конфигурации доставки журналов. Установите флажок **Использовать экземпляр сервера мониторинга** , затем выберите пункт **Настройки** , чтобы указать экземпляр сервера мониторинга.  
  
 **Экземпляр сервера мониторинга**  
 Указывает настроенный в настоящий момент экземпляр сервера мониторинга для этой конфигурации доставки журналов.  
  
 **Настройки**  
 Настраивает экземпляр сервера мониторинга для конфигурации доставки журналов. Выберите пункт **Настройки** , чтобы настроить экземпляр сервера мониторинга.  
  
 **Скрипт конфигурации**  
 Создает скрипт для настройки доставки журналов с выбранными параметрами. Нажмите кнопку **Скрипт конфигурации**, а затем выберите выходное назначение для скрипта.  
  
> [!IMPORTANT]  
>  До создания сценария настройки для базы данных-получателя необходимо вызвать диалоговое окно **Настройки базы данных-получателя** . При вызове этого диалогового окна выполняется подключение к серверу-получателю и получение текущих настроек базы данных-получателя, необходимых для создания скрипта.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры доставки журналов (Transact-SQL)](/sql/relational-databases/system-stored-procedures/log-shipping-stored-procedures-transact-sql)   
 [Таблицы доставки журналов (Transact-SQL)](/sql/relational-databases/system-tables/log-shipping-tables-transact-sql)  
  
  