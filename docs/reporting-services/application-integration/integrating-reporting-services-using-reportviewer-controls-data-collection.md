---
title: Сбор данных в элементе управления ReportViewer
description: Элемент управления собирает анонимные данные, которые позволяют лучше понять, как клиенты используют продукт. Данные об использовании позволяют улучшать продукт в будущем с учетом требований пользователей.
author: maggiesMSFT
ms.author: maggies
ms.custom: ''
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 09/18/2018
ms.openlocfilehash: d7b70445fc4d8a29d8ebcdf7ecbffe4b54133f0e
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "74796898"
---
# <a name="integrate-reporting-services-using-reportviewer-controls---data-collection"></a>Интеграция служб Reporting Services с помощью элементов управления ReportViewer — сбор данных

Элемент управления собирает анонимные данные, которые позволяют лучше понять, как клиенты используют продукт. Данные об использовании позволяют улучшать продукт в будущем.

Описание методик сбора и использования данных Microsoft SQL Server и средства просмотра отчетов приведено в [заявлении о конфиденциальности](https://go.microsoft.com/fwlink/?LinkID=868444).

## <a name="opting-out-of-data-collection"></a>Отказ от сбора данных

Сбор данных об использовании можно отключить с помощью свойства ```EnableTelemetry```.

```xml
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

Кроме того, это можно сделать программным способом перед настройкой элемента управления.
    
```csharp
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>См. также раздел

[Using the WebForms ReportViewer Control](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md) (Использование элемента управления средства просмотра отчетов WebForms)  
[Интеграция служб Reporting Services с помощью элементов управления средства просмотра отчетов](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 



