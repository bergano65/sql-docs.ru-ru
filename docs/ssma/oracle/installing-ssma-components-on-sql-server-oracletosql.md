---
title: Установка компонентов SSMA на SQL Server (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 10/01/2019
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Installign the Extension Pack
- SQL Server Database Objects
ms.assetid: 33070e5f-4e39-4b70-ae81-b8af6e4983c5
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 1f0cea859e9465eebefebc061ee51107dc7844aa
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71713311"
---
# <a name="installing-ssma-components-on-sql-server-oracletosql"></a>Установка компонентов SSMA на SQL Server (OracleToSQL)

Помимо установки SSMA, необходимо также установить компоненты на компьютере, на котором выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. К этим компонентам относится пакет расширений SSMA, который поддерживает миграцию данных, и поставщики Oracle для обеспечения подключения между серверами.  
  
## <a name="ssma-for-oracle-extension-pack"></a>SSMA для пакета расширений Oracle

Пакет расширений SSMA добавляет базы данных **сисдб** и **ссматестердб** в указанный экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. База данных **сисдб** содержит таблицы и хранимые процедуры, необходимые для переноса данных, и определяемые пользователем функции, имитирующие системные функции Oracle. База данных **ссматестердб** содержит таблицы и процедуры, необходимые компоненту тестера.  
  
Кроме того, при переносе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]в SSMA создает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] задания агента, когда для переноса данных используется модуль миграции данных на стороне сервера.  
  
### <a name="prerequisites"></a>Предварительные требования

Перед установкой SSMA для компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]сервера Oracle убедитесь, что система соответствует следующим требованиям.  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]экземпляр установлен. SSMA не поддерживает SQL Server 2008 Express Edition.
  
- Установщик [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows версии 3.1 или более поздняя версия.  
  
- Поставщик клиента Oracle или поставщик OLE DB для Oracle, а также подключение к базе данных Oracle, которую требуется перенести. Поставщики можно установить с носителя продукта Oracle или с веб-сайта Oracle.  
  
- Служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера должна быть запущена во время установки. Используется для заполнения списка экземпляров [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в мастере установки. Службу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера можно отключить после установки.  
  
    > [!NOTE]  
    > Если служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] браузера запущена, но список экземпляров в программе установки по-прежнему не отображается, необходимо разблокировать UDP-порт 1434. Вы можете использовать брандмауэр Windows, чтобы временно разблокировать порт, или временно отключить брандмауэр Windows. Также может потребоваться временное отключение антивирусного по. После установки обязательно включите брандмауэры и антивирусное по.  
  
### <a name="installing-the-extension-pack"></a>Установка пакета расширений

Пакет расширений можно установить в любое время перед переносом данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
> [!IMPORTANT]  
> Чтобы установить пакет расширений, необходимо быть членом роли сервера **sysadmin** на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Установка пакета расширений**
  
1. Если вы этого еще не сделали, извлеките все файлы из ZIP-файла SSMA.  
  
    В зависимости от версии WinZip можно дважды щелкнуть файл или щелкнуть его правой кнопкой мыши и выбрать пункт **извлечь все** или **Открыть в WinZip**. Чтобы извлечь файлы, следуйте инструкциям в пользовательском интерфейсе WinZip.  
  
2. Скопируйте **SSMA для пакета расширения Oracle.* n*. Install. exe** (где *n* — номер сборки) на компьютере, где работает [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
3. Дважды щелкните **SSMA для пакета расширения Oracle.* n*. Install. exe**.  
  
4. На странице **приветствия** нажмите кнопку **Далее**.  
  
5. На странице Лицензионное **соглашение** ознакомьтесь с лицензионным соглашением. Если вы согласны, установите флажок **я принимаю условия лицензионного соглашения** и нажмите кнопку **Далее**.  
  
6. На странице **Выбор типа установки** выберите вариант **Обычная**.  
  
7. На странице **все готово для установки** нажмите кнопку **установить**.  
  
8. На странице **завершено первое действие установки** нажмите кнопку **Далее**.  
  
    Появится новое диалоговое окно, в котором будет выбран экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для установки пакета расширений.  
  
9. Выберите экземпляр, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в котором будут перенесены схемы Oracle, и нажмите кнопку **Далее**.  
  
    Имя экземпляра по умолчанию совпадает с именем компьютера. За именованными экземплярами будет следовать обратная косая черта и имя экземпляра.  
  
10. На странице Подключение выберите метод проверки подлинности и нажмите кнопку **Далее**.  
  
    При проверке подлинности Windows будут использоваться учетные данные Windows для входа в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При выборе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности необходимо ввести имя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа и пароль.  
  
11. На следующей странице выберите **установить служебные базы данных** *n*, где *n* — номер версии, а затем нажмите кнопку **Далее**.  
  
    База данных **сисдб** создается, а определяемые пользователем функции и хранимые процедуры создаются в этой базе данных.  
  
    Если установлен флажок **установить базу данных тестировщика** , будет создана база данных **ссматестердб** Tester.  
  
12. Чтобы установить служебные программы на другой экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], выберите **Да**, а затем нажмите кнопку **Далее**или закройте мастер и выберите **нет**.  
  
13. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или с помощью программы sqlcmd выполните следующий скрипт, чтобы включить CLR:  
  
    ```
    sp_configure 'clr enabled', 1  
    GO  
    RECONFIGURE  
    GO  
    ```

    Если среда CLR не включена, при подключении SSMA к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]выполните следующее сообщение об ошибке:  
  
    SSMA не удалось получить сведения о версии сборки пакета расширений. Переустановите пакет расширений на сервере базы данных.  
  
### <a name="sql-server-database-objects"></a>SQL Server объекты базы данных  

После установки пакета расширений в базе данных **сисдб** появляется таблица **ssma_oracle. bcp_migration_packages** .

Каждый раз при миграции данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SSMA создает задание [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агента. Эти задания называются **ssma_oracle пакет переноса данных {GUID}** и отображаются в узле [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] агент [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] в папке задания.  
  
## <a name="see-also"></a>См. также раздел

[Установка SSMA для клиента Oracle &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Перенос баз данных Oracle в SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
