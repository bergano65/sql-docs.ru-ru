---
title: Пользовательские свойства Excel | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: bdcc72b8-8950-47bd-88bf-5db6d48cc6bf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d8d556a199b608659a9ceaaeb3b7036155886d6c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62827237"
---
# <a name="excel-custom-properties"></a>Пользовательские свойства Excel
  **Пользовательские свойства источника**  
  
 Источник «Excel» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства источника «Excel». Все свойства доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|AccessMode|Целое число|Режим, используемый для доступа к базе данных. Возможные значения: **открытый набор строк**, **открытый набор строк из переменной**, `SQL Command`и **команда SQL из переменной**. Значение по умолчанию: **Открытый набор строк**.|  
|CommandTimeout|Целое число|Время ожидания для выполнения команды (в секундах).  Значение 0 указывает на бесконечное время ожидания.<br /><br /> **Примечание** Это свойство недоступно в диалоговом окне **Редактор источника «Excel»** , однако его можно установить при помощи окна **Расширенный редактор**.|  
|OpenRowset|String|Имя объекта базы данных, используемого для открытия набора строк.|  
|OpenRowsetVariable|String|Переменная, содержащая имя объекта базы данных, используемого для открытия набора строк.|  
|ParameterMapping|String|Сопоставление между параметрами в команде SQL и переменными.|  
|SqlCommand|String|Команда SQL для выполнения.|  
|SqlCommandVariable|String|Переменная, содержащая команду SQL для выполнения.|  
  
 Вывод и выходные столбцы источника «Excel» не имеют пользовательских свойств.  
  
 Дополнительные сведения см. в статье [Excel Source](excel-source.md).  
  
 **Пользовательские свойства назначений**  
  
 Назначение «Excel» обладает как пользовательскими свойствами, так и свойствами, общими для всех компонентов потока данных.  
  
 В следующей таблице описаны пользовательские свойства назначения «Excel». Все свойства доступны для чтения и записи.  
  
|Имя свойства|Тип данных|Описание|  
|-------------------|---------------|-----------------|  
|AccessMode|Integer (перечисление)|Значение, указывающее, как назначение получает доступ к целевой базе данных.<br /><br /> Это свойство может принимать одно из следующих значений:<br /><br /> `OpenRowset`(0) — укажите имя таблицы или представления.<br /><br /> `OpenRowset from Variable`(1) — укажите имя переменной, содержащей имя таблицы или представления.<br /><br /> `OpenRowset Using Fastload`(3) — укажите имя таблицы или представления.<br /><br /> `OpenRowset Using Fastload from Variable`(4) — укажите имя переменной, содержащей имя таблицы или представления.<br /><br /> `SQL Command`(2) — вы предоставляете инструкцию SQL.|  
|CommandTimeout|Целое число|Максимальное время ожидания в секундах, в течение которого может выполняться команда SQL. Значение **0** указывает на бесконечное время работы. Значение этого свойства по умолчанию равно **0**.<br /><br /> Примечание. Это свойство недоступно в **редакторе назначения "Excel"** , но его можно задать с помощью **расширенного редактора**.|  
|FastLoadKeepIdentity|Логическое|Значение, которое указывает, следует ли при загрузке данных копировать значения идентификаторов. Это свойство доступно только при использовании одного из параметров быстрой загрузки. Это свойство имеет значение по умолчанию **False**.|  
|FastLoadKeepNulls|Логическое|Значение параметра указывает, следует ли при загрузке данных копировать значения NULL. Это свойство доступно только при использовании одного из параметров быстрой загрузки. Это свойство имеет значение по умолчанию **False**.|  
|FastLoadMaxInsertCommitSize|Целое число|Это значение указывает размер пакетов, который назначение «Excel» пытается фиксировать во время операций быстрой загрузки. Значение по умолчанию ― **2147483647**. Значение **0** указывает, что используется единая операция фиксации после обработки всех строк.|  
|FastLoadOptions|String|Коллекция параметров быстрой загрузки. К параметрам быстрой загрузки относятся параметры блокировки таблиц и проверки ограничений. Можно указать один, оба или не указывать ни одного параметра.<br /><br /> Примечание. Некоторые свойства недоступны в **редакторе назначения "Excel"** , но их можно задать с помощью **расширенного редактора**.|  
|OpenRowset|String|Если AccessMode имеет `OpenRowset`значение, то имя таблицы или представления, к которому обращается назначение «Excel».|  
|OpenRowsetVariable|String|Если AccessMode имеет `OpenRowset from Variable`значение, имя переменной, содержащей имя таблицы или представления, к которому обращается назначение «Excel».|  
|SqlCommand|String|Если AccessMode имеет `SQL Command`значение, инструкция TRANSACT-SQL, используемая назначением «Excel» для указания целевых столбцов данных.|  
  
 У ввода и входных столбцов назначения «Excel» нет пользовательских свойств.  
  
 Дополнительные сведения см. в статье [Excel Destination](excel-destination.md).  
  
## <a name="see-also"></a>См. также:  
 [Общие свойства](../common-properties.md)  
  
  
