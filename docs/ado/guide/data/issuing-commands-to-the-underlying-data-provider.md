---
title: Выдача команд базовому поставщику данных | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 02a861daa78b798c1b19b5fc2607cfcaf0ce5968
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67924948"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Выдача команды для базового поставщика данных
Любая команда, которая не начинается с SHAPE, передается поставщику данных. Это эквивалентно выдаче команды Shape в виде "SHAPE {поставщик команда}". Этим командам *не* требуется создавать **набор записей**. Например, форма {DROP TABLE MyTable} является абсолютно допустимой командой Shape, предполагая, что поставщик данных поддерживает инструкцию DROP TABLE.  
  
 Эта возможность позволяет использовать как обычные команды поставщика, так и команды Shape для совместного использования одного соединения и транзакции.  
  
## <a name="see-also"></a>См. также:  
 [Пример формирования данных](../../../ado/guide/data/data-shaping-example.md)   
 [Грамматика формальной фигуры](../../../ado/guide/data/formal-shape-grammar.md)   
 [Общие сведения о командах формирования данных](../../../ado/guide/data/shape-commands-in-general.md)
