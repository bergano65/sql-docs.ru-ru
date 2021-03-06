---
title: 'ISSCommandWithParameters:: GetParameterProperties (OLE DB) | Документация Майкрософт'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISSCommandWithParameters::GetParameterProperties (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetParameterProperties method
ms.assetid: 7f4cc5ea-d028-4fe5-9192-bd153ab3c26c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d492a64b6d8a4e8ddf7de27067f1f0bcfef205e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62638086"
---
# <a name="isscommandwithparametersgetparameterproperties-ole-db"></a>ISSCommandWithParameters::GetParameterProperties (OLE DB)
  Возвращает массив структур SSPARAMPROPS, представляющих собой множества свойств, по одному множеству свойств SSPARAMPROPS на каждый параметр определяемого пользователем типа или XML.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
HRESULT GetParameterProperties(  
DB_UPARAMS *pcParams,  
SSPARAMPROPS **prgParamProperties);  
```  
  
## <a name="arguments"></a>Аргументы  
 *пкпарамс*[out] [in]  
 Указатель на область памяти, где содержится количество структур SSPARAMPROPS, возвращаемых в параметре *prgParamProperties*.  
  
 *пргпарампропертиес*[out]  
 Указатель на область памяти, в которую будет возвращен массив структур SSPARAMPROPS. Поставщик выделяет память для структур и возвращает адрес в эту память. Потребитель освобождает эту память с помощью **unalloc:: Free** , если она больше не нуждается в структурах. Перед вызовом метода **unalloc:: Free** для *пргпарампропертиес*потребитель должен также вызвать **вариантклеар** для свойства *управляемое vValue* каждой структуры DBPROP, чтобы предотвратить утечку памяти в случаях, когда вариант содержит ссылочный тип (например, BSTR). Если *пкпарамс* имеет нулевое значение на выходе или возникает ошибка, отличная от DB_E_ERRORSOCCURRED, поставщик не выделяет память и гарантирует, что *пргпарампропертиес* является пустым указателем на выходе.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Метод **GetParameterProperties** возвращает те же коды ошибок, что и метод Core OLE DB **ICommandProperties::** , за исключением того, что DB_S_ERRORSOCCURRED и DB_E_ERRORSOCCURED не могут быть вызваны.  
  
## <a name="remarks"></a>Remarks  
 **ISSCommandWithParameters:: GetParameterProperties** действует согласованно с уважением **GetParameterInfo**. Если [ISSCommandWithParameters:: SetParameterProperties](isscommandwithparameters-setparameterproperties-ole-db.md) или **SetParameterInfo** не были вызваны или вызваны с кпарамс равными нулю, **GetParameterInfo** наследует сведения о параметрах и возвращает this. Если **ISSCommandWithParameters:: SetParameterProperties** или **SetParameterInfo** были вызваны по крайней мере для одного параметра, **ISSCommandWithParameters:: GetParameterProperties** Возвращает свойства только для тех параметров, для которых был вызван **ISSCommandWithParameters:: SetParameterProperties** . Если **ISSCommandWithParameters:: SetParameterProperties** вызывается после **ISSCommandWithParameters:: GetParameterProperties** или **GetParameterInfo**, последующие вызовы **ISSCommandWithParameters:: GetParameterProperties** возвращают переопределенные значения для этих параметров, для которых был вызван **ISSCommandWithParameters:: SetParameterProperties** .  
  
 Структура SSPARAMPROPS определена следующим образом.  
  
 `struct SSPARAMPROPS {`  
  
 `DBORDINAL iOrdinal;`  
  
 `ULONG cPropertySets;`  
  
 `DBPROPSET *rgPropertySets;`  
  
 `};`  
  
|Участник|Description|  
|------------|-----------------|  
|*иординал*|Порядковый номер переданного параметра.|  
|*кпропертисетс*|Количество структур DBPROPSET в *rgPropertySets*.|  
|*rgPropertySets*|Указатель на буфер, в который будет возвращен массив структур DBPROPSET.|  
  
## <a name="see-also"></a>См. также:  
 [ISSCommandWithParameters &#40;OLE DB&#41;](isscommandwithparameters-ole-db.md)  
  
  
