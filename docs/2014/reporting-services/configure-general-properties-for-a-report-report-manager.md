---
title: Настройка общих свойств отчета (диспетчер отчетов) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 23184e77efbe41eae3d4de434a30ff8f3a4847ff
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177034"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a>Настройка общих свойств отчета (диспетчер отчетов)
  
### <a name="to-configure-general-report-properties"></a>Настройка общих свойств отчета

1.  Запустите [Диспетчер отчетов (службы Reporting Services в основном режиме)](../../2014/reporting-services/report-manager-ssrs-native-mode.md).

2.  В диспетчере отчетов перейдите на страницу **Содержимое** . Перейдите к отчету, для которого нужно настроить конфигурацию общих свойств, и откройте его.

3.  Перейдите на вкладку **Свойства**.

     Или, если страница **содержимое** находится в представлении Details, щелкните значок страницы свойств:

     ![Значок страницы свойств](media/prop.gif "Значок страницы свойств")

4.  Отобразится страница **Общие** свойства, и можно настроить свойства следующим образом.

    -   В разделе **Свойства** можно изменить имя и описание отчета.

    -   Можно установить флажок **Скрыть в представлении списка** , чтобы скрыть элемент при открытии страницы в макете страницы по умолчанию (представление списка), где элементы упорядочиваются по странице.

    -   В разделе **Определение отчета** нажмите кнопку **изменить** , чтобы извлечь копию определения отчета. Изменения определения отчетов, произведенные локально, на сервере отчетов не сохраняются.

         Или, чтобы обновить определение отчета из RDL-файла, нажмите кнопку **Обновить**.

        > [!NOTE]
        >  По завершении обновления определения отчета необходимо сбросить параметры настроек источника данных.

    -   Используйте кнопки **Удалить** или **переместить** , чтобы удалить или переместить отчет.

    -   Можно также создать связанный отчет.

5.  Завершив настройку общих свойств отчета, нажмите кнопку **Применить**.

## <a name="see-also"></a>См. также:
 [Перемещение или удаление элемента &#40;диспетчер отчетов](report-server/move-or-delete-an-item-report-manager.md) [Страница "содержимое"&#41;&#40;диспетчер отчетов](../../2014/reporting-services/contents-page-report-manager.md) [Поиск, просмотр и управление отчетами&#41;&#40;и службы SSRS построитель отчетов](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [страница "Общие свойства", отчеты &#41;&#40;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) диспетчер отчетов


