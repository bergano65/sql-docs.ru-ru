---
title: Подключение к служебной программе SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 9b1b61c1f600667b60601d91a97a1327797daa7b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2020
ms.locfileid: "78175893"
---
# <a name="connect-to-a-sql-server-utility"></a>Подключение к служебной программе SQL Server
  Перед подключением к программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо создать точку управления служебной программой. Дополнительные сведения см. в разделе [Функции и задачи служебной программы SQL Server](sql-server-utility-features-and-tasks.md).

 Для просмотра работоспособности ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и управления ей подключитесь к программе [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] с помощью среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (SSMS).

 Подключение к программе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью среды SSMS.

1.  Запустите среду SSMS.

2.  В среде SSMS подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

3.  В меню **Вид** выберите пункт **Обозреватель служебных программ**.

4.  На панели навигации обозревателя служебных программы щелкните ![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility")**Соединение со служебной программой**.

5.  В диалоговом окне **Подключение к серверу** укажите имя экземпляра точки управления служебной программой (UCP) и нажмите кнопку **Подключить**.

6.  Откройте панель навигации обозревателя программы, чтобы отобразить дерево ресурсов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , зарегистрированных в этом пункте управления программой.

 При создании новой точкой управления служебной программой также устанавливается соединение со служебной программой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в статье [Создание точки управления служебной программой SQL Server (служебная программа SQL Server Utility)](create-a-sql-server-utility-control-point-sql-server-utility.md).

## <a name="see-also"></a>См. также:
 [Служебная программа SQL Server функции и задачи](sql-server-utility-features-and-tasks.md) [Просмотр результатов Работоспособность ресурсов политики &#40;служебная программа SQL Server&#41;](view-resource-health-policy-results-sql-server-utility.md)


