---
title: "サーバー接続ファイル (AccessToSQL) |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 08/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 829153be-aa8e-4162-87e8-69882feecf19
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 7d5bc198ae3082c1b79a3a64637662968b0748b2
ms.openlocfilehash: 7812e5ad1b6566a3ef477800d8098b23abacdd6a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="creating-the-server-connection-files-accesstosql"></a>接続ファイル (AccessToSQL) サーバーを作成します。
サーバーの情報は、スクリプト ファイルの [サーバー] セクションのいずれかを指定します。 サーバーの情報は、別のサーバー接続ファイルにも指定することができます。 サーバー接続ファイルのコマンド ライン パラメーターが`-c <serverconnectionfile>`です。 サーバーと同じ id がスクリプトとサーバーの両方の接続ファイルに存在する場合は、スクリプト ファイル内のサーバー定義と見なされます。  
  
```xml  
<!--Sample of server connection file commands -->  
<!--Connection to SQL Server-->  
  
<sql-server name="target_3">  
  
  <sql-server-authentication>  
  
    <server value="$TargetServerName$"/>  
  
    <database value="$TargetDB$"/>  
  
    <user-id value="$TargetUserName$"/>  
  
    <password value="$TargetPassword$"/>  
  
    <encrypt value="true"/>  
  
    <trust-server-certificate value="true"/>  
  
  </sql-server-authentication>  
  
</sql-server>  
```  
  
```xml  
<!--Connection to SQL Azure-->  
  
<sql-azure name="target_azure">  
  
  <server value="$TargetAzureServerName$"/>  
  
  <database value="$TargetAzureDB$"/>  
  
  <user-id value="$TargetAzureUserName$"/>  
  
  <password value="$TargetAzurePassword$"/>  
  
</sql-azure>  
```  
  
## <a name="server-connection-file-validation"></a>サーバー接続ファイルの検証  
ユーザーが、スキーマ定義ファイルに対する自分のサーバー接続ファイルを簡単に検証**'A2SSConsoleScriptServersSchema.xsd'** 'スキーマ' フォルダー内にあります。  
  
## <a name="next-step"></a>次の手順  
コンソールの運用には、次の手順は[SSMA コンソール &#40; を実行します。AccessToSQL &#41;](../../ssma/access/executing-the-ssma-console-accesstosql.md)  
  
## <a name="see-also"></a>参照  
[SSMA コンソール (アクセス) を実行します。](http://msdn.microsoft.com/aa1bf665-8dc0-4259-b36f-46ae67197a43)  
  
