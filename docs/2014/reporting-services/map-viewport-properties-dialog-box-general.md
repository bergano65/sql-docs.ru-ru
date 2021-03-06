---
title: Диалоговое окно "Свойства окна просмотра карт" — "Общие" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.mapviewport.general.f1
- "10505"
ms.assetid: 6c9c773e-5c56-4571-95ed-8a157cfdfe52
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ec0aaa051ba317cd05a9784c80fb997f5fa19e6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66108234"
---
# <a name="map-viewport-properties-dialog-box-general"></a>Диалоговое окно «Свойства окна просмотра карты», вкладка «Общие»
  Перейдите на вкладку **Общие** диалогового окна **Свойства окна просмотра карты** , чтобы изменить параметры системы координат, проекции и границ.  
  
## <a name="options"></a>Параметры  
 **Система координат**  
 Укажите тип координат, в которых заданы данные карты.  
  
-   **Плоская** Выберите этот параметр, если данные Map находятся в координатах X и Y, например для планов здания.  
  
-   **Географическая** Выберите этот параметр, если данные сопоставляются с координатами долготы и широты, например для мест расположения городов.  
  
 **Отображения**  
 Укажите метод проецирования географических координат на плоскую поверхность. Выберите проекцию, совместимую с визуализируемыми данными. Проекция оказывает влияние на четыре пространственных свойства: площадь, форму, расстояние и направление. Выбор проекции для представления земной поверхности определяется центром представления, границами карты и масштабом.  
  
 Каждая из следующих проекций не изменяет одно или несколько пространственных свойств.  
  
-   **Равнопромежуточная** Выберите этот параметр, чтобы использовать долготу и широту в качестве прямоугольных координат.  
  
-   **Меркатора** Выберите эту популярную проекцию для областей меньшего размера, чтобы уменьшить искажения на равенство или добавить слой карты с существующим мозаичным слоем, использующим проекцию Меркатора.  
  
-   **Робинсон** Выберите этот параметр, чтобы уменьшить искажения больших областей, которые охватывают от тождественности до полюсам. Разработана Артуром Робинсоном в 1963 г.  
  
-   **Фэйи** Выберите этот параметр, чтобы уменьшить искажения больших областей, которые охватывают от тождественности до полюсам. Разработана Лоуренсом Фэйи в 1975 г.  
  
-   **Эккерт1** Выберите этот параметр для использования одинаковых параллельных вычислений в широте и прямых линий для меридианы в долготе.  
  
-   **Эккерт3** Выберите этот параметр, чтобы использовать одинаковые параллельные области в широте и кривых линий для меридианы в долготе.  
  
-   **Хаммераитофф** Выберите этот параметр для полярных карт или карт мира.  
  
-   **Wagner3** Выберите этот параметр для карт мира.  
  
-   **Проекция Бонна** Выберите этот параметр для просмотра мира в том виде, в котором он отображается в Atlas.  
  
 **Параметры разрыва страниц**  
 Выберите необходимые параметры, чтобы указать, как размещается содержимое на странице отчета.  
  
 **Параметры границ**  
 Укажите нижнюю и верхнюю границы значений координат, определяющих, какая часть карты будет отображена в отчете.  
  
 **Минимальное значение X**  
 Наименьшее значение X. Доступно только для типа координат **Планарные** .  
  
 **Максимальное значение X**  
 Наибольшее значение X. Доступно только для типа координат **Планарные** .  
  
 **Минимальное значение Y**  
 Наименьшее значение Y. Доступно только для типа координат **Планарные** .  
  
 **Максимальное значение Y**  
 Наибольшее значение Y. Доступно только для типа координат **Планарные** .  
  
 **Минимальная долгота**  
 Наименьшее значение долготы. Доступно только для типа координат **Географические** .  
  
 **Максимальная долгота**  
 Наибольшее значение долготы. Доступно только для типа координат **Географические** .  
  
 **Минимальная широта**  
 Наименьшее значение широты. Доступно только для типа координат **Географические** .  
  
 **Максимальная широта**  
 Наибольшее значение широты. Доступно только для типа координат **Географические** .  
  
## <a name="see-also"></a>См. также:  
 [Карты (построитель отчетов и службы SSRS)](report-design/maps-report-builder-and-ssrs.md)  
  
  
