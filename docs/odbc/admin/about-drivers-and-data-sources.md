---
title: Сведения о драйверах и источниках данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC data source administrator [ODBC], concepts
ms.assetid: 2bb83ef1-4bbe-4be3-8c32-c4d1140aae1d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4e9b7229882b3b7f94e6b059e04c6496bde09641
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67938041"
---
# <a name="about-drivers-and-data-sources"></a>Сведения о драйверах и источниках данных
*Драйверы* — это компоненты, которые обрабатывают запросы ODBC и возвращают данные в приложение. При необходимости драйверы изменяют запрос приложения в форму, понятную источнику данных. Для добавления или удаления драйвера с компьютера необходимо использовать программу установки драйвера.  
  
 *Источники данных* — это базы данных или файлы, к которым обращается драйвер, которые определяются по имени источника данных (DSN). Используйте администратор источников данных ODBC для добавления, настройки и удаления источников данных из системы. Типы источников данных, которые можно использовать, описаны в следующей таблице.  
  
|Источник данных|Description|  
|-----------------|-----------------|  
|User|Пользовательские имена DSN являются локальными для компьютера и могут использоваться только текущим пользователем. Они регистрируются в поддереве реестра HKEY_CURRENT_USER.|  
|Система|Системные имена DSN являются локальными для компьютера, а не предназначены для пользователя. Система или любой пользователь с привилегиями может использовать источник данных, настроенный с системным именем DSN. Системные имена DSN регистрируются в поддереве реестра HKEY_LOCAL_MACHINE.|  
|Файл|Файловые DSN-файлы представляют собой файловые источники, которые могут совместно использоваться всеми пользователями, на которых установлены одни и те же драйверы, и поэтому они имеют доступ к базе данных. Эти источники данных не должны быть выделенными для пользователя и не должны быть локальными для компьютера. Имена файловых источников данных не идентифицируются выделенными записями реестра. Вместо этого они идентифицируются по имени файла с расширением имени DSN.|  
  
 Пользовательские и системные источники данных совместно называются *машинными* источниками данных, так как они являются локальными для компьютера.  
  
 Каждый из этих источников данных имеет вкладку в диалоговом окне « **Администратор источников данных ODBC** ». Дополнительные сведения о доступных источниках данных см. в разделе [Источники данных](../../odbc/reference/data-sources.md).
