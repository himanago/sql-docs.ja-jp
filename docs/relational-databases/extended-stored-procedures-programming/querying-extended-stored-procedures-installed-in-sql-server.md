---
title: クエリを実行する SQL Server にインストールされているストアド プロシージャを拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: f2d5584d70b32764fd9c7e11a53131626e9df444
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814300"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a>SQL Server にインストールされた拡張ストアド プロシージャの照会
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]拡張ストアド プロシージャを現在定義されている表示ユーザーを認証しを実行している各 DLL の名前が属している、 **sp_helpextendedproc**システム プロシージャ。 たとえば、次の例が DLL を返しますを**xp_hello**が属しています。  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 場合**sp_helpextendedproc**拡張ストアド プロシージャをすべての拡張ストアド プロシージャの Dll が表示されるかを指定せずに実行されます。  
  
> [!IMPORTANT]  
>  ログインしたユーザーが所有しているか、権限を持っている拡張ストアド プロシージャの情報だけが返されます。 メンバーのみ、 **sysadmin**固定サーバー ロールおよび**db_owner**、 **db_securityadmin**、および**db_ddladmin**固定データベースロールは、すべての拡張ストアド プロシージャの情報を表示できます。  
  
## <a name="see-also"></a>参照  
 [sp_helpextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql.md)   
 [sp_addextendedproc &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql.md)   
 [sp_dropextendedproc &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql.md)  
  
  
