---
title: Преобразование типов данных Python и SQL
description: Обзор явных и неявных преобразований типов данных между Python и SQL Server в решениях для обработки и анализа данных и машинного обучения.
ms.prod: sql
ms.technology: machine-learning
ms.date: 12/10/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.custom: seo-lt-2019
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f22f838bc78d4791e73a1d107cd253aae314d205
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "73727514"
---
# <a name="data-type-mappings-between-python-and-sql-server"></a>Сопоставления типов данных между Python и SQL Server
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Для работы с решениями Python, которые выполняются в компоненте интеграции Python в службах машинного обучения SQL Server, ознакомьтесь со списком неподдерживаемых типов данных и преобразований типов данных, которые могут быть выполнены неявным образом при передаче данных между Python и SQL Server.

## <a name="python-version"></a>Версия Python

Подмножество функций RevoScaleR (rxLinMod, rxLogit, rxPredict, rxDTrees, rxBTrees и, возможно, ряд других) предоставляется с помощью API Python с использованием нового пакета Python **revoscalepy**. Этот пакет можно использовать для работы с данными с помощью кадров данных Pandas, XDF-файлов или запросов данных SQL.

Дополнительные сведения см. в статьях [Модуль revoscalepy в SQL Server](ref-py-revoscalepy.md) и [Справочник по функции revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package).

По сравнению с SQL Server Python поддерживает ограниченное число типов данных. Поэтому при каждом использовании данных из SQL Server в сценариях Python данные могут быть неявно преобразованы в совместимый тип. Однако зачастую точное преобразование невозможно выполнить автоматически, и в результате возвращается ошибка.

## <a name="python-and-sql-data-types"></a>Типы данных Python и SQL

В этой таблице приводятся неявные преобразования. Другие типы данных не поддерживаются.

|Тип SQL|Тип Python|
|-------|-----------|
|**bigint**|`numeric`|
|**binary**|`raw`|
|**bit**|`bool`|
|**char**|`str`|
|**float**|`float64`|
|**int**|`int32`|
|**nchar**|`str`|
|**nvarchar**|`str`|
|**nvarchar(max)**|`str`|
|**real**|`float32`|
|**smallint**|`int16`|
|**tinyint**|`uint8`|
|**varbinary**|`bytes`|
|**varbinary(max)**|`bytes`|
|**varchar(n)**|`str`|
|**varchar(max)**|`str`|
