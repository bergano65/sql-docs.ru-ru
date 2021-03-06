---
title: Страница «Создание модели» (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b9fdcac2499cdf33d98ba636596218c14704f9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108210"
---
# <a name="new-model-page-report-manager"></a>Страница «Создание модели» (диспетчер отчетов)
  Эта страница позволяет создать модель отчетов по умолчанию на основе общего источника данных. Модели отчетов можно создавать только из многомерных источников данных службы [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , реляционных источников данных [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и реляционных источников данных Oracle.  
  
 Модели, создаваемые в диспетчере отчетов, основаны на схеме общего источника данных. Для всех таблиц и столбцов источника данных создаются сущности, папки и поля. Исключать элементы нельзя, и невозможно задавать параметры, определяющие способ создания модели. Если модель необходимо настроить или уточнить, вместо этого следует использовать конструктор моделей.  
  
## <a name="navigation"></a>Навигации  
 Чтобы перейти к этому местоположению в пользовательском интерфейсе, используйте следующую процедуру.  
  
###### <a name="to-open-the-new-model-page"></a>Открытие страницы «Создать модель»  
  
1.  Откройте диспетчер отчетов и найдите общий источник данных, с помощью которого необходимо создать модель.  
  
2.  Подведите курсор к источнику данных и щелкните стрелку раскрывающегося списка.  
  
3.  В раскрывающемся меню выполните одно из следующих действий:  
  
    -   Нажмите кнопку **Создать модель отчета** , чтобы открыть страницу «Создать модель».  
  
    -   Выберите **Управление** , чтобы открыть страницу свойств отчета «Общие». Затем нажмите кнопку **Создать модель отчета** , чтобы открыть страницу «Создать модель».  
  
## <a name="options"></a>Параметры  
 **Название**  
 Указывает имя модели. Имя должно содержать хотя бы одну букву или цифру. В него могут также входить пробелы и другие символы. При задании имени нельзя использовать следующие символы:  
  
 ; ? : \@ & = +, $/* \< > | " /  
  
 **Описание**  
 Показывает описание модели. Пользователям, просматривающим этот элемент с помощью диспетчера отчетов, это описание предоставляется при просмотре иерархии папок.  
  
 **Изменение местоположения**  
 Показывает папку, в которой будет размещена новая модель. Чтобы выбрать другое местоположение, нажмите кнопку **Изменить местоположение** .  
  
  
