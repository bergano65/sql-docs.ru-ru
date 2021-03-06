---
title: Параметр SORT_IN_TEMPDB для индексов | Документация Майкрософт
ms.custom: ''
ms.date: 04/24/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- SORT_IN_TEMPDB option
- disk space [SQL Server], indexes
- space [SQL Server], indexes
- tempdb database [SQL Server], indexes
- indexes [SQL Server], tempdb database
- index creation [SQL Server], tempdb database
ms.assetid: 754a003f-fe51-4d10-975a-f6b8c04ebd35
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 03dbb54a41ef319b7a44185cee00d5de7d46b126
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67909546"
---
# <a name="sort_in_tempdb-option-for-indexes"></a>Параметр SORT_IN_TEMPDB для индексов
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  При создании или перестроении индекса можно установить параметр SORT_IN_TEMPDB в значение ON, чтобы компонент [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] использовал базу данных **tempdb** для хранения промежуточных результатов сортировки, которые применяются для построения индекса. Данный параметр увеличивает место на диске, временно занимаемое при построении индекса, но с его помощью можно сократить время, необходимое для создания или перестроения индекса, когда **tempdb** находится в наборе дисков, отличном от набора, используемого для размещения пользовательской базы данных. Дополнительные сведения о параметре **tempdb**см. в разделе [Настройка параметра конфигурации сервера index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md).  
  
## <a name="phases-of-index-building"></a>Фазы построения индекса  
 Процесс построения индекса компонентой [!INCLUDE[ssDE](../../includes/ssde-md.md)] состоит из следующих фаз.  
  
-   Сначала компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] просматривает страницы данных базовой таблицы, чтобы получить значение ключа, и строит конечную строку индекса для каждой строки данных. Когда внутренние буферы сортировки заполняются конечными элементами индекса, эти элементы сортируются и записываются на диск как промежуточный проход сортировки. Затем компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] возобновляет просмотр страниц данных, пока буфер сортировки не заполнится вновь. Процедура просмотра нескольких страниц данных с последующей сортировкой и записью результатов сортировки продолжается до тех пор, пока не будут обработаны все строки базовой таблицы.  
  
     В кластеризованном индексе конечные строки являются строками данных таблицы, поэтому промежуточная сортировка содержит все строки. В некластеризованном индексе конечные строки могут содержать неключевые столбцы, но в целом они меньше, чем кластеризованный индекс. Если ключи индекса большие или в индекс входят несколько неключевых столбцов, то операция некластеризованной сортировки может быть большей. Дополнительные сведения о неключевых столбцах см. в разделе [Create Indexes with Included Columns](../../relational-databases/indexes/create-indexes-with-included-columns.md).  
  
-   Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] объединяет отсортированные потоки конечных строк индекса в единый отсортированный поток. Компонент объединенной сортировки компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] начинает с первой страницы каждой операции сортировки, отыскивает самый нижний ключ во всех страницах и передает эту конечную строку компоненту создания индекса. Затем обрабатывается следующий индекс снизу, потом следующий и т. д. Когда последняя конечная строка индекса извлекается из страницы операции сортировки, процесс переходит к следующей странице этой операции сортировки. Когда все страницы в операции сортировки обработаны, кластер страниц освобождается. Когда каждая конечная строка индекса пересылается в компонент создания индекса, она включается в конечную страницу индекса в буфере. Каждая конечная страница записывается по мере заполнения. По мере записи конечных страниц компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] также строит верхние уровни индекса. Каждая страница индекса верхнего уровня записывается по мере заполнения.  
  
## <a name="sort_in_tempdb-option"></a>SORT_IN_TEMPDB, параметр  
 Если параметр SORT_IN_TEMPDB имеет значение OFF, устанавливаемое по умолчанию, то операции сортировки хранятся в целевой файловой группе. Во время первой фазы создания индекса чередующиеся операции чтения страниц базовой таблицы и записи операций сортировки перемещают головки чтения и записи диска из одной области диска в другую. Головки находятся в области страницы данных, когда просматриваются страницы данных. Они перемещаются в область свободного пространства, когда буферы сортировки заполняются и текущая операция сортировки записывается на диск, а затем перемещаются назад в область страницы данных при возобновлении просмотра табличной страницы. Скорость головки на чтение-запись больше во второй фазе. На этом этапе процесса сортировки, как правило, чередуются операции чтения из каждой области сортировки. Как операции сортировки, так и новые страницы индекса строятся в целевой файловой группе. Это значит, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] одновременно распределяет операции чтения по операциям сортировки, при этом приходится периодически переходить к экстентам индекса для записи новых страниц индекса по мере их заполнения.  
  
 Если параметр SORT_IN_TEMPDB имеет значение ON и база данных **tempdb** размещена на ином наборе дисков, нежели целевая файловая группа, то чтение страниц данных в первой фазе выполняется не с того диска, на который производится запись в рабочую область сортировки **tempdb**. Это значит, что считывание ключей данных с диска проводится в более последовательной манере, и операции записи на диск **tempdb** также в основном последовательные, как и операции записи при построении окончательного индекса. Даже если другие пользователи используют базу данных и обращаются по раздельным дисковым адресам, общая последовательность операций чтения и записи будет более эффективной, если задан параметр SORT_IN_TEMPDB.  
  
 Благодаря параметру SORT_IN_TEMPDB может быть повышена непрерывность экстентов индекса, особенно если параллельно не обрабатывается операция CREATE INDEX. Экстенты рабочей области сортировки освобождаются довольно беспорядочно относительно их местоположения в базе данных. Если рабочие области сортировки содержатся в целевой файловой группе, то по мере освобождения экстентов сортировки они могут быть задействованы по запросу для хранения структуры индекса в процессе ее построения. Это может привести к некоторому разупорядочению местонахождений экстентов индексов. Если экстенты сортировки хранятся в **tempdb**раздельно, то последовательность их освобождения не влияет на расположение экстентов индекса. Кроме того, если промежуточные операции сортировки хранятся в **tempdb** вместо целевой файловой группы, то в целевой файловой группе имеется больше доступного пространства. В результате увеличивается вероятность того, что экстенты индекса будут последовательными.  
  
 Параметр SORT_IN_TEMPDB влияет только на текущую инструкцию. В метаданных не отмечается, был ли индекс сортирован в **tempdb**. Например, если создается некластеризованный индекс с использованием параметра SORT_IN_TEMPDB, а позднее создается кластеризованный индекс без указания этого параметра, то компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] не использует параметр при повторном создании некластеризованного индекса.  
  
