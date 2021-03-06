---
title: Безопасность SQL Server
description: Общие сведения о средствах безопасности SQL Server и сценариях приложений для создания безопасных приложений ADO.NET, предназначенных для SQL Server.
ms.date: 09/26/2019
ms.assetid: 9053724d-a1fb-4f0f-b9dc-7f6dd893e8ff
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: af4e3ff43499f32d276d27873211330bc28f0cc5
ms.sourcegitcommit: 610e49c3e1fa97056611a85e31e06ab30fd866b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/07/2020
ms.locfileid: "78896276"
---
# <a name="sql-server-security"></a>Безопасность SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

SQL Server предоставляет много функций для создания безопасных приложений баз данных.  
  
Такие общие угрозы безопасности, как кража данных или вандализм, существуют независимо от используемой версии SQL Server. Целостность данных также следует рассматривать как вопрос, связанный с безопасностью. Если данные не защищены, они могут стать бесполезными в результате разрешения нерегламентированной обработки данных и случайного или намеренного изменения данных, используя неправильные значения, или полностью удалены. Кроме того, сейчас часто предъявляются юридические требования, которые необходимо соблюдать, например требования к правильному хранению конфиденциальной информации. В зависимости от законов, которые применяются в определенной юрисдикции, хранение некоторых видов персональных данных может быть полностью запрещено.  
  
В каждой версии SQL Server есть свои средства безопасности, как и в каждой версии Windows, при этом возможности более поздних версий шире, чем возможности более ранних. Важно понимать, что функции безопасности сами по себе не могут гарантировать безопасность приложения базы данных. Каждое приложение базы данных имеет уникальные требования, среду выполнения, модель развертывания, физическое местоположение и количество пользователей. Для некоторых локальных приложений может потребоваться лишь минимальный уровень безопасности, в то время как для других локальных приложений или приложений, развернутых в Интернете, могут потребоваться строгие меры безопасности, а также постоянные мониторинг и оценка.  
  
Требования безопасности для приложения базы данных SQL Server следует рассматривать во время разработки, а не впоследствии. Оценка угроз на ранней стадии цикла разработки дает возможность уменьшить потенциальный ущерб, где бы ни была обнаружена уязвимость.  
  
Даже если первоначальное проектирование приложения проработано правильно, по мере развития системы могут возникать новые угрозы. Создавая несколько линий обороны вокруг вашей базы данных, вы можете свести к минимуму ущерб, наносимый нарушением безопасности. Ваша первая линия обороны заключается в том, чтобы уменьшить площадь атаки, не давая больше разрешений, чем это необходимо.  
  
В этом разделе кратко описываются средства безопасности в SQL Server, которые нужны разработчикам. Здесь также приведены ссылки на соответствующие разделы электронной документации на SQL Server и другие ресурсы, где эти возможности описаны более подробно.  
  
## <a name="in-this-section"></a>В этом разделе  
[Проверка подлинности в SQL Server](authentication-sql-server.md)  
Описание имен входа и проверки подлинности в SQL Server и ссылки на дополнительные ресурсы. 
  
[Сценарии безопасности приложений в SQL Server](application-security-scenarios-sql-server.md)  
Подразделы с описанием различных сценариев обеспечения безопасности для приложений ADO.NET и SQL Server.  
  
[Безопасность SQL Server Express](sql-server-express-security.md)  
Описание вопросов безопасности для SQL Server Express.  
  
## <a name="related-sections"></a>См. также  
[Центр безопасности для ядра СУБД SQL Server и Базы данных Azure SQL](../../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)  
Описывает вопросы безопасности для SQL Server и Базы данных Azure SQL.

[Вопросы безопасности при установке SQL Server](../../../sql-server/install/security-considerations-for-a-sql-server-installation.md)  
Описывает вопросы безопасности, которые следует учитывать перед установкой SQL Server.

## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
