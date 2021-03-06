---
title: Установка azdata с помощью zypper
titleSuffix: SQL Server big data clusters
description: Сведения о том, как установить средство azdata для установки Кластеров больших данных и управления ими с помощью zypper.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.date: 01/07/2020
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: a02b4f0707d98d8acc9e65a2a27cee8d886c1ae7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75728575"
---
# <a name="install-azdata-with-zypper"></a>Установка `azdata` с помощью zypper

Для дистрибутивов Linux с `zypper` существует пакет для `azdata-cli`. Пакет CLI протестирован для версий Linux, которые используют `zyper`, а именно:

- openSUSE Leap 42.2 и более поздних версий;
- SLES 12 SP 2 и более поздних версий.

[!INCLUDE [azdata-package-installation-remove-pip-install](../includes/azdata-package-installation-remove-pip-install.md)]

## <a name="install-with-zypper"></a>Установка с помощью zypper
>[!IMPORTANT]
>Пакет RPM для `azdata-cli` зависит от пакета python3. В вашей системе может быть установлена более ранняя версия Python, чем *требуемая версия 3.6.x*. Если для вас это важно, найдите другой пакет python3 или выполните инструкции по установке вручную с помощью [`pip`](deploy-install-azdata-pip.md).

1. Установите зависимости, необходимые для установки `azdata-cli`.

   ```bash
   sudo zypper install -y curl
   ```

1. Импортируйте ключ репозитория Майкрософт.

   ```bash
   sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
   ```

1. Создайте сведения о локальном репозитории.

   ```bash
   sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2019.repo
   ```

1. Установка

   ```bash
   sudo zypper install --from packages-microsoft-com-mssql-server-2019 -y azdata-cli
   ```

## <a name="verify-install"></a>Проверка установки

   ```bash
   azdata
   azdata --version
   ```

## <a name="update"></a>Update

Выполните обновление `azdata-cli` с помощью команды `zypper update`.

   ```bash
   sudo zypper refresh
   sudo zypper update azdata-cli
   ```

## <a name="uninstall"></a>Удаление

Удалите пакет из системы.

```bash
   sudo zypper removerepo azdata-cli
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о кластерах больших данных см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
