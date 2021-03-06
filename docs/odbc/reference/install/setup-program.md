---
title: Программа установки | Документация Майкрософт
ms.custom: ''
ms.date: 08/31/2016
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
ms.assetid: 9cc5d75d-b293-41e5-927c-10f4af2e7af1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dc79bb5d12b53938e3e2ef1c531fd03b0002ed78
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68093836"
---
# <a name="setup-program"></a>Программа установки
> **Примечание.** Начиная с Windows XP и Windows Server 2003, **ODBC входит в операционную систему Windows**. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Пользователь запускает программу установки для запуска процесса установки. Программа установки написана разработчиком приложения или драйвера. В дополнение к установке компонентов ODBC можно установить другое программное обеспечение. Например, разработчики приложений могут использовать одну и ту же программу установки для установки компонентов ODBC и установки приложений.  
  
 Разработчики могут написать программу установки с нуля, используя служебные программы установки пакета Microsoft® Windows® SDK или программу установки программного обеспечения от других поставщиков. Это дает разработчикам полный контроль над внешним видом и поведением программы установки. Программа установки может быть написана для установки дополнительного программного обеспечения, например приложения ODBC. Дополнительные сведения о программах установки Windows SDK см. в документации по Windows SDK.  
  
 Объем установки, фактически выполняемый программой установки, зависит от того, какие функции она вызывает в библиотеке DLL установщика. Библиотека DLL установщика содержит функции для установки отдельных компонентов ODBC. Программа установки просто вызывает **склинсталлдриверманажер**, **склинсталлдриверекс**или **склинсталлтранслаторекс** в библиотеке DLL установщика для получения пути к каталогу, в котором должен быть установлен компонент, а также для добавления сведений о компоненте в реестр. Эти функции фактически не копируют файлы. Программа установки выполняет это с помощью сведений в аргументах этих функций.  
  
 Библиотека DLL установщика также содержит функции для удаления компонентов ODBC. Программа установки вызывает **склремоведриверманажер**, **склремоведривер**или **склремоветранслатор** в библиотеке DLL установщика для уменьшения числа использований компонента в реестре и, если счетчик использования нового компонента падает до 0, удалите все сведения о компоненте из реестра. Эти функции фактически не удаляют файлы для компонента. Программа установки делает это, если число новых использований становится равным 0.
