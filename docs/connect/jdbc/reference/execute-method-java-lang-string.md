---
title: "execute (java.lang.String) メソッド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 219d4ff6ff793b244e30ca43582f4d194e7e6a5d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="execute-method-javalangstring"></a>execute (java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された SQL ステートメントを実行します。このステートメントは、複数の結果を返す場合があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *sql*  
  
 A**文字列**SQL ステートメントを含むです。  
  
## <a name="return-value"></a>戻り値  
 **true**場合は、ステートメントが結果セットを返します。 **false**場合は、更新数か、何の結果を返します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この execute メソッドは、java.sql.Statement インターフェイスの execute メソッドによって指定されます。  
  
 このメソッドは、[実行](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)メソッド内にある、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。  
  
 オブジェクトが作成されるとき、SQLServerPreparedStatement オブジェクトの SQL ステートメントが指定されてためこのメソッドを呼び出すが、例外が発生します。  
  
## <a name="see-also"></a>参照  
 [方法 &#40; を実行します。SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement のメンバー](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement クラス](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  