---
title: Администрирование базы данных сервера отчетов (службы SSRS в собственном режиме) | Документы Майкрософт
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], databases
- renaming databases
- report server database
- databases [Reporting Services], administering
- reportservertempdb
- reportserver database
ms.assetid: 97b2e1b5-3869-4766-97b9-9bf206b52262
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d155437880f1fb93779a2352bd507ea83de16256
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66104282"
---
# <a name="administer-a-report-server-database-ssrs-native-mode"></a>Администрирование базы данных сервера отчетов (службы Reporting Services в собственном режиме)
  В развертывании служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в качестве внутреннего хранилища используются две реляционные базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . По умолчанию эти базы данных имеют имена ReportServer и ReportServerTempdb. База данных ReportServerTempdb создается вместе с основной базой данных сервера отчетов и используется для хранения временных данных, сведений о сеансе и кэшированных отчетов.  
  
 В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]задачи администрирования баз данных включают создание резервных копий и восстановление из копии баз данных сервера отчетов, а также управление ключами шифрования, применяемыми для шифрования и расшифровки конфиденциальных данных.  
  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предоставляет различные средства для администрирования баз данных сервера отчетов.  
  
-   Для резервного копирования или восстановления базы данных сервера отчетов, перемещения базы данных сервера отчетов или восстановления базы данных сервера отчетов можно использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] команды или программы командной строки базы данных. Инструкции см. в статье [Перемещение баз данных сервера отчетов на другой компьютер (собственный режим служб SSRS)](moving-the-report-server-databases-to-another-computer-ssrs-native-mode.md) в электронной документации по SQL Server.  
  
-   Чтобы скопировать содержимое существующей базы данных в другую базу данных сервера отчетов, можно присоединить копию базы данных сервера отчетов и использовать ее с другим экземпляром сервера отчетов. Либо можно создать и выполнить скрипт, использующий вызовы SOAP для повторного создания содержимого сервера отчетов в новой базе данных. Для выполнения скрипта можно использовать служебную программу **rs** .  
  
-   Чтобы управлять соединениями между сервером отчетов и его базой данных и найти, какая база данных используется для экземпляра сервера отчетов, можно использовать страницу «Установка базы данных» средства настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Дополнительные сведения о подключении сервера отчетов к базе данных сервера отчетов см. в разделе [Configure a Report Server Database Connection  &#40;SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md).  
  
## <a name="sql-server-login-and-database-permissions"></a>Разрешения на вход в систему и доступ к базам данных SQL Server  
 Базы данных сервера отчетов используются сервером отчетов для внутренних целей. Соединения с любой базой данных устанавливаются службой сервера отчетов. Чтобы настроить соединение сервера отчетов с базой данных сервера отчетов, применяется средство настройки служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] .  
  
 Учетными данными для соединения сервера отчетов с базой данных может служить учетная запись службы, учетная запись локального пользователя Windows или пользователя домена, а также учетная запись пользователя базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Для соединения необходимо выбрать существующую учетную запись; службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] не создают учетные записи для пользователей.  
  
 Для указанной учетной записи автоматически создается имя входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , позволяющее подключиться к базе данных сервера отчетов.  
  
 Настройка разрешений для этой базы данных также выполняется автоматически. Средство настройки служб Reporting Services делает эту учетную запись или пользователя базы данных членом ролей `Public` и `RSExecRole` для баз данных сервера отчетов. Роль `RSExecRole` предоставляет разрешения для доступа к таблицам баз данных и выполнения хранимых процедур. Объект `RSExecRole` создается в базе данных master и msdb при создании сервера отчетов. Пользователь `RSExecRole` является членом роли `db_owner` для баз данных сервера отчетов, что позволяет серверу отчетов обновлять свою собственную схему для поддержки процесса автоматического обновления.  
  
