---
title: Создание распределенных транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 05/13/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, performing distributed transactions
- SQL Server Native Client ODBC driver, transactions
- distributed transactions [ODBC]
- transactions [ODBC]
- ODBC, transactions
ms.assetid: 2c17fba0-7a3c-453c-91b7-f801e7b39ccb
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b01e47f81f153b73c8a57d23c9a75fc8b57ef66
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73761069"
---
# <a name="create-a-distributed-transaction"></a>Создание распределенной транзакции

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

<!--
The following includes .md file is Empty, as of long before 2019/May/13.
/includes/snac-deprecated.md
-->


Распределенную транзакцию можно создать для различных систем Microsoft SQL разными способами.

## <a name="odbc-driver-calls-the-msdtc-for-sql-server-on-premises"></a>Драйвер ODBC вызывает MSDTC для локальной SQL Server

Microsoft координатор распределенных транзакций (MSDTC) позволяет приложениям расширять или _распределять_ транзакции между двумя или более экземплярами [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Распределенная транзакция работает, даже если два экземпляра размещены на разных компьютерах.

Служба MSDTC устанавливается локально для Microsoft SQL Server, но недоступна для облачной службы базы данных SQL Microsoft Azure.

MSDTC вызывается драйвером SQL Server Native Client для ODBC, когда программа C++ управляет распределенной транзакцией. Драйвер ODBC для собственного клиента имеет диспетчер транзакций, совместимый со стандартом XA с открытой групповой обработкой распределенных транзакций (DTP). Это соответствие требуется для MSDTC. Как правило, все команды управления транзакциями отправляются с помощью этого драйвера ODBC собственного клиента. Последовательность выглядит так:

1. Приложение ODBC для собственного клиента C++ запускает транзакцию, вызывая [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md), при этом режим автоматической фиксации отключен.

2. Приложение обновляет некоторые данные на SQL Server X на компьютере а.

3. Приложение обновляет некоторые данные на SQL Server Y на компьютере B.
    - Если обновление на SQL Server Y завершается сбоем, выполняется откат всех незафиксированных обновлений в обоих экземплярах SQL Server.

4. Наконец, приложение завершает транзакцию путем вызова [SQLEndTran _(1)_](../../../relational-databases/native-client-odbc-api/sqlendtran.md)с параметром SQL_COMMIT или SQL_ROLLBACK.

_(1)_ MSDTC можно вызывать без ODBC. В этом случае MSDTC превращается в диспетчер транзакций, а приложение больше не использует **SQLEndTran**.

### <a name="only-one-distributed-transaction"></a>Только одна распределенная транзакция

Предположим, что приложение ODBC собственного клиента C++ прикреплено к распределенной транзакции. Затем приложение прикрепляется во второй распределенной транзакции. В этом случае драйвер ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для собственного клиента оставляет исходную распределенную транзакцию и прикрепляется к новой распределенной транзакции.

Дополнительные сведения см. в [справочнике программиста по DTC](https://docs.microsoft.com/previous-versions/windows/desktop/ms686108\(v=vs.85\)).

## <a name="c-alternative-for-sql-database-in-the-cloud"></a>Альтернатива C# для базы данных SQL в облаке

MSDTC не поддерживается для базы данных SQL Azure или хранилища данных SQL Azure.

Тем не менее, для базы данных SQL можно создать распределенную транзакцию, используя в программе C# класс .NET [System. Transactions. TransactionScope](/dotnet/api/system.transactions.transactionscope).

### <a name="other-programming-languages"></a>Другие языки программирования

Следующие языки программирования могут не обеспечивать поддержку распределенных транзакций со службой базы данных SQL:

- Машинный код C++, использующий драйверы ODBC
- Связанный сервер с использованием Transact-SQL
- Драйверы JDBC

## <a name="see-also"></a>См. также раздел

[Выполнение транзакций (ODBC)](performing-transactions-in-odbc.md)
