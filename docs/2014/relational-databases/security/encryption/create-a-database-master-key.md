---
title: Создание главного ключа базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 09/12/2019
ms.prod: sql-server-2014
ms.reviewer: carlrab
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- database master key [SQL Server], creating
ms.assetid: 8cb24263-e97d-4e4d-9429-6cf494a4d5eb
author: jaszymas
ms.author: jaszymas
manager: craigg
ms.openlocfilehash: 86f74710e99079d0acd28db09bcf1e4ba7c57865
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74957248"
---
# <a name="create-a-database-master-key"></a>Создание главного ключа базы данных

В этом разделе описывается создание главного ключа базы данных в `master` базе данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью. [!INCLUDE[tsql](../../../includes/tsql-md.md)]

**В этом разделе**

- **Перед началом работы**

  [Безопасность](#Security)

- [Создание главного ключа базы данных с помощью Transact-SQL](#TsqlProcedure)

## <a name="BeforeYouBegin"></a> Перед началом

### <a name="Security"></a> безопасность

#### <a name="Permissions"></a> Permissions

Требует разрешения CONTROL для базы данных.

## <a name="TsqlProcedure"></a> Использование Transact-SQL

### <a name="to-create-a-database-master-key"></a>Создание главного ключа базы данных

1. Выберите пароль для шифрования копии главного ключа базы данных, которая будет храниться в базе данных.
2. В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].
3. Разверните узел **Системные базы данных**, щелкните правой кнопкой мыши базу данных `master` и выберите пункт **Создать запрос**.
4. Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.

  ```sql
  -- Creates the master key.
  -- The key is encrypted using the password "23987hxJ#KL95234nl0zBe."
  CREATE MASTER KEY ENCRYPTION BY PASSWORD = '23987hxJ#KL95234nl0zBe';
```

Дополнительные сведения см. в разделе [CREATE MASTER KEY (Transact-SQL)](/sql/t-sql/statements/create-master-key-transact-sql).
