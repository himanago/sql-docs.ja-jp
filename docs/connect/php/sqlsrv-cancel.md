---
title: "sqlsrv_cancel |Microsoft ドキュメント"
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
- sqlsrv_cancel
apitype: NA
helpviewer_keywords:
- sqlsrv_cancel
- API Reference, sqlsrv_cancel
ms.assetid: 75798c9b-f711-445d-9b8f-ba4d405ca50a
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1f69d5a11e4edd726479c48918f9a332f2279ed7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvcancel"></a>sqlsrv_cancel
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

ステートメントをキャンセルします。 これは、保留中のステートメントの結果を破棄することを意味します。 使用して準備された場合は、この関数が呼び出された後、ステートメントを再実行することができます[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)です。 ステートメントに関連付けられているすべての結果が消費されている場合、この関数を呼び出す必要はありません。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_cancel( resource $stmt)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$stmt*: 取り消されるステートメントです。  
  
## <a name="return-value"></a>戻り値  
ブール値: 操作が成功した場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="example"></a>例  
次の例では、 [AdventureWorks](http://go.microsoft.com/fwlink/?LinkID=67739) データベースを使用してクエリを実行し、変数 *$salesTotal* が、指定した値に達するまで結果を消費してカウントします。 残りのクエリ結果は破棄されます。 この例では、ローカル コンピューターに SQL Server および AdventureWorks データベースがインストールされていることを前提にしています。 コマンド ラインからこの例を実行すると、すべての出力はコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and   
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Prepare and execute the query. */  
$tsql = "SELECT OrderQty, UnitPrice FROM Sales.SalesOrderDetail";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in statement preparation.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
if( sqlsrv_execute( $stmt ) === false)  
{  
     echo "Error in statement execution.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Initialize tracking variables. */  
$salesTotal = 0;  
$count = 0;  
  
/* Count and display the number of sales that produce revenue  
of $100,000. */  
while( ($row = sqlsrv_fetch_array( $stmt)) && $salesTotal <=100000)  
{  
     $qty = $row[0];  
     $price = $row[1];  
     $salesTotal += ( $price * $qty);  
     $count++;  
}  
echo "$count sales accounted for the first $$salesTotal in revenue.\n";  
  
/* Cancel the pending results. The statement can be reused. */  
sqlsrv_cancel( $stmt);  
?>  
```  
  
## <a name="comments"></a>コメント  
準備ができたし、の組み合わせを使用して実行するステートメント[sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)と[sqlsrv_execute](../../connect/php/sqlsrv-execute.md)再実行することができます**sqlsrv_execute** を呼び出した後**sqlsrv_cancel**です。 実行すると、ステートメント[sqlsrv_query](../../connect/php/sqlsrv-query.md)呼び出した後に再実行することはできません**sqlsrv_cancel**です。  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  
[データの取得](../../connect/php/retrieving-data.md)  
[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
[sqlsrv_free_stmt](../../connect/php/sqlsrv-free-stmt.md)  
  
