---
title: Диалоговое окно "Свойства источника данных" — "Общие" | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasourceproperties.general.f1
- "10120"
ms.assetid: 44b5edd3-5c11-4d3d-91b8-5871aa0572ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f918d6583f01473e061792406821b13a4856cea
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109477"
---
# <a name="data-source-properties-dialog-box-general"></a>Диалоговое окно «Свойства источника данных» — «Общие»
  Вкладка **Общие** в диалоговом окне **Источник данных** позволяет просмотреть и изменить сведения о соединении источника данных с отчетом.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Введите имя источника данных. Имя источника данных должно быть уникальным в пределах отчета. По умолчанию источнику данных присваивается стандартное имя, например ИсточникДанных1 или ИсточникДанных2.  
  
 **Внедренное соединение**  
 Выберите этот параметр, если общий источник данных не нужен.  
  
 **Тип**  
 Выберите модуль обработки данных. В списке перечислены все зарегистрированные модули.  
  
 **Строка подключения**  
 Введите строку соединения для источника данных. Чтобы построить строку соединения с помощью диалогового окна **Свойства соединения** , нажмите кнопку **Изменить** . Нажмите кнопку **выражения** (*FX*), чтобы изменить выражение.  
  
 **Использовать ссылку на общий источник данных**  
 Выберите этот параметр, чтобы задать ссылку на общий источник данных. Выберите общий источник данных из раскрывающегося списка. Чтобы изменить выбранный источник данных, нажмите кнопку **Изменить**. Если установлен флажок **Использовать ссылку на общий источник данных** , флажки **Тип** и **Строка соединения** отключены.  
  
 **Использовать одну транзакцию при обработке запросов**  
 Выберите этот параметр, чтобы указать, что все наборы данных, использующие этот источник данных, запускаются в единой транзакции базы данных. Чтобы транзакции вложенного отчета использовали тот же источник данных, задайте для этого вложенного отчета в панели **Свойства** в разделе **Прочее** для свойства **MergeTransactions** значение **True** .  
  
## <a name="see-also"></a>См. также:  
 [Добавление данных в построитель отчетов &#40;отчетов и SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Создание внедренного или общего источника данных &#40;SSRS&#41;](../../2014/reporting-services/create-an-embedded-or-shared-data-source-ssrs.md)   
 [Подключения к данным, источники данных и строки подключения в Reporting Services](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-reporting-services.md)   
 [Диалоговое окно «Свойства источника данных» — «Учетные данные»](../../2014/reporting-services/data-source-properties-dialog-box-credentials.md)  
  
  
