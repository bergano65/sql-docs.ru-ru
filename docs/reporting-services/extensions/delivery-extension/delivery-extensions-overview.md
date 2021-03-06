---
title: Общие сведения о модулях доставки | Документы Майкрософт
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- subscriptions [Reporting Services], delivery extensions
- delivery extensions [Reporting Services], about extensions
ms.assetid: a30600a9-bbed-4519-9426-3470ff2982e7
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 69dce8309f96988a9d339aefbb684116c0df2eb4
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "63193786"
---
# <a name="delivery-extensions-overview"></a>Общие сведения о модулях доставки
  С помощью среды [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] пользователи могут создавать и публиковать отчеты, которые затем можно доставлять в различные места. Кроме того, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] содержат несколько модулей доставки и API-интерфейс доставки, который позволяет разработчикам создавать дополнительные модули доставки, расширяя возможности доставки в службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 В следующей таблице перечислены модули доставки, входящие в состав служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
|Модуль доставки|Описание|  
|------------------------|-----------------|  
|Электронная почта сервера отчетов|Отправляет отчеты отдельным пользователям или группам пользователей по электронной почте через SMTP-сервер.|  
|Общая папка сервера отчетов|Используется для распространения отчетов по организации с использованием сетевых общих папок. Дает возможность автоматически копировать отчет в общую папку по заданному расписанию.|  
  
 ![Архитектура модуля доставки Reporting Services](../../../reporting-services/extensions/delivery-extension/media/bk-reportservicedelivery.gif "Архитектура модуля доставки служб Reporting Services")  
Архитектура модуля доставки служб Reporting Services  
  
 Подпискам ставятся в соответствие модули доставки. При создании подписки, чтобы определить порядок доставки отчета, пользователь может выбрать один из доступных модулей доставки. В службах [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] подписки располагаются в базе данных сервера отчетов. Когда происходит событие, службы [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] проверяет событие по подпискам, содержащимся в базе данных сервера отчетов. Для каждой подписки, сопоставленной с событием, сервер отчетов создает уведомление. Для управляемых данными подписок уведомление создается для каждого получателя. После создания уведомления сервер отчетов вызывает определенный модуль доставки и передает для параметров модуля значения, указанные в уведомлении. Модуль доставки отправляет уведомление пользователю, как указано в выбранном модуле доставки.  
  
 В модулях доставки реализуется API-интерфейс модулей доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. За счет поддержки API-интерфейса модулей доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] модули доставки имеют возможность получать уведомления от сервера отчетов и указывать состояние уведомления.  
  
 Сервер отчетов не управляет назначением доставки для уведомлений и отчетов. Сбор сведений о назначении выполняется кодом, который включается в модуль доставки.  
  
## <a name="subscriptions-and-delivery-extensions"></a>Подписки и модули доставки  
 Клиентские приложения создают подписки, использующие модули доставки, с помощью двух методов веб-службы сервера отчетов: <xref:ReportService2010.ReportingService2010.CreateSubscription%2A> и <xref:ReportService2010.ReportingService2010.CreateDataDrivenSubscription%2A>. Для изменения существующих подписок используются методы <xref:ReportService2010.ReportingService2010.SetSubscriptionProperties%2A> и <xref:ReportService2010.ReportingService2010.SetDataDrivenSubscriptionProperties%2A>. Во время создания подписки пользователь также выбирает для нее модуль доставки и вводит значения для необходимых параметров модуля. Когда пользователь сохраняет подписку, она записывается в базу данных сервера отчетов. Подписки создают уведомления по расписанию или в результате некоторых событий. Когда начинается доставка, выбранный модуль доставки сначала загружает данные конфигурации из файла конфигурации. Затем получаются параметры модуля для подписки и задаются их значения. Наконец, вызывается метод <xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension.Deliver%2A> и отправляется уведомление.  
  
## <a name="developer-requirements"></a>Требования для разработки  
 Для разработки модуля доставки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] необходимо:  
  
-   компьютер для развертывания с установленным сервером отчетов;  
  
-   компьютер для разработки с установленной средой [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] или пакетом средств разработки программного обеспечения (пакетом SDK) для [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)];  
  
-   основные сведения о функциях и возможностях служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], в особенности относящихся к подписке и доставке;  
  
-   основные сведения о [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] и веб-элементах управления, если планируется реализация собственного пользовательского интерфейса подписки для диспетчера отчетов;  
  
-   опыт разработки на языке [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], например [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# или [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] .NET.  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
