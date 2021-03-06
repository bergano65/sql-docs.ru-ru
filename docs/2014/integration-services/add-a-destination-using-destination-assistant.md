---
title: Добавление назначения с помощью помощника по назначениям | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 747a0de0-3c2f-4d31-a692-7111fc0911d8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 66e48903776824b0e540b854a5704ceef3a9782e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062071"
---
# <a name="add-a-destination-using-destination-assistant"></a>Добавление назначения с помощью помощника по назначениям
  В этом разделе приведены шаги по добавлению нового назначения с помощью помощника по назначениям, а также приведен список параметров, доступных в диалоговом окне **Добавление нового назначения**, которое отображается при перетаскивании помощника по назначениям в конструктор служб SSIS.  
  
### <a name="to-use-destination-assistant-to-add-a-destination"></a>Добавление назначения с помощью помощника по назначениям  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте пакет служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , в который нужно добавить компонент назначения.  
  
2.  Перетащите компонент **Помощник по назначению** из панели элементов служб SSIS на вкладку **поток данных** . Появится диалоговое окно **Добавление нового назначения** . В следующем разделе приведены подробные сведения о параметрах, доступных в этом диалоговом окне.  
  
3.  Выберите тип назначения в списке **Типы** .  
  
4.  Выберите существующий диспетчер соединений в списке **Диспетчеры соединений** или нажмите кнопку ** \<создать>** , чтобы создать новый диспетчер соединений.  
  
5.  Если был выбран существующий диспетчер соединений, нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Добавление нового назначения** . Должны быть показаны назначение и диспетчеры соединений, добавленные в поток данных.  
  
6.  Если нажать кнопку ** \<создать>** для создания нового диспетчера соединений, появится диалоговое окно **Диспетчер соединений** , в котором можно указать параметры соединения. После завершения создания нового диспетчера соединений в конструкторе служб SSIS будут показаны назначение и диспетчер соединений.  
  
  
