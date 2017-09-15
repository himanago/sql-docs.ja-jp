---
title: "xp_cmdshell サーバー構成オプション | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- xp_cmdshell
ms.assetid: c147c9e1-b81d-49c8-b800-3019f4d86a13
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: b32eef170d0834b44932f753075bbd2df67762a2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="xpcmdshell-server-configuration-option"></a>xp_cmdshell サーバー構成オプション
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **xp_cmdshell** オプションは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] xp_cmdshell **拡張ストアド プロシージャをシステムで実行できるかどうかをシステム管理者が制御できるようにする、** のサーバー構成オプションです。 新しいインストールでは、 **xp_cmdshell** オプションは既定で無効になっており、ポリシー ベースの管理を使用するか、次のコード例のように **sp_configure** システム ストアド プロシージャを実行することで有効にできます。  
  
```  
-- To allow advanced options to be changed.  
EXEC sp_configure 'show advanced options', 1;  
GO  
-- To update the currently configured value for advanced options.  
RECONFIGURE;  
GO  
-- To enable the feature.  
EXEC sp_configure 'xp_cmdshell', 1;  
GO  
-- To update the currently configured value for this feature.  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [ポリシー ベースの管理を使用したサーバーの管理](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  
