---
title: Свойство ProtocolDLL (класс clientnetworkprotocol)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
apiname:
- ProtocolDLL Property (ClientNetworkProtocol Class)
apilocation:
- sqlmgmproviderxpsp2up.mof
apitype: MOFDef
helpviewer_keywords:
- ProtocolDLL property
ms.assetid: fe8650d5-7b9d-46f8-bf74-baf1d9d2a06a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b671dab32f21317c181fc1139726e6af279cb0c9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73660253"
---
# <a name="protocoldll-property-clientnetworkprotocol-class"></a>Свойство ProtocolDLL (класс ClientNetworkProtocol)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  Возвращает имя DLL-файла, необходимого сетевому протоколу, заданному в параметре [Настройка клиентских протоколов](https://technet.microsoft.com/library/ms181035.aspx).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
object.ProtocolDLL [= value]  
```  
  
## <a name="parts"></a>Компоненты  
 *объектами*  
 A [класса ClientNetworkProtocol](../../../relational-databases/wmi-provider-configuration-classes/clientnetworkprotocol-class/clientnetworkprotocol-class.md) , который представляет сетевой протокол, используемый клиентом [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
## <a name="property-valuereturn-value"></a>Значение свойства/возвращаемое значение  
 Строковое значение, определяющее DLL-файл протокола, необходимый для клиентского сетевого протокола.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="see-also"></a>См. также:  
 [Настройка сетевых протоколов клиента и сетевых библиотек](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
