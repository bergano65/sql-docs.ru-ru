---
title: Параметры ("среда" — страница "Общие") | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.SQLEnvironmentOptions
ms.assetid: c32ccdb8-2cf8-4c78-b474-a3abd3dbbd13
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9a96b77c3f1243bc3d95cf38242463724348134b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68188501"
---
# <a name="options-environment-general-page"></a>Параметры ("Среда" — "Общие")
  Диалоговое окно **Параметры** используется для настройки действий среды [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] при запуске, общих параметров управления окнами и других общих настроек. В меню **Сервис** выберите пункт **Параметры**, откройте папку **Среда** и выберите пункт **Общие**.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **При запуске**  
 Выберите действие, которое среда [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] будет выполнять при запуске. Доступны следующие параметры.  
  
-   **Открыть обозреватель объектов** запрашивает подключение, а затем открывает обозреватель объектов.  
  
-   **Открыть новое окно запроса** с запросом на подключение, а затем открыть редактор SQL-запросов.  
  
-   **Открыть обозреватель объектов и создать запрос** на ввод соединения, а затем открыть как обозреватель объектов, так и редактор SQL-запросов с этим соединением.  
  
-   **Открыть пустую среду** открывается [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] без окна редактора SQL-запросов и без подключения обозревателя объектов к серверу.  
  
 **Скрыть системные объекты в обозревателе объектов**  
 Установите этот флажок для удаления системных баз данных, системных таблиц, системных представлений и системных хранимых процедур из представления в обозревателе объектов. Системные функции и системные типы данных не скрываются. Этот параметр применяется только к экземплярам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и не оказывает влияния на серверы, уже подключенные к обозревателю объектов.  
  
## <a name="environment-layout"></a>Макет среды  
 Для переключения среды из режима «документы с вкладками» в режим многодокументного интерфейса (MDI) необходимо закрыть и вновь открыть среду [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 **Документы с вкладками**  
 Выберите этот параметр для отображения внутри редакторов окон с документами, которые связаны между собой вкладками. Окна документов с вкладками полезно применять для организации нескольких открытых документов и для переключения от одного такого документа к другому.  
  
 **Среда MDI**  
 Выберите этот параметр для открытия документов в среде MDI. Использовать окна с документами в режиме MDI полезно в тех случаях, когда необходимо высвободить пространство на экране, которое в ином случае (в режиме документов с вкладками) было бы занято вкладками. При работе в режиме MDI можно переходить от одного документа к другому, используя сочетание клавиш CTRL+TAB или выбирая в меню **Окно** команды расположения сверху вниз или слева направо.  
  
## <a name="docked-tool-window-behavior"></a>Поведение закрепленного окна инструментов  
 **Кнопка "Закрыть" действует только на активной вкладке**  
 Указывает, что когда этот флажок установлен, закрываются не все закрепленные окна инструментов, а только то окно инструментов, которое в данный момент имеет фокус. По умолчанию этот флажок установлен.  
  
 **Кнопка Автоматическое скрытие влияет только на активную вкладку**  
 Указывает, что когда этот флажок установлен, автоматически скрываются не все закрепленные окна инструментов, а только то окно инструментов, которое в данный момент имеет фокус. По умолчанию этот флажок снят.  
  
## <a name="display"></a>Отобразить  
 **Отображать n файлов в списке недавно использованных**  
 Задает число недавно открывавшихся проектов и недавно использованных файлов, которые отображаются в меню **Файл** . Введите число от 1 до 24. По умолчанию — 4. Это удобный способ получения недавно использованных проектов скриптов и проектов файлов и скриптов.  
  
  
