---
title: Редактор задачи «Отправка почты» (страница «почта») | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.mail.f1
helpviewer_keywords:
- Send Mail Task Editor
ms.assetid: adb385d5-ef24-4d18-b9ea-b39e00a7075e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: d80ca8e475bf9c2b56c11118a44e5282573f280d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055830"
---
# <a name="send-mail-task-editor-mail-page"></a>Редактор задачи «Отправка почты» (страница «Почта»)
  Страница **Почта** диалогового окна **Редактор задачи «Отправка почты»** служит для определения получателей, типа и приоритета сообщения. К сообщению можно также прикрепить файлы. Текстом сообщения может быть введенная строка, соединение с файлом, содержащим текст, или имя переменной, содержащей текст.  
  
 Дополнительные сведения об этой задаче см. в разделе [Send Mail Task](control-flow/send-mail-task.md).  
  
## <a name="options"></a>Параметры  
 **SMTPConnection**  
 Выберите Диспетчер соединений SMTP в списке или нажмите кнопку ** \<создать соединение... >** , чтобы создать новый диспетчер соединений.  
  
> [!IMPORTANT]  
>  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
 **См. также:** [Диспетчер соединений SMTP](connection-manager/smtp-connection-manager.md)  
  
 **От**  
 Задайте адрес электронной почты отправителя.  
  
 **Кому**  
 Укажите адреса электронной почты получателей, разделенные точкой с запятой.  
  
 **Кому**  
 Задайте адреса электронной почты получателей, которые также получают копии сообщения. Разделяйте адреса точками с запятой.  
  
 **СК**  
 Задайте адреса электронной почты получателей, которые получают скрытые копии сообщения. Разделяйте адреса точками с запятой.  
  
 **Тема**  
 Укажите тему электронного сообщения.  
  
 **MessageSourceType**  
 Выберите тип источника сообщения. Это свойство имеет параметры, указанные в следующей таблице.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Прямой ввод**|Задание источника текста сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Соединение с файлом**|Задание в качестве источника файла, содержащего текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
|**Перемен**|В качестве источника указывается переменная, содержащая текст сообщения. При выборе этого значения отображается динамический параметр **MessageSource**.|  
  
 **Приоритеты**  
 Задается приоритет сообщения.  
  
 **Вло**  
 Укажите имена вложений для электронного сообщения, разделенные символом вертикальной черты (|).  
  
> [!NOTE]  
>  Длина строк «Кому», «Копия» и «СК» ограничена 256 символами в соответствии со стандартами Интернета.  
  
## <a name="messagesourcetype-dynamic-options"></a>Динамические параметры MessageSourceType  
  
### <a name="messagesourcetype--direct-input"></a>MessageSourceType = Прямой ввод  
 **MessageSource**  
 Введите текст сообщения или нажмите кнопку обзора (...), а затем введите сообщение в диалоговом окне **Источник сообщения**.  
  
### <a name="messagesourcetype--file-connection"></a>MessageSourceType = Соединение с файлом  
 **MessageSource**  
 Выберите Диспетчер подключения файлов в списке или нажмите кнопку \< **создать соединение...**>, чтобы создать новый диспетчер соединений.  
  
 **См. также:** [Диспетчер соединения файлов](connection-manager/file-connection-manager.md), [Редактор диспетчера подключения файлов](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="messagesourcetype--variable"></a>MessageSourceType = Переменная  
 **MessageSource**  
 Выберите переменную из списка или нажмите кнопку \< **создать переменную...**>, чтобы создать новую переменную.  
  
 **См. также:** [Integration Services &#40;переменные&#41; SSIS](integration-services-ssis-variables.md), [Добавить переменную](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи «Отправка почты» &#40;страница «Общие»&#41;](general-page-of-integration-services-designers-options.md)   
 [Страница «Выражения»](expressions/expressions-page.md)  
  
  
