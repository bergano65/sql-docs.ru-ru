---
title: DROP SECURITY POLICY (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_SECURITY_POLICY_TSQL
- DROP SECURITY POLICY
- DROP SECURITY
- DROP_SECURITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DROP SECURITY POLICY statement
ms.assetid: 5bd3393d-2fa5-4db0-a69a-a1a72d638e9d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 33b04fb6e1db0afa87ecde24e28dd28772d6c3a9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68070279"
---
# <a name="drop-security-policy-transact-sql"></a>DROP SECURITY POLICY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  Удаляет политику безопасности.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
DROP SECURITY POLICY [ IF EXISTS ] [schema_name. ] security_policy_name    
[;]  
```  
  
## <a name="arguments"></a>Аргументы  
 *IF EXISTS*  
 **Применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] до [текущей версии](https://go.microsoft.com/fwlink/p/?LinkId=299658)).  
  
 Условное удаление политики безопасности только в том случае, если она уже существует.  
  
 *schema_name*  
 Имя схемы, которой принадлежит политика безопасности.  
  
 *security_policy_name*  
 Имя политики безопасности. Имена политик безопасности должны удовлетворять правилам построения идентификаторов и должны быть уникальными в пределах базы данных и схемы.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение ALTER ANY SECURITY POLICY и разрешение ALTER в схеме.  
  
## <a name="example"></a>Пример  
  
```  
DROP SECURITY POLICY secPolicy;  
```  
  
## <a name="see-also"></a>См. также:  
 [Безопасность на уровне строк](../../relational-databases/security/row-level-security.md)   
 [CREATE SECURITY POLICY (Transact-SQL)](../../t-sql/statements/create-security-policy-transact-sql.md)   
 [ALTER SECURITY POLICY (Transact-SQL)](../../t-sql/statements/alter-security-policy-transact-sql.md)   
 [sys.security_policies (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-policies-transact-sql.md)   
 [sys.security_predicates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-security-predicates-transact-sql.md)  
  
  
