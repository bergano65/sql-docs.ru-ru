---
title: Диспетчер подключений Azure Resource Manager | Документы Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL13.DTS.DESIGNER.AFPARMCM.F1
- SQL14.DTS.DESIGNER.AFPARMCM.F1
ms.assetid: 8ce8024f-153f-4066-b607-0d36fefc79ed
author: Lingxi-Li
ms.author: lingxl
ms.openlocfilehash: cb8482fe4acee529da7462f5eb9400f2738439d6
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67968149"
---
# <a name="azure-resource-manager-connection-manager"></a>Диспетчер подключений Azure Resource Manager

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


**Диспетчер подключений Azure Resource Manager** позволяет пакету служб SSIS управлять ресурсами Azure с помощью [субъекта-службы](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal).

**Диспетчер подключений Azure Resource Manager** входит в состав [пакета дополнительных компонентов SQL Server Integration Services (SSIS) для Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md).

Чтобы создать и настроить **диспетчер подключений Azure Resource Manager**, выполните указанные ниже действия:

1. В диалоговом окне **Добавление диспетчера соединений со службами SSIS** выберите **AzureResourceManager**и щелкните **Добавить**.
2. В диалоговом окне **редактора диспетчера подключений Azure Resource Manager** укажите **Идентификатор приложения**, **Ключ приложения** и **Идентификатор клиента** для субъекта-службы. Дополнительные сведения об этих свойствах см. [этой](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal) статье.
3. Чтобы закрыть диалоговое окно, нажмите кнопку **ОК** .
4. Свойства созданного диспетчера соединений можно просмотреть в окне **Свойства** .
