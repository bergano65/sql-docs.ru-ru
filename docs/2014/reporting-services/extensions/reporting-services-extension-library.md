---
title: Библиотека модулей служб Reporting Services | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- namespaces [Reporting Services]
- Reporting Services, extending
- extensions [Reporting Services], library
- library [Reporting Services]
ms.assetid: e8eff470-64d6-41c3-b98b-5ec916c121c3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d09464ce4a61903a3e9b74711482d2ce07bd0c4e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62985753"
---
# <a name="reporting-services-extension-library"></a>Библиотека модулей служб Reporting Services
  Библиотека модулей служб Reporting Services — это набор классов, интерфейсов и типов значений, включенных в службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Эта библиотека предоставляет доступ к функциональным возможностям системы и предназначена для того, чтобы стать основой [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] , в которой приложения могут расширять [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] компоненты.  
  
## <a name="namespaces"></a>Пространства имен  
 Библиотека модулей служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] содержит следующие пространства имен.  
  
 <xref:Microsoft.ReportingServices.DataProcessing>  
 Содержит классы и интерфейсы, которые позволяют строить компоненты, расширяющие возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по обработке данных.  
  
 <xref:Microsoft.ReportingServices.Interfaces>  
 Содержит классы и интерфейсы, которые позволяют создавать и отправлять пользователям нестандартные уведомления с помощью собственных модулей доставки, а также строить настраиваемые модули безопасности для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
 `Microsoft.ReportingServices.ReportRendering`  
 Содержит классы и интерфейсы, которые позволяют расширить возможности служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] по подготовке отчетов к просмотру. С помощью элементов этого пространства имен вместе с элементами пространства имен <xref:Microsoft.ReportingServices.Interfaces> можно строить пользовательские модули подготовки отчетов для служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Модули служб Reporting Services](reporting-services-extensions.md)  
  
  
