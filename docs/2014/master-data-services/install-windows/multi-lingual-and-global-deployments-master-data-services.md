---
title: Многоязычные и международные развертывания (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: c3d485f8-867c-4aa2-a90d-f38fda192534
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d53ff45452f90c5cf29f376ba01a395d2bbccf65
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65482965"
---
# <a name="multi-lingual-and-global-deployments-master-data-services"></a>Многоязычное и международное развертывание (службы Master Data Services)
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]поддерживает развертывание компонентов и средств на всех языках, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]поддерживаемых. Дополнительные сведения см. в статье [Local Language Versions in SQL Server](../../sql-server/install/local-language-versions-in-sql-server.md).  
  
## <a name="how-languages-are-used"></a>Использование языков  
 В следующей таблице описывается языковая поддержка для компонентов и средств [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] .  
  
|Компонент или средство|Description|  
|-----------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]Установки|Выберите программу установки на английском языке, если нужно, чтобы веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] было доступно и поддерживалось на языках, отличных от языка установки. Дополнительные сведения см. в приведенном ниже описании [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] .|  
|[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]|Язык установки определяет язык [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] . Например, если выбрать в качестве языка установки немецкий, то [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] на этом компьютере будет доступен на немецком языке.|  
|[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]|При запуске программы установки на английском языке веб-приложение [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] поддерживается и доступно на всех языках приложения. [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)]может отображаться на любом из этих языков приложений и принимать входные данные, зависящие от языкового стандарта, на основе языковых настроек клиентского веб-браузера. Если в языковых параметрах задан неподдерживаемый язык приложения, то в службах [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] по умолчанию используется английский.<br /><br /> При выполнении программы установки на любом языке, кроме английского, устанавливаются ресурсы для всех других языков приложения, однако клиенты не могут использовать [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от выбранного языка установки. При попытке доступа к [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] на языке, отличном от языка установки, могут возникнуть проблемы с отображением и вводом данных в приложении.|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]СУБД|Данные в базе данных [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] не относятся к какой-либо конкретной локали. Это позволяет [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] определять способ отображения данных, например дат и чисел, в формате, определяемом языковыми параметрами клиентского веб-браузера.|  
  
## <a name="see-also"></a>См. также:  
 [Установка служб Master Data Services](install-master-data-services.md)  
  
  
