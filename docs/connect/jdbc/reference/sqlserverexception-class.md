---
title: "SQLServerException クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af5ef257-7cf6-4db3-b1ee-07d22d82bef1
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd894bf23d8b1643722691451ccf3ae29ec6cd54
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverexception-class"></a>SQLServerException クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  SQL ステートメントの実行に失敗したこと、または実行が完了しなかったことを表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **拡張:** java.sql.SQLException  
  
 **実装:** java.io.Serializable  
  
## <a name="syntax"></a>構文  
  
```  
  
public final class SQLServerException  
```  
  
## <a name="remarks"></a>解説  
 SQLServerException クラスでは、SQL 92 と XOPEN の両方の状態コードを処理します。 これらは、ユーザー指定の接続プロパティを使用して切り替えることができます。 例外は、開いている指定のログ ファイルに書き込まれます。  
  
## <a name="see-also"></a>参照  
 [SQLServerException のメンバー](../../../connect/jdbc/reference/sqlserverexception-members.md)   
 [JDBC ドライバー API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  