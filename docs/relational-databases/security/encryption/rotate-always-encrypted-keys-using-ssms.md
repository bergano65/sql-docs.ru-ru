---
title: Циклический сдвиг ключей Always Encrypted с помощью SQL Server Management Studio | Документация Майкрософт
ms.custom: ''
ms.date: 10/01/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.COLUMNMASTERKEY.ROTATION.F1
- sql13.SWB.COLUMNMASTERKEY.CLEANUP.F1
helpviewer_keywords:
- Always Encrypted, configure with SSMS
ms.assetid: 29816a41-f105-4414-8be1-070675d62e84
author: jaszymas
ms.author: jaszymas
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5d0a96f061f01749194cd3f0d1be1aae5443ff8a
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "73595709"
---
# <a name="rotate-always-encrypted-keys-using-sql-server-management-studio"></a>Ротация ключей Always Encrypted с помощью SQL Server Management Studio
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

В этой статье описаны задачи для выполнения циклического сдвига главных ключей столбцов и ключей шифрования столбцов Always Encrypted с помощью [SQL Server Management Studio (SSMS)](../../../ssms/download-sql-server-management-studio-ssms.md).

Обзор управления ключами Always Encrypted, включая общие рекомендации и важные вопросы безопасности, см. в разделе [Общие сведения об управлении ключами Always Encrypted](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md).

<a name="rotatecmk"></a>
## <a name="rotate-column-master-keys"></a>Выполнение циклического сдвига главных ключей столбцов 

Смена главного ключа столбца — это процесс замены существующего главного ключа столбца новым главным ключом столбца. Смена ключа может потребоваться в случае его компрометации или для обеспечения соответствия политикам или нормам организации, предусматривающим регулярную смену ключей шифрования. Процедура смены главного ключа столбца включает в себя действия по расшифровке ключей шифрования столбцов, которые защищены с помощью текущего главного ключа столбца, их повторному шифрованию с помощью нового главного ключа столбца и обновлению метаданных ключа. 

### <a name="step-1-provision-a-new-column-master-key"></a>Шаг 1. Подготовка нового главного ключа столбца

Выполните действия, представленные в разделе [Подготовка главных ключей столбцов в диалоговом окне "Создание главного ключа столбца"](configure-always-encrypted-keys-using-ssms.md#provision-column-master-keys-with-the-new-column-master-key-dialog).

### <a name="step-2-encrypt-column-encryption-keys-with-the-new-column-master-key"></a>Шаг 2. Шифрование ключей шифрования столбцов с помощью нового главного ключа столбца

Как правило, главный ключ столбца защищает один или несколько ключей шифрования столбцов. Каждый ключ шифрования столбца имеет зашифрованное значение, хранящееся в базе данных, которое является результатом шифрования ключа шифрования столбца с помощью главного ключа столбца.
На этом шаге необходимо зашифровать все ключи шифрования столбцов, защищенные заменяемым главным ключом столбца, с помощью нового главного ключа столбца и сохранить новое зашифрованное значение в базе данных. В результате каждый ключ шифрования столбца, затрагиваемый сменой, будет иметь два зашифрованных значения: одно значение, зашифрованное существующим главным ключом столбца, и новое значение, зашифрованное новым главным ключом столбца.

1.  В **обозревателе объектов** перейдите к папке **Безопасность > Ключи Always Encrypted > Главные ключи столбцов** и найдите главный ключ столбца, который нужно сменить.
2.  Щелкните правой кнопкой мыши этот главный ключ столбца и выберите **Сменить**.
3.  В диалоговом окне **Смена главного ключа столбца** выберите имя нового главного ключа столбца, созданного на шаге 1, в поле **Целевой объект** .
4.  Просмотрите список ключей шифрования столбца, защищенных существующими главными ключами столбца. Эти ключи будут затронуты сменой.
5.  Нажмите кнопку **ОК**.

Среда SQL Server Management Studio получит метаданные ключей шифрования столбцов, защищенных с помощью старого главного ключа столбца, и метаданные старого и нового главных ключей столбцов. Затем среда SSMS с помощью метаданных главного ключа столбца получит доступ к хранилищу ключей, содержащему старый главный ключа столбца, и расшифрует ключи шифрования столбцов. После этого среда SSMS обратится в хранилище ключей, содержащее новый главный ключ столбца, чтобы создать набор зашифрованных значений ключей шифрования столбцов. Затем среда добавит новые значения в метаданные (создав и выполнив инструкции [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md) ).

> [!NOTE]
> Убедитесь, что каждый ключ шифрования столбца, зашифрованный старым главным ключом столбца, не зашифрован с помощью какого-либо другого главного ключа столбца. Другими словами, каждый ключ шифрования столбца, затрагиваемый сменой, должен иметь ровно одно зашифрованное значение в базе данных. Если какой-либо из затрагиваемых ключей шифрования столбца имеет несколько зашифрованных значений, необходимо удалить лишние значения, прежде чем продолжать смену (см. *шаг 4* по удалению зашифрованного значения ключа шифрования столбца).

### <a name="step-3-configure-your-applications-with-the-new-column-master-key"></a>Шаг 3. Настройка приложений с помощью нового главного ключа столбца

На этом шаге необходимо убедиться, что все клиентские приложения, запрашивающие столбцы базы данных и защищенные с помощью главного ключа столбца, который планируется сменить (то есть столбцы базы данных зашифрованы с помощью ключа шифрования столбца, который зашифрован заменяемым главным ключом столбца), имеют доступ к новому главному ключу столбца. Этот шаг зависит от типа хранилища ключей, используемого для хранения нового главного ключа столбца. Пример:

- Если новый главный ключ столбца является сертификатом из хранилища сертификатов Windows, необходимо развернуть этот сертификат в том же расположении хранилища сертификатов (*текущего пользователя* или *локального компьютера*), которое указано в пути к главному ключу столбца в базе данных. Приложение должно иметь доступ к этому сертификату:
  - Если сертификат хранится в расположении хранилища сертификатов *текущего пользователя*, сертификат необходимо импортировать в хранилище текущего пользователя удостоверения Windows приложения.
  - Если сертификат хранится в расположении хранилища сертификатов *локального компьютера*, удостоверение Windows приложения должно иметь разрешение на доступ к этому сертификату.
- Если новый главный ключ столбца хранится в хранилище ключей Microsoft Azure, приложение должно быть реализовано так, чтобы оно могло пройти проверку подлинности в Azure и имело разрешение на доступ к ключу.

Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

> [!NOTE]
> На этом этапе процедуры смены и старый, и новый главные ключи столбца являются действительными и могут использоваться для доступа к данным.

### <a name="step-4-clean-up-column-encryption-key-values-encrypted-with-the-old-column-master-key"></a>Шаг 4. Очистка значений ключа шифрования столбца, зашифрованных с помощью старого главного ключа столбца.

После настройки использования нового главного ключа столбца во всех приложениях удалите из базы данных значения ключей шифрования столбца, зашифрованные с помощью *старого* главного ключа столбца. После удаления старых значений все будет готово к новой смене (учитывайте, что для смены главного ключа столбца каждый ключ шифрования столбца, защищенный с помощью главного ключа столбца, должен иметь ровно одно зашифрованное значение).

Еще одна причина для очистки старого значения до архивации или удаления старого главного ключа связана с производительностью: при запросе зашифрованного столбца драйвер клиента с поддержкой постоянного шифрования может попытаться расшифровать два значения — старое и новое. У драйвера нет сведения о том, какой из двух главных ключей столбца является действительным в среде приложения. Поэтому драйвер будет извлекать оба зашифрованных значения с сервера. Если одно из значений не удается расшифровать, так как оно защищено недоступным главным ключом столбца (например, это старый главный ключ столбца, который был удален из хранилища), драйвер будет пытаться расшифровать другое значение с помощью нового главного ключа столбца.

> [!WARNING]
> Если удалить значение ключа шифрования столбца до того, как его соответствующий главный ключ столбца станет доступным для приложения, это приложение больше не сможет расшифровывать столбец базы данных.

1.  В **обозревателе объектов** перейдите в папку **Безопасность>Ключи постоянного шифрования** и найдите главный ключ столбца, который требуется сменить.
2.  Щелкните правой кнопкой мыши существующий главный ключ столбца и выберите **Очистить**.
3.  Просмотрите список значений ключей шифрования столбцов для удаления.
4.  Нажмите кнопку **ОК**.

Среда SQL Server Management Studio выполнит инструкции [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md) для удаления зашифрованных значений ключей шифрования столбцов, которые зашифрованы с помощью старого главного ключа столбца.

### <a name="step-5-delete-metadata-for-your-old-column-master-key"></a>Шаг 5. Удаление метаданных для старого главного ключа столбца

Если вы решили удалить определение старого главного ключа столбца из базы данных, выполните действия, описанные ниже.

1. В **обозревателе объектов** перейдите в папку **Безопасность>Ключи постоянного шифрования>Главные ключи столбцов** и найдите старый главный ключ столбца, который требуется удалить из базы данных.
2. Щелкните правой кнопкой мыши старый главный ключ столбца и выберите **Удалить**. (Будет создана и выполнена инструкция [DROP COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/drop-column-master-key-transact-sql.md) для удаления метаданных главного ключа столбца.)
3. Нажмите кнопку **ОК**.

> [!NOTE]
> Настоятельно рекомендуется не удалять старый главный ключ столбца после смены без возможности восстановления. Старый главный ключ столбца следует сохранить в его текущем хранилище ключей или скопировать в другое надежное место. Старый ключ потребуется при восстановлении базы данных из файла резервной копии на момент времени, предшествующий настройке нового главного ключа столбца.

### <a name="permissions-for-rotating-column-master-key"></a>Разрешения на смену главных ключей столбцов

Для смены главного ключа столбца необходимы указанные далее разрешения базы данных.

- **ALTER ANY COLUMN MASTER KEY** — требуется для создания метаданных для нового главного ключа столбца и удаления метаданных для старого главного ключа столбца.
- **ALTER ANY COLUMN ENCRYPTION KEY** — требуется для изменения метаданных ключа шифрования столбца (для добавления новых зашифрованных значений).

Необходимо также иметь доступ к старому и новому главным ключам столбцов в их хранилищах. Чтобы получить доступ к хранилищу ключей и использовать главный ключ столбца, вам могут потребоваться указанные далее разрешения для хранилища ключей и (или) ключа.
- **Хранилище сертификатов — локальный компьютер** — требуется доступ на чтение к сертификату, который используется в качестве главного ключа столбца, либо необходимо быть администратором компьютера.
- **Хранилище ключей Azure** — требуются разрешения *create*, *get*, *unwrapKey*, *wrapKey*, *sign*и *verify* к хранилищу, содержащему главный ключ столбца.
- **Поставщик хранилища ключей (CNG)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и KSP.
- **Поставщик служб шифрования (CAPI)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и CSP.

Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

<a name="rotatecek"></a> 
## <a name="rotate-column-encryption-keys"></a>Выполнение циклического сдвига ключей шифрования столбцов

Процедура смены ключа шифрования столбца включает в себя действия по расшифровке данных во всех столбцах, которые зашифрованы с помощью подлежащего смене ключа, и повторному шифрованию данных с помощью нового ключа шифрования столбца.

>[!NOTE]
> Смена ключа шифрования столбца может занимать очень много времени, если размер таблиц, содержащих столбцы, зашифрованные с помощью заменяемого ключа, слишком велик. Во время повторного шифрования данных приложения не смогут выполнять запись в затрагиваемые таблицы. Поэтому организации необходимо очень тщательно спланировать процесс смены ключа шифрования столбца.
Для смены ключа шифрования столбца используется мастер постоянного шифрования.

1.  Откройте мастер в базе данных. Для этого щелкните правой кнопкой мыши базу данных, наведите курсор на пункт **Задачи**, а затем щелкните **Зашифровать столбцы**.
2.  Прочитайте страницу **Введение** , а затем нажмите кнопку **Далее**.
3.  На странице **Выбор столбцов** разверните таблицы и найдите все подлежащие замене столбцы, которые зашифрованы с помощью старого ключа шифрования столбца.
4.  Для каждого такого столбца задайте в качестве значения **ключа шифрования** новый автоматически созданный ключ. **Примечание.** Можно также создать новый ключ шифрования столбца перед запуском мастера — см. раздел [Подготовка ключей шифрования столбцов в диалоговом окне "Создание ключа шифрования столбца"](configure-always-encrypted-keys-using-ssms.md#provision-column-encryption-keys-with-the-new-column-encryption-key-dialog).
5.  На странице **Конфигурация главного ключа** выберите расположение для сохранения нового ключа и источник главного ключа, а затем нажмите кнопку **Далее**. **Примечание.** При использовании существующего ключа шифрования столбца (не созданного автоматически) на этой странице ничего делать не нужно.
6.  На странице **Проверка**выберите, требуется ли немедленно запустить сценарий, или создайте сценарий PowerShell и нажмите кнопку **Далее**.
7.  На странице **Сводка** просмотрите выбранные параметры и нажмите кнопку **Готово**, чтобы закрыть мастер.
8.  В **обозревателе объектов**перейдите в папку **Безопасность/Ключи постоянного шифрования/Ключи шифрования столбцов** и найдите старый ключ шифрования столбца, который требуется удалить из базы данных. Щелкните ключ правой кнопкой мыши и выберите команду **Удалить**.

### <a name="permissions-for-rotating-column-encryption-keys"></a>Разрешения на смену ключей шифрования столбцов

Для смены ключа шифрования столбца необходимы указанные далее разрешения базы данных. **ALTER ANY COLUMN MASTER KEY** — требуется при использовании нового автоматически созданного ключа шифрования столбца (также будут созданы главный ключ столбца и его новые метаданные).
**ALTER ANY COLUMN ENCRYPTION KEY** — требуется для добавления метаданных для нового ключа шифрования столбца.

Необходимо также иметь доступ к главным ключам столбцов для старого и нового ключей шифрования столбцов. Чтобы получить доступ к хранилищу ключей и использовать главный ключ столбца, вам могут потребоваться указанные далее разрешения для хранилища ключей и (или) ключа.
- **Хранилище сертификатов — локальный компьютер** — требуется доступ на чтение к сертификату, который используется в качестве главного ключа столбца, либо необходимо быть администратором компьютера.
- **Хранилище ключей Azure** — требуются разрешения get, unwrapKey и verify к хранилищу, содержащему главный ключ столбца.
- **Поставщик хранилища ключей (CNG)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и KSP.
- **Поставщик служб шифрования (CAPI)** — необходимые разрешения и учетные данные, которые могут быть запрошены при использовании хранилища ключей или ключа, зависят от конфигурации хранилища и CSP.

Дополнительные сведения см. в разделе [Создание и хранение главных ключей столбцов для Always Encrypted](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md).

## <a name="next-steps"></a>Next Steps
- [Выполнение запросов к столбцам с помощью Always Encrypted с использованием SQL Server Management Studio](always-encrypted-query-columns-ssms.md)
- [Разработка приложений с помощью Always Encrypted](always-encrypted-client-development.md)

## <a name="see-also"></a>См. также:
- [Always Encrypted](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [Общие сведения об управлении ключами для Always Encrypted](overview-of-key-management-for-always-encrypted.md) 
- [Настройка функции Always Encrypted с помощью SQL Server Management Studio](configure-always-encrypted-using-sql-server-management-studio.md)
- [Настройка постоянного шифрования с помощью PowerShell](configure-always-encrypted-using-powershell.md)
- [CREATE COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/create-column-master-key-transact-sql.md)
- [DROP COLUMN MASTER KEY (Transact-SQL)](../../../t-sql/statements/drop-column-master-key-transact-sql.md)
- [CREATE COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/create-column-encryption-key-transact-sql.md)
- [ALTER COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/alter-column-encryption-key-transact-sql.md)
- [DROP COLUMN ENCRYPTION KEY (Transact-SQL)](../../../t-sql/statements/drop-column-encryption-key-transact-sql.md) 
- [sys.column_master_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-master-keys-transact-sql.md)
- [sys.column_encryption_keys (Transact-SQL)](../../../relational-databases/system-catalog-views/sys-column-encryption-keys-transact-sql.md)
