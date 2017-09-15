---
title: "データベース ミラーリング セッションでのトランザクションの安全性の変更 (Transact-SQL) | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction safety [SQL Server database mirroring]
ms.assetid: 8b03bb82-8589-4558-8545-9942fe008391
caps.latest.revision: 38
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 9cf22d160c37c4d8904830d363e6358cb5b40aea
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="change-transaction-safety-in-a-database-mirroring-session-transact-sql"></a>データベース ミラーリング セッションでのトランザクションの安全性の変更 (Transact-SQL)
  トランザクションの安全性は、セッションの動作モードを制御する属性です。 ただし、データベース所有者は、いつでもトランザクションの安全性を変更できます。 既定では、トランザクションの安全性レベルは FULL (同期動作モード) に設定されています。  
  
 トランザクションの安全性を無効にすると、セッションの動作モードが、パフォーマンスを最適にする非同期動作モードに切り替わります。 プリンシパル サーバーを使用できなくなるとミラー サーバーは停止しますが、ミラー サーバーをウォーム スタンバイ サーバーとして使用することができます (フェールオーバーにはサービスの強制が必要ですが、データを損失する可能性があります)。  
  
### <a name="to-turn-on-transaction-safety"></a>トランザクションの安全性を有効にするには  
  
1.  プリンシパル サーバーに接続します。  
  
2.  次の Transact-SQL ステートメントを実行します。  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY FULL  
    ```  
  
     *\<database>* はミラー化されたデータベースの名前です。  
  
### <a name="to-turn-off-transaction-safety"></a>トランザクションの安全性を無効にするには  
  
1.  プリンシパル サーバーに接続します。  
  
2.  次のステートメントを実行します。  
  
    ```  
    ALTER DATABASE <database> SET PARTNER SAFETY OFF  
    ```  
  
     *\<database>* はミラー化されたデータベースです。  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  