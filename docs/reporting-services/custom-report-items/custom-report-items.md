---
title: Пользовательские элементы отчета | Документы Майкрософт
ms.date: 03/03/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: custom-report-items
ms.topic: reference
helpviewer_keywords:
- extending Reporting Services
- Reporting Services, extending
- custom report items
ms.assetid: 64dcaf2c-1af5-4937-8ff7-98f1ec3b367e
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: ee4b1e82ec3671cdc978c9af889d201ec430ed87
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "63194142"
---
# <a name="custom-report-items"></a>Пользовательские элементы отчета
  Службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] предлагают широкий выбор средств для построения и публикации отчетов предприятия, управления безопасностью и подписками. Эти средства позволяют расширить функциональные возможности по созданию отчетов через всеобъемлющий API-интерфейс. Отчеты определяются с помощью языка, основанного на языке XML, называемого языком определения отчетов Report Definition Language (RDL). Язык определения отчетов предоставляет ясный набор инструкций, описывающих макет, сведения о запросах и типы элементов для отчетов. Язык определения отчетов возможно расширить, создав пользовательские элементы отчетов. Пользовательский элемент отчета состоит из исполняемого компонента, который вызывается обработчиком отчетов во время выполнения, и компонента времени разработки, который делает пользовательский элемент отчета доступным в конструкторе отчетов.  
  
 Образец полностью реализованного пользовательского элемента отчета см. на странице [Образцы продуктов служб SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="custom-report-item-scenarios"></a>Сценарии применения пользовательских элементов отчета  
 Разработчикам, желающим интегрировать службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в собственные приложения, могут потребоваться функциональные возможности, не поддерживаемые языком определения отчетов. В их число могут входить следующие элементы: карты, горизонтальные списки, списки в столбцах и матрицы с возможностью сведения. Можно разработать пользовательский элемент отчета времени выполнения, а затем распространить его через приложение, которое удовлетворит потребности разработчиков.  
  
 В дополнение к предоставлению возможностей, которые изначально не поддерживались, некоторые разработчики могут захотеть расширить функциональные возможности, создав альтернативные версии элементов управления, изначально присутствовавших в службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. В данном сценарии разработчик может предоставить три компонента: компонент времени выполнения, компонент времени разработки и компонент преобразования элемента отчета времени разработки, по запросу преобразующий существующий элемент отчета в пользовательский элемент отчета.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Архитектура пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-architecture.md)  
 Описывает компоненты, из которых состоит пользовательский элемент отчета.  
  
 [Требования к реализации пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-implementation-requirements.md)  
 Описывает предварительные условия для создания пользовательского элемента отчета.  
  
 [Создание компонента времени выполнения пользовательского элемента отчета](../../reporting-services/custom-report-items/creating-a-custom-report-item-run-time-component.md)  
 Описывает процесс создания компонента времени выполнения пользовательского элемента отчета.  
  
 [Создание компонента времени разработки пользовательского элемента отчета](../../reporting-services/custom-report-items/creating-a-custom-report-item-design-time-component.md)  
 Описывает процесс создания компонента времени разработки пользовательского элемента отчета.  
  
 [Развертывание пользовательского элемента отчета](../../reporting-services/custom-report-items/how-to-deploy-a-custom-report-item.md)  
 Описывает процесс развертывания пользовательского элемента отчета.  
  
 [Библиотеки классов пользовательских элементов отчета](../../reporting-services/custom-report-items/custom-report-item-class-libraries.md)  
 Описывает классы инфраструктуры пользовательского элемента отчета и управляемые классы-оболочки в пространстве имен **Microsoft.ReportDesigner**.  
  
## <a name="see-also"></a>См. также:  
 [Технический справочник (службы SSRS)](../../reporting-services/technical-reference-ssrs.md)  
  
  
