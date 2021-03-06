---
title: Статические курсоры | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], static
- static cursors [ADO]
ms.assetid: cce93ace-c4ed-4c6c-940c-28a50ff2fd12
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 520c484bdaaa6eb59488900208993a607c5b0f7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924121"
---
# <a name="static-cursors"></a>Статические курсоры
Статический курсор всегда отображает результирующий набор в том виде, в котором он был при первом открытии курсора. В зависимости от реализации статические курсоры доступны только для чтения или для чтения и записи и обеспечивают прямую и обратную прокрутку. Статический курсор обычно не обнаруживает изменения, внесенные в членство, порядок или значения результирующего набора после открытия курсора. Статические курсоры могут обнаруживать результаты собственных инструкций обновления, удаления и вставки, хотя это и не обязательно.  
  
 Статические курсоры никогда не обнаруживают другие обновления, удаления и вставки. Например, предположим, что статический курсор извлекает строку, а другое приложение затем обновляет ее. Если приложение извлекает строку из статического курсора, оно получает значения без изменений, внесенных другим приложением. Поддерживаются все типы прокрутки, но поставщики могут или не поддерживать закладки.  
  
 Если приложению не требуется обнаруживать изменения данных и требуется прокрутка, то лучшим выбором является статический курсор. Используйте **Адопенстатик курсортипинум** , чтобы указать, что вы хотите использовать статический курсор в ADO.  
  
## <a name="see-also"></a>См. также:  
 [Однопроходные курсоры](../../../ado/guide/data/forward-only-cursors.md)   
 [Курсоры набора ключей](../../../ado/guide/data/keyset-cursors.md)   
 [Динамические курсоры](../../../ado/guide/data/dynamic-cursors.md)
