---
title: Конфигурация сетевого протокола SQL Server по умолчанию | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- protocols [SQL Server], default settings
- default protocols, after install
ms.assetid: 635ea361-a797-4971-bd05-e3415862bc5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 218389eaf76336e33d866f16c6b79ef54661be0b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68011947"
---
# <a name="default-sql-server-network-protocol-configuration"></a>Конфигурация сетевого протокола SQL Server по умолчанию
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Для улучшения защиты при установке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] сетевая возможность подключения в некоторых случаях блокируется. Сетевая функциональность TCP/IP не блокируется, если используется выпуск Enterprise, Standard, Evaluation или Workgroup или если на компьютере установлена предыдущая версия [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]. Чтобы можно было устанавливать локальные соединения с сервером, при установке SQL Server всегда активируется протокол общей памяти. Служба браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] может быть остановлена в зависимости от параметров и условий установки SQL Server.

Чтобы настроить сетевые протоколы после установки, используйте узел "Сетевая конфигурация [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] " диспетчера конфигурации [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Чтобы настроить автоматический запуск службы браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] , используйте узел "Службы [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] " диспетчера конфигурации [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Включение или отключение сетевого протокола сервера](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md).


## <a name="default-configuration"></a>Конфигурация по умолчанию

Конфигурация SQL Server 2005 после установки описана в следующей таблице.

|Выпуск | Новая установка или установленный экземпляр | Общая память | TCP/IP | Именованные каналы|
| -------- | -- | -- | -- | --  |  
|Enterprise | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Standard | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Интернет | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|Разработчик | Новая установка | Активировано | Выключено | Отключено для сетевых подключений.|
|Ознакомительная версия | Новая установка | Активировано | Активировано | Отключено для сетевых подключений.|
|SQL Server Express | Новая установка | Активировано | Выключено | Отключено для сетевых подключений.|
|Все выпуски | Присутствует установленный экземпляр, но выполнение не обновляется. | То же, что и при новой установке | То же, что и при новой установке | То же, что и при новой установке|
|Все выпуски | Обновление | Активировано | Сохраняются параметры установленного экземпляра. | Сохраняются параметры установленного экземпляра.|


>[!NOTE]
> Если экземпляр работает в отказоустойчивом кластере [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], он прослушивает порты каждого IP-адреса, выбранного для [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] во время установки [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)].
 
>[!NOTE]
> При установке [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] с аргументами командной строки можно указать, какие протоколы нужно включить при помощи параметров `TCPENABLED` и `NPENABLED` . Дополнительные сведения см. в разделе [Установка SQL Server из командной строки](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md).

## <a name="creating-a-connection-string"></a>Создание строки подключения

Примеры строк подключения см. в следующих разделах:
* [Создание допустимой строки соединения с использованием протокола общей памяти](../../tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)
* [Создание допустимой строки подключения с использованием протокола TCP/IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)



## <a name="includessnoversion_mdincludesssnoversion-mdmd-browser-settings"></a>[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Параметры браузера

Во время установки можно настроить автоматический запуск службы браузера [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] . По умолчанию служба запускается автоматически при выполнении следующих условий:

* при обновлении установки;
* при установке параллельно с другим экземпляром [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)];
* при установке в кластере;
* при установке именованного экземпляра ядра СУБД, включая все экземпляры [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] Express;
* при установке именованного экземпляра служб Analysis Services.

## <a name="see-also"></a>См. также:

[Требования к оборудованию и программному обеспечению для установки SQL Server 2016](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)

[Настройка контактной зоны](../../relational-databases/security/surface-area-configuration.md)  



