---
title: Свойства служб Reporting Services | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- properties [Reporting Services], about properties
- reports [Reporting Services], properties
- Report Server Web service, properties
- report properties [Reporting Services]
- XML Web service [Reporting Services], properties
- Web service [Reporting Services], properties
- properties [Reporting Services]
ms.assetid: 8c855194-4c20-4ecc-a328-5137d54b560c
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 36a105d3220755dd03ff05a50dd403d4bac25d3a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "62703833"
---
# <a name="reporting-services-properties"></a>Свойства служб Reporting Services
  Сервер отчетов определяет набор системных свойств, являющихся глобальными для сервера отчетов, и набор свойств элементов, связанных с отдельным элементом, хранимым в базе данных сервера отчетов. Свойства, определенные сервером отчетов, не могут быть удалены; в некоторых случаях они доступны только для чтения. Приложение может расширить системные свойства и свойства элементов, добавив к ним дополнительные определяемые пользователем свойства.  
  
 Указанные ниже методы веб-служб возвращают и задают свойства [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Метод|Действие|  
|------------|------------|  
|<xref:ReportService2010.ReportingService2010.GetProperties%2A>|Возвращает значения одного или нескольких свойств элемента в базе данных сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>|Возвращает одно или несколько системных свойств.|  
|<xref:ReportService2010.ReportingService2010.SetProperties%2A>|Задает одно или несколько свойств элемента в базе данных сервера отчетов.|  
|<xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>|Задает одно или несколько системных свойств.|  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Свойства элемента сервера отчетов](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-item-properties.md)|Описывает характерные для элементов свойства в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
|[Системные свойства сервера отчетов](../../../reporting-services/report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md)|Описывает характерные для системы свойства в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].|  
  
## <a name="see-also"></a>См. также:  
 [Создание приложений с помощью веб-службы и .NET Framework](../../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)   
 [Веб-служба сервера отчетов](../../../reporting-services/report-server-web-service/report-server-web-service.md)   
 [Технический справочник (службы SSRS)](../../../reporting-services/technical-reference-ssrs.md)  
  
  
