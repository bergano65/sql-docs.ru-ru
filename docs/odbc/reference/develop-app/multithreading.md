---
title: Многопоточность | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], thread-safe
- thread-safe drivers [ODBC]
- multithreaded applications [ODBC]
ms.assetid: cdfebdf5-12ff-4e28-8055-41f49b77f664
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1eaa07ce22436bc8bfae215c0431480081ee0f06
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086350"
---
# <a name="multithreading"></a>Многопоточность
В многопоточных операционных системах драйверы должны быть потокобезопасными. То есть приложения должны использовать один и тот же обработчик для нескольких потоков. Как это достигается в зависимости от драйвера, и, скорее всего, драйверы будут выполнять сериализацию всех попыток одновременного использования одного и того же маркера в двух разных потоках.  
  
 Приложения обычно используют несколько потоков вместо асинхронной обработки. Приложение создает отдельный поток, вызывает для него функцию ODBC, а затем возобновляет обработку в основном потоке. Вместо постоянного опроса асинхронной функции, как в случае использования атрибута SQL_ATTR_ASYNC_ENABLE инструкции, приложение может просто позволить вновь созданному потоку завершиться.  
  
 Функции, которые принимают маркер оператора и выполняются в одном потоке, могут быть отменены путем вызова **SQLCancel** с тем же маркером оператора из другого потока. Хотя драйверы не должны выполнять сериализацию использования **SQLCancel** таким образом, нет никакой гарантии, что вызов **SQLCancel** будет действительно отменять функцию, выполняющуюся в другом потоке.
