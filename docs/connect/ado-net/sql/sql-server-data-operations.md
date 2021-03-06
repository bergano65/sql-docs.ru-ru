---
title: Операции с данными SQL Server в ADO.NET
description: Описание работы с данными в SQL Server. Содержит разделы, посвященные массовым операциям копирования, режиму MARS, асинхронным операциям и возвращающим табличное значение параметрам.
ms.date: 08/15/2019
ms.assetid: b864ebc9-ed8e-4059-85fd-36d9198f5521
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: aea8e0ecbb542645f0553e8bf34172381f37929b
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896620"
---
# <a name="sql-server-data-operations-in-adonet"></a>Операции с данными SQL Server в ADO.NET

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

В этом разделе описываются функции и режимы работы SQL Server, характерные для поставщика данных Microsoft SqlClient для SQL Server (<xref:Microsoft.Data.SqlClient>).  
  
## <a name="in-this-section"></a>В этом разделе  
[Операции массового копирования в SQL Server](bulk-copy-operations-sql-server.md)  
Описание возможности массового копирования для поставщика данных .NET Framework для SQL Server.  
  
[Режим MARS](multiple-active-result-sets-mars.md)  
Сведения о том, как можно открыть несколько экземпляров <xref:Microsoft.Data.SqlClient.SqlDataReader> в одном подключении, где каждый экземпляр <xref:Microsoft.Data.SqlClient.SqlDataReader> запускается отдельной командой.  
  
[Асинхронные операции](asynchronous-operations.md)  
Описание выполнения асинхронных операций с базой данных при помощи API-интерфейса, который создан по асинхронной модели, используемой платформой .NET Framework.  
  
[Параметры, возвращающие табличные значения](table-valued-parameters.md)  
Здесь описывается работа с возвращающими табличное значение параметрами, появившимися в SQL Server 2008.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