> [!NOTE]  
>  Если выполнение сортировки не требуется или если сортировка может быть выполнена в памяти, параметр SORT_IN_TEMPDB пропускается.  
  
## <a name="disk-space-requirements"></a>Требования к месту на диске  
 При установке параметра SORT_IN_TEMPDB в значение ON требуется достаточно свободного места на диске в базе данных **tempdb** , чтобы хранить запуски промежуточной сортировки, и достаточно места на диске в целевой файловой группе, чтобы хранить новый индекс. Выполнить инструкцию CREATE INDEX не удается, если свободное пространство недостаточно и по какой-то причине база данных не может автоматически задействовать дополнительное пространство, например нет места на диске или режим автоматического расширения отключен.  
  
 Если параметр SORT_IN_TEMPDB имеет значение OFF, то размер свободного места на диске для целевой файловой группы должен быть примерно равным размеру окончательного индекса. Во время первой фазы строятся операции сортировки, которым требуется примерно такое же пространство, как и окончательному индексу. Во время второй фазы каждый экстент сортировки освобождается после обработки. Это значит, что экстенты сортировки освобождаются примерно с такой же частотой, с которой экстенты задействуются для хранения страниц окончательного индекса; поэтому общие требования к пространству незначительно превышают размера окончательного индекса. Побочным эффектом того, что размер свободного пространства очень близок к размеру окончательного индекса, является то, что компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] , как правило, очень быстро повторно использует освобождаемые экстенты сортировки. Поскольку кластеры страниц сортировки освобождаются в произвольной манере, в результате увеличивается прерывистость экстентов индекса. Если значение параметра SORT_IN_TEMPDB равно OFF, то непрерывность экстентов индекса повышается при наличии свободного пространства для целевой файловой группы, которое можно выделить для экстентов индекса из непрерывного пула, а не из вновь освобожденных экстентов сортировки.  
  
При создании некластеризованного индекса необходимо иметь доступное свободное пространство:  
  
-   Если параметр SORT_IN_TEMPDB имеет значение ON, то в **tempdb** необходимо иметь свободное пространство, достаточное для хранения результатов операций сортировки, и свободное пространство в целевой файловой группе, достаточное для хранения структуры окончательного индекса. Результаты операций сортировки содержат конечные строки индекса;  
  
-   если параметр SORT_IN_TEMPDB имеет значение OFF, то свободное пространство целевой файловой группы должно быть достаточным для сохранения структуры окончательного индекса. При наличии большего объема свободного пространства может быть повышена степень непрерывности кластера страниц индекса.  
  
При создании кластеризованного индекса таблицы, которая не имеет некластеризованных индексов, необходимо иметь свободное пространство:  
  
-   Если параметр SORT_IN_TEMPDB имеет значение ON, то в **tempdb** должно быть достаточно свободного пространства для хранения результатов операций сортировки. К ним относятся строки данных таблицы. Необходимо свободное место на диске в целевой файловой группе, для хранения структуры окончательного индекса. К ней относятся строки данных таблицы и сбалансированное дерево индекса. Иногда приходится корректировать оценку с учетом таких факторов, как большой размер ключа или коэффициент заполнения с низким значением;  
  
-   если параметр SORT_IN_TEMPDB имеет значение OFF, с целью сохранения окончательной таблицы должно быть свободное пространство для целевой файловой группы. Это включает структуру индекса. При наличии большего объема свободного пространства может быть повышена степень непрерывности экстента таблицы и индекса.  
  
При создании кластеризованного индекса таблицы, которая имеет некластеризованные индексы, необходимо иметь свободное пространство:  
  
-   Если параметр SORT_IN_TEMPDB имеет значение ON, то свободное пространство **tempdb** должно быть достаточным для хранения коллекции операций сортировки для самого большого, обычно кластеризованного, индекса, а свободное пространство в целевой файловой группе должно быть достаточным для хранения окончательных структур всех индексов. Это включает кластеризованный индекс, который содержит строки данных таблицы;  
  
-   если параметр SORT_IN_TEMPDB имеет значение OFF, с целью сохранения окончательной таблицы должно быть свободное пространство для целевой файловой группы. Это включает структуры всех индексов. При наличии большего объема свободного пространства может быть повышена степень непрерывности экстента таблицы и индекса.  
  
## <a name="related-tasks"></a>Связанные задачи  
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)  
  
 [Реорганизация и перестроение индексов](../../relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
## <a name="related-content"></a>См. также  
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)  
  
 [Настройка параметра конфигурации сервера index create memory](../../database-engine/configure-windows/configure-the-index-create-memory-server-configuration-option.md)  
  
 [Disk Space Requirements for Index DDL Operations](../../relational-databases/indexes/disk-space-requirements-for-index-ddl-operations.md)  
  
  
