---
title: Подключение к базе данных SQL Azure (SybaseToSQL) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 96538007-1099-40c8-9902-edd07c5620ee
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 68fbac69959d423477750a69bb6e5b06ab62af2b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083474"
---
# <a name="connect-to-azure-sql-db--sybasetosql"></a>Подключение к базе данных SQL Azure (SybaseToSQL)
Чтобы подключиться к базе данных SQL Azure, которую необходимо перенести, используйте диалоговое окно Подключение к БД SQL Azure.  
  
Чтобы открыть это диалоговое окно, в меню **файл** выберите **подключиться к базе данных SQL Azure**. Если подключение было выполнено ранее, команда **повторно подключится к базе данных SQL Azure.**  
  
## <a name="options"></a>Параметры  
**Имя сервера**  
  
Выберите или введите имя сервера для подключения к базе данных SQL Azure.  
  
**База данных**  
  
Выберите, введите или **Просмотрите** имя базы данных.  
  
> [!IMPORTANT]  
> SSMA для Sybase не поддерживает подключение к базе данных master в Azure SQL DB.  
  
**User name**  
  
Введите имя пользователя, которое SSMA будет использовать для подключения к базе данных SQL Azure.  
  
**Пароль**  
  
Введите пароль для этого имени пользователя,  
  
**шифрование;**  
  
SSMA рекомендует зашифрованное подключение к базе данных SQL Azure.  
  
## <a name="create-azure-database"></a>Создание базы данных Azure  
Если в учетной записи базы данных SQL Azure нет баз данных, можно создать самую первую базу данных.  
  
Чтобы создать новую базу данных в первый раз, выполните следующие действия.  
  
1.  Нажмите кнопку "Обзор", которая есть в диалоговом окне "подключение к базе данных SQL Azure"  
  
2.  Если базы данных отсутствуют, отображаются два следующих пункта меню.  
  
    1.  **(базы данных не найдены)** , которые отключены и неактивны все время  
  
    2.  **Создать новую базу данных** , которая доступна только при отсутствии баз данных в учетной записи базы данных SQL Azure. При щелчке этого пункта меню создается диалоговое окно Создание базы данных Azure с именем и размером базы данных.  
  
3.  Во время создания базы данных следующие два параметра задаются как входные данные:  
  
    1.  **Имя базы данных:** Введите имя базы данных.  
  
    2.  **Размер базы данных:** Выберите размер базы данных, который необходимо создать в учетной записи базы данных SQL Azure.  
  
