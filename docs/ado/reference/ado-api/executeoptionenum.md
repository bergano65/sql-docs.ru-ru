---
title: Ексекутеоптионенум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ExecuteOptionEnum
helpviewer_keywords:
- ExecuteOptionEnum enumeration [ADO]
ms.assetid: 68bfa83a-5df4-4bef-8736-0f88ae8c29ea
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bef70bd72425e749865e31ecf162e719737dd272
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67932846"
---
# <a name="executeoptionenum"></a>ExecuteOptionEnum
Указывает, как поставщик должен выполнять команду.  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адасинцексекуте**|0x10|Указывает, что команда должна выполняться асинхронно.<br /><br /> Это значение не может быть объединено со значением [Коммандтипинум](../../../ado/reference/ado-api/commandtypeenum.md) **адкмдтабледирект**.|  
|**адасинкфетч**|0x20|Указывает, что оставшиеся строки после начального количества, указанные в свойстве [CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md) , должны быть получены асинхронно.|  
|**адасинкфетчнонблоккинг**|0x40|Указывает, что главный поток никогда не блокируется при извлечении. Если запрошенная строка не была получена, то текущая строка автоматически переместится в конец файла.<br /><br /> При открытии [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) из [потока](../../../ado/reference/ado-api/stream-object-ado.md) , содержащего сохраняемый **набор записей**, **адасинкфетчнонблоккинг** не будет иметь никакого влияния; операция будет синхронной и заблокированной.<br /><br /> **адасинчфетчнонблоккинг** не действует, если для открытия **набора записей**используется параметр [адкмдтабледирект](../../../ado/reference/ado-api/commandtypeenum.md) .|  
|**адексекутенорекордс**|0x80|Указывает, что текст команды является командой или хранимой процедурой, которая не возвращает строки (например, команда, которая вставляет только данные). Если какие бы то ни было строки получены, они отбрасываются и не возвращаются.<br /><br /> **адексекутенорекордс** можно передать только как необязательный параметр для метода Execute **команды** или **соединения** .|  
|**адексекутестреам**|0x400|Указывает, что результаты выполнения команды должны возвращаться в виде потока.<br /><br /> **адексекутестреам** может быть передан в метод **EXECUTE** только как необязательный параметр.|  
|**адексекутерекорд**||Указывает, что **CommandText** является командой или хранимой процедурой, возвращающей одну строку, которая должна возвращаться в качестве объекта **записи** .|  
|**адоптионунспеЦифиед**|-1|Указывает, что команда не указана.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. Ексекутеоптион. АСИНЦЕКСЕКУТЕ|  
|Адоенумс. Ексекутеоптион. АСИНКФЕТЧ|  
|Адоенумс. Ексекутеоптион. АСИНКФЕТЧНОНБЛОККИНГ|  
|Адоенумс. Ексекутеоптион. незаписи|  
|Адоенумс. Ексекутеоптион. не указано|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод Execute (объект Command ADO)](../../../ado/reference/ado-api/execute-method-ado-command.md)|[Метод Execute (объект Connection ADO)](../../../ado/reference/ado-api/execute-method-ado-connection.md)|  
|[Метод Open (объект Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[Метод Requery](../../../ado/reference/ado-api/requery-method.md)|
