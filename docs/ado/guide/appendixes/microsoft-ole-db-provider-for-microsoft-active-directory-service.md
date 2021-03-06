---
title: Поставщик OLE DB Майкрософт для службы Microsoft Active Directory | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e204a4f6f7f395ca93198bc560f4a216d5a70673
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67926678"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Поставщик OLE DB Майкрософт для службы Microsoft Active Directory
Поставщик интерфейсов служб Active Directory (ADSI) позволяет ADO подключаться к разнородным службам каталогов через ADSI. Это дает приложениям ADO доступ только для чтения к службам каталогов Microsoft Windows NT 4,0 и Microsoft Windows 2000 в дополнение к любым LDAP-совместимым службам каталогов и службами каталогов Novell. Интерфейсы ADSI основаны на модели поставщика, поэтому при наличии нового поставщика, предоставляющего доступ к другому каталогу, приложение ADO будет иметь доступ к нему без проблем. Поставщик ADSI бесплатен и поддерживает Юникод.  
  
## <a name="connection-string-parameters"></a>Параметры строки подключения  
 Чтобы подключиться к этому поставщику, задайте для аргумента **поставщика** свойства [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) следующее значение:  
  
```vb
ADSDSOObject  
```  
  
 При чтении свойства [поставщика](../../../ado/reference/ado-api/provider-property-ado.md) также будет возвращена эта строка.  
  
## <a name="typical-connection-string"></a>Типичная строка подключения  
 Типичная строка подключения для этого поставщика выглядит следующим образом:  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 Строка состоит из следующих ключевых слов.  
  
|Ключевое слово|Description|  
|-------------|-----------------|  
|**Поставщик**|Указывает поставщика OLE DB для службы Active Directory.|  
|**Идентификатор пользователя.**|Указывает имя пользователя. Если это ключевое слово опущено, используется текущий вход.|  
|**Пароль**|Указывает пароль пользователя. Значение, если ключевое слово пропущено. Затем используется текущий вход в систему.|  
  
> [!NOTE]
>  При подключении к поставщику источника данных, который поддерживает проверку подлинности Windows, следует указать **Trusted_Connection = Yes** или **Integrated Security = SSPI** вместо сведений об идентификаторе пользователя и пароле в строке подключения.  
  
## <a name="command-text"></a>Текст команды  
 Поставщик в следующем синтаксисе распознает строку текста команды из четырех частей:  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Значение|Description|  
|-----------|-----------------|  
|*Root*|Указывает **путь** к объекту, с которого начинается поиск (то есть корневой элемент поиска).|  
|*Filter*|Указывает фильтр поиска в формате RFC 1960.|  
|*Атрибуты*|Указывает разделенный запятыми список атрибутов, которые должны быть возвращены.|  
|*Область*|Необязательный параметр. **Строка** , указывающая область поиска. Может применяться один из перечисленных ниже типов.<br /><br /> -Base — Поиск только базового объекта (корень поиска).<br />-Одноуровневой — Поиск только на одном уровне.<br />-Subtree — Поиск по всему поддереву.|  
  
 Пример:  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Поставщик также поддерживает SQL SELECT для текста команды. Пример:  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Remarks  
 Поставщик не принимает вызовы хранимых процедур или простые имена таблиц (например, свойство [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) всегда будет **адкмдтекст**). Более подробное описание элементов текста команды см. в документации по интерфейсам службы Active Directory.  
  
## <a name="recordset-behavior"></a>Поведение набора записей  
 В следующих таблицах перечислены функции, доступные в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) , открытом с помощью этого поставщика. Доступен только статический тип курсора (**адопенстатик**).  
  
 Чтобы получить дополнительные сведения о поведении **набора записей** для конфигурации поставщика, выполните метод [поддерживает](../../../ado/reference/ado-api/supports-method.md) и перечислите коллекцию [свойств](../../../ado/reference/ado-api/properties-collection-ado.md) **набора записей** , чтобы определить, имеются ли связанные с поставщиком динамические свойства.  
  
 **Доступность стандартных свойств набора записей ADO:**  
  
|Свойство|доступность;|  
|--------------|------------------|  
|[Примеры absolutepage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|чтение/запись|  
|[Примеры AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|чтение/запись|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|Только для чтения|  
|[BOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|  
|[Закладка](../../../ado/reference/ado-api/bookmark-property-ado.md)|чтение/запись|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|чтение/запись|  
|[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|всегда **адусесервер**|  
|[Примеры CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|всегда **адопенстатик**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|всегда **адедитноне**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|Только для чтения|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|чтение/запись|  
|[LockType](../../../ado/reference/ado-api/locktype-property-ado.md)|чтение/запись|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|недоступно|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|чтение/запись|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|Только для чтения|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|чтение/запись|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|Только для чтения|  
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|чтение/запись|  
|[Состояние](../../../ado/reference/ado-api/state-property-ado.md)|Только для чтения|  
|[Состояние](../../../ado/reference/ado-api/status-property-ado-recordset.md)|Только для чтения|  
  
 **Доступность стандартных методов набора записей ADO:**  
  
|Метод|Имеющ?|  
|------------|----------------|  
|[Вызов](../../../ado/reference/ado-api/addnew-method-ado.md)|нет|  
|[Отмена](../../../ado/reference/ado-api/cancel-method-ado.md)|нет|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|нет|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|нет|  
|[Клонировать](../../../ado/reference/ado-api/clone-method-ado.md)|Да|  
|[Закрыть](../../../ado/reference/ado-api/close-method-ado.md)|Да|  
|[Удаление](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|нет|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Да|  
|[Переместить](../../../ado/reference/ado-api/move-method-ado.md)|Да|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Да|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Да|  
|[Открыть](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Да|  
|[Повтор](../../../ado/reference/ado-api/requery-method.md)|Да|  
|[Повторная синхронизация](../../../ado/reference/ado-api/resync-method.md)|Да|  
|[Принтер](../../../ado/reference/ado-api/supports-method.md)|Да|  
|[Обновляют](../../../ado/reference/ado-api/update-method.md)|нет|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|нет|  
  
 Дополнительные сведения о ADSI и особенностях поставщика см. в документации по интерфейсам Active Directory служб или на веб-странице ADSI.  
  
## <a name="see-also"></a>См. также:  
 [Свойство CommandType (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [Свойство ConnectionString (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Коллекция Properties (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Свойство Provider (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Объект Recordset (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Метод Supports](../../../ado/reference/ado-api/supports-method.md)
