---
title: Создание файлов подключения к серверу (DB2ToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 685419f6-8606-462c-be12-8bace45bede6
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 484b9e12d53d22160358d873ddb2a3dc60d0977e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67989812"
---
# <a name="creating-the-server-connection-files-db2tosql"></a>Создание файлов подключения к серверу (DB2ToSQL)
Сведения о сервере можно указать либо в разделе Servers файла сценария, либо в отдельном файле соединения сервера. Параметр командной строки для файла соединения сервера имеет значение, `-c <serverconnectionfile>`. Если один и тот же идентификатор сервера имеется как в файле скрипта, так и в файле соединения сервера, то будет считаться определение сервера в файле скрипта.  
  
**Пример: 1**  
  
```  
<!--Sample of server connection file commands -->  
  
<db2 name="<source-server-unique-name>">  
  
    <standard-mode>  
  
      <connection-provider value ="OleDB Provider"/>  
  
      <!-- Defines server manager to connect.  
  
              Available manager attribute values  
  
              • zOs      - upgrades the project (default)  
  
              • LUW       - displays an error and halts the execution-->  
  
      <database-manager value="$Db2Manager$"/>  
  
      <server-name value="$Db2HostName$" />  
  
      <port value="$Db2Port$" />  
  
      <initial-catalog value="$Db2Instance$" />  
  
      <user-id value="$Db2UserName$" />  
  
      <password value="$Db2Password$"/>  
  
    </standard-mode>  
  
</db2>  
```  
  
```  
<sql-server name="<target-server-unique-name>">  
  
  <sql-server-authentication>  
  
    <server value="<server-name>"/>  
  
    <database value="<database-name>"/>  
  
    <user-id value="<user-name>"/>  
  
    <password value="<password>"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
## <a name="next-step"></a>Дальнейшее действие  
Следующий шаг в работе консоли заключается [в выполнении консоли SSMA &#40;DB2ToSQL&#41;](../../ssma/db2/executing-the-ssma-console-db2tosql.md)  
  
## <a name="see-also"></a>См. также:  
[Выполнение команд консоли SSMA](https://msdn.microsoft.com/ce63f633-067d-4f04-b8e9-e1abd7ec740b)  
  
