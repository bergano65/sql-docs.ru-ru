---
title: Использование базы знаний DQS по умолчанию | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: b36af13b-9fcc-4168-bb92-214d600b1c93
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: d0fa10fa26f46857bd4f6848bd98bdcf1d65253a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65484076"
---
# <a name="using-the-dqs-default-knowledge-base"></a>Использование базы знаний DQS по умолчанию
  В этом разделе описывается база знаний **DQS Data**, которая используется по умолчанию и устанавливается со службами [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS). Эта готовая база данных содержит следующие домены.  
  
-   **Страна или регион**: содержит стандартное длинное (официальное) название, заданное в стране или регионе, и короткие имена (общее имя, используемое в списках, на картах и т. д.), аббревиатуру из двух букв, три буквы и три цифры для каждого местоположения.  В качестве первого значения указывается длинное название страны.  
  
-   **Страна или регион (с тремя буквами)**: содержит обычное длинное (официальное название, обозначенное страной или регионом) и короткие имена (общее имя, используемое в списках, на картах и т. д.), двухбуквенный аббревиатуру, три буквы и три цифры для каждого местоположения.  В качестве первого значения указывается трехбуквенное обозначение округа.  
  
-   **Страна или регион (с двумя буквами)**: содержит обычное длинное (официальное название, обозначенное страной или регионом) и краткие имена (общее имя, используемое в списках, на картах и т. д.), двухбуквенный аббревиатуру, три буквы и три цифры для каждого местоположения.  В качестве первого значения указывается двухбуквенное обозначение страны.  
  
-   **US-counts**: содержит список районов США.  
  
-   **US-Last Name**: содержит список фамилий (фамилий), происходящих в 100 или более раз в переписи 2000.  
  
-   **US-Places**: содержит список мест для состояний 50, округ Колумбия и Пуэрто-Рико, извлеченных из переписи 2010.  
  
-   **US-State**: содержит стандартное длинное (официальное) имя и двузначное обозначение для каждого штата в США. В качестве первого значения указывается длинное (официальное) название штата.  
  
-   **US-State (заголовок с двумя буквами)**: содержит стандартное длинное (официальное) имя и двузначное обозначение для каждого штата в США. В качестве первого значения указывается двухбуквенное обозначение штата.  
  
## <a name="using-the-default-knowledge-base"></a>Использование базы знаний по умолчанию  
 База знаний по умолчанию DQS Data служб DQS позволяет сделать следующее.  
  
-   Быстро запустить и внедрить проект по качеству данных с помощью базы знаний по умолчанию, не создавая новую базу знаний служб DQS.  
  
-   Выполнять действия по управлению доменами и обнаружению знаний, а также действия, связанные с политикой сопоставления, в базе данных по умолчанию. Для этого нажмите кнопку **Открыть базу знаний** на экране [Data Quality Client Home Screen](../../2014/data-quality-services/data-quality-client-home-screen.md), выберите базу знаний **DQS Data** на экране **Открыть базу знаний** и выберите нужное действие в области **Выбрать действие** . Чтобы продолжить, нажмите кнопку **Далее**.  
  
-   Создать новую базу знаний с помощью базы знаний по умолчанию. Сведения о создании базы знаний на основе существующей базы знаний см. в разделе [Create a Knowledge Base](../../2014/data-quality-services/create-a-knowledge-base.md).  
  
-   Использовать базу знаний по умолчанию можно в [компоненте DQS Cleansing  в службах Integration Services](https://go.microsoft.com/fwlink/?LinkId=238830) , а также в [надстройке Master Data Services для Excel](../master-data-services/microsoft-excel-add-in/data-quality-matching-in-the-mds-add-in-for-excel.md).  
  
## <a name="see-also"></a>См. также:  
 [Базы знаний и домены DQS](../../2014/data-quality-services/dqs-knowledge-bases-and-domains.md)  
  
  