## <a name="naming-conventions-for-the-report-server-databases"></a>Соглашения об именах для баз данных сервера отчетов  
 Имя базы данных-источника должно соответствовать правилам, определенным для [идентификаторов базы данных](../../relational-databases/databases/database-identifiers.md). Имя временной базы данных всегда совпадает с именем основной базы данных сервера отчетов с добавлением суффикса Tempdb. Невозможно выбрать другое имя для временной базы данных.  
  
 Переименование базы данных сервера отчетов не поддерживается, так как базы данных сервера отчетов рассматриваются как внутренние компоненты. Переименование баз данных сервера отчетов может вызвать ошибки. В частности, при переименовании базы данных источника появляется сообщение об ошибке, объясняющее, что имена баз данных не синхронизированы. При переименовании базы данных ReportServerTempdb следующая внутренняя ошибка возникает позже при выполнении отчетов:  
  
 «Произошла внутренняя ошибка на сервере отчетов. Дополнительные подробности см. в журнале ошибок. (rsInternalError)  
  
 Недопустимое имя объекта "ReportServerTempDB.dbo.PersistedStream"».  
  
 Причина этой ошибки заключается в том, что имя ReportServerTempdb хранится внутренне и используется хранимыми процедурами для выполнения внутренних операций. Переименование временной базы данных приведет к неправильной работе хранимых процедур.  
  
## <a name="enabling-snapshot-isolation-on-the-report-server-database"></a>Включение изоляции моментального снимка в базе данных сервера отчетов  
 В базе данных сервера отчетов нельзя включить изоляцию моментального снимка. Если изоляция моментального снимка включена, будет возникать следующая ошибка: «Выбранный отчет не готов для просмотра. Выполняется подготовка отчета к отображению, или недоступен моментальный снимок отчета.».  
  
 Даже если изоляция моментального снимка специально не была включена, этот атрибут может быть установлен другим приложением или изоляция моментального снимка включена в базе данных **model** , а это приводит к тому, что все новые базы данных наследуют эту настройку.  
  
 Чтобы отменить изоляцию моментального снимка в базе данных сервера отчетов, в среде Management Studio откройте новое окно запроса, вставьте и запустите следующий скрипт:  
  
```  
ALTER DATABASE ReportServer  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServerTempdb  
SET ALLOW_SNAPSHOT_ISOLATION OFF  
ALTER DATABASE ReportServer  
SET READ_COMMITTED_SNAPSHOT OFF  
ALTER DATABASE ReportServerTempDb  
SET READ_COMMITTED_SNAPSHOT OFF  
```  
  
## <a name="about-database-versions"></a>О версиях базы данных  
 В службах [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]явная информация о версии базы данных не доступна. Но так как версия базы данных всегда синхронизирована с версией продукта, для определения факта смены версии базы данных можно пользоваться сведениями о версии продукта. Сведения о версии продукта [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] для указываются в файлах журнала, в заголовках всех вызовов SOAP и при подключении к URL-адресу сервера отчетов (например, при открытии браузера в http://localhost/reportserver)среде).  
  
## <a name="see-also"></a>См. также:  
 [Использование диспетчера конфигурации служб Reporting Services (собственный режим)](../../sql-server/install/reporting-services-configuration-manager-native-mode.md)   
 [Создание базы данных сервера отчетов в собственном режиме &#40;Configuration Manager SSRS&#41;](../install-windows/ssrs-report-server-create-a-native-mode-report-server-database.md)   
 [Настройка учетной записи службы сервера отчетов (диспетчер конфигурации служб SSRS)](../install-windows/configure-the-report-server-service-account-ssrs-configuration-manager.md)   
 [Настройка подключения к базе данных сервера отчетов &#40;службы SSRS Configuration Manager&#41;](../../sql-server/install/configure-a-report-server-database-connection-ssrs-configuration-manager.md)   
 [Создание базы данных сервера отчетов (диспетчер конфигурации служб SSRS)](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)   
 [Операции резервного копирования и восстановления для Reporting Services](../install-windows/backup-and-restore-operations-for-reporting-services.md)   
 [База данных сервера отчетов (службы Reporting Services в собственном режиме)](report-server-database-ssrs-native-mode.md)   
 [Reporting Services сервера отчетов &#40;в основном режиме&#41;](reporting-services-report-server-native-mode.md)   
 [Хранение зашифрованных данных сервера отчетов &#40;служб SSRS Configuration Manager&#41;](../install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)   
 [Настройка ключей шифрования и управление ими (диспетчер конфигурации служб SSRS)](../install-windows/ssrs-encryption-keys-manage-encryption-keys.md)  
  
  
