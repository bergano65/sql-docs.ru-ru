---
title: srv_paramtype (интерфейс API расширенных хранимых процедур) | Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramtype
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramtype
ms.assetid: badc6d36-8a87-42b5-b28c-9c4f5ded8552
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f81904fd930e22857bfa51584c2eefda813e7e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75253537"
---
# <a name="srv_paramtype-extended-stored-procedure-api"></a>srv_paramtype (API-интерфейс расширенных хранимых процедур)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]Вместо этого используйте интеграцию со средой CLR.  
  
 Возвращает тип данных параметра вызова удаленной хранимой процедуры.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
int srv_paramtype (  
SRV_PROC *  
srvproc  
,  
int  
n   
);  
```  
  
## <a name="arguments"></a>Аргументы  
 *srvproc*  
 Указатель на структуру SRV_PROC, представляющую собой дескриптор соединения с клиентом (в данном случае — дескриптор, который получил вызов удаленной хранимой процедуры). Эта структура содержит сведения, которые используются библиотекой API-интерфейса расширенных хранимых процедур для управления связью и передачи данных между приложением и клиентом.  
  
 *\n*  
 Указывает номер параметра. Первый параметр имеет значение 1.  
  
## <a name="returns"></a>Возвращает  
 Значение токена для типа данных параметра. Сведения о типах данных см. в разделе [Типы данных (интерфейс API расширенных хранимых процедур)](../../relational-databases/extended-stored-procedures-reference/data-types-extended-stored-procedure-api.md). Если параметра с номером *n* или удаленной хранимой процедуры не существует, возвращается значение - 1.  
  
 Эта функция возвращает следующие значения, если параметр относится к одному из [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] типов данных.  
  
|Новые типы данных|Возвращаемое значение|  
|--------------------|------------------|  
|**BITN**|SRVBIT|  
|**BIGVARCHAR**|VARCHAR|  
|**BIGCHAR**|CHAR|  
|**BIGBINARY**|BINARY|  
|**BIGVARBINARY**|VARBINARY|  
|**NCHAR**|CHAR|  
|**NVARCHAR**|VARCHAR|  
|**ТИПЫ**|-1|  
  
## <a name="remarks"></a>Remarks  
 Когда удаленная хранимая процедура вызывается с параметрами, эти параметры могут быть переданы либо по имени, либо по позиции — без указания имени. Если при вызове удаленной хранимой процедуры часть параметров передается по имени, а часть — по позиции, возникает ошибка. Обработчик SRV_RPC по-прежнему вызывается, но он выглядит так, как если бы параметры не существовали, а **srv_rpcparams** возвращает 0.  
  
> [!IMPORTANT]  
>  Необходимо тщательно просмотреть исходный код расширенных хранимых процедур и проверить скомпилированные библиотеки DLL перед их установкой на рабочий сервер. Сведения о проверке безопасности см. на следующем [веб-сайте Майкрософт](https://www.microsoft.com/msrc?rtc=1).  
  
## <a name="see-also"></a>См. также:  
 [API srv_paraminfo &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paraminfo-extended-stored-procedure-api.md)   
 [API srv_rpcparams &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-rpcparams-extended-stored-procedure-api.md)  
  
  
