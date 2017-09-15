---
title: "SQL Server 識別子のエスケープ | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a73e945-daa6-4e5d-93da-10f000f1f3a2
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: cf3199ee84469a62ebe0adac365034ab16e77503
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="escape-sql-server-identifiers"></a>SQL Server 識別子のエスケープ
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の区切れらた識別子には使用でき、Windows PowerShell パス名には使用できない文字をエスケープするためによく使用されるのが、Windows PowerShell のバック ティック エスケープ文字 (`) です。 ただし、エスケープできない文字もあります。 たとえば、Windows PowerShell ではコロン文字 (:) をエスケープできません。 この文字を含んだ識別子は、エンコードする必要があります。 エンコードは、すべての文字に有効であるため、エスケープよりも確実です。  
  
## <a name="before-you-begin"></a>はじめに  
 通常、バック ティック文字 (`) のキーは、キーボード左上の Esc キーの下にあります (英語キーボードの場合)。  
  
## <a name="examples"></a>使用例  
 次に示すのは、# 文字をエスケープする例です。  
  
```  
cd SQLSERVER:\SQL\MyComputer\MyInstance\MyDatabase\MySchema\`#MyTempTable  
```  
  
 次に示すのは、コンピューター名として (local) を指定する際に、かっこをエスケープする例です。  
  
```  
Set-Location SQLSERVER:\SQL\`(local`)\DEFAULT  
```  
  
## <a name="see-also"></a>参照  
 [PowerShell での SQL Server 識別子](../../relational-databases/scripting/sql-server-identifiers-in-powershell.md)   
 [SQL Server PowerShell プロバイダー](../../relational-databases/scripting/sql-server-powershell-provider.md)   
 [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  