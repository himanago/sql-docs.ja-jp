---
title: "SQL Server: User Settable オブジェクト | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- User Settable object
- SQLServer:User Settable
ms.assetid: 633de3ef-533c-4f0c-9c7b-c105129d8e94
caps.latest.revision: 22
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0852dd58d7b89a9cf222c234a18bcecbad1cd943
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="sql-server-user-settable-object"></a>SQL Server: User Settable オブジェクト
  Microsoft **の** User Settable [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトを使用すると、カスタムのカウンター インスタンスを作成できます。 カスタムのカウンター インスタンスは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのユーザー独自のコンポーネントなど、既存のカウンターでは監視されないサーバーの特性を監視するために使用します。たとえば、ログに記録された顧客注文数や製品在庫数などを監視できます。  
  
 **User Settable** オブジェクトには、 **ユーザー カウンター 1** から **ユーザー カウンター 10**まで、クエリ カウンターの 10 個のインスタンスが含まれています。 これらのカウンターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sp_user_counter1 **から** sp_user_counter10 **までの**ストアド プロシージャに対応します。 ユーザー アプリケーションからこれらのストアド プロシージャが実行されると、ストアド プロシージャによって設定された値がシステム モニターに表示されます。 1 つのカウンターは、1 日に発生した特定製品の注文件数を数えるストアド プロシージャなど、任意の整数値を 1 つ監視できます。  
  
> [!NOTE]  
>  ユーザー カウンターのストアド プロシージャは、システム モニターから自動的にポーリングされることはありません。 カウンター値を更新するには、ユーザー アプリケーションから明示的にストアド プロシージャを実行する必要があります。 カウンター値を自動的に更新するには、トリガーを使用します。 たとえば、テーブルの行数を監視するカウンターを作成するには、テーブルに対する INSERT と DELETE のトリガーを作成し、 `SELECT COUNT(*) FROM table`というステートメントが実行されるようにします。 テーブルに対する INSERT 操作か DELETE 操作が発生するとトリガーが起動され、システム モニター カウンターが自動的に更新されます。  
  
 次の表では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **User Settable** object.  
  
|SQL Server User Settable カウンター|説明|  
|---------------------------------------|-----------------|  
|**Query**|**User Settable** オブジェクトには、Query カウンターが含まれています。 ユーザーは、クエリ オブジェクト内の **ユーザー カウンター** を構成します。|  
  
 次の表では、 **Query** カウンターの **インスタンス** について説明します。  
  
|Query カウンターのインスタンス|説明|  
|-----------------------------|-----------------|  
|**ユーザー カウンター 1**|**sp_user_counter1**を使用して定義します。|  
|**ユーザー カウンター 2**|**sp_user_counter2**を使用して定義します。|  
|**ユーザー カウンター 3**|**sp_user_counter3**を使用して定義します。|  
|…||  
|**ユーザー カウンター 10**|**sp_user_counter10**を使用して定義します。|  
  
 ユーザー カウンターのストアド プロシージャを使用するには、カウンターの新しい値を示す 1 つの整数パラメーターを指定して、独自のアプリケーションからそのストアド プロシージャを実行します。 たとえば、 **ユーザー カウンター 1** の値を 10 に設定するには、次の Transact-SQL ステートメントを実行します。  
  
```  
EXECUTE sp_user_counter1 10  
```  
  
 ユーザー カウンターのストアド プロシージャは、独自のストアド プロシージャなど他のストアド プロシージャを呼び出せる場所なら、どこからでも呼び出すことができます。 たとえば、次のストアド プロシージャを作成して、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されてから行われた接続と接続試行の数を数えることができます。  
  
```  
DROP PROC My_Proc  
GO  
CREATE PROC My_Proc  
AS   
   EXECUTE sp_user_counter1 @@CONNECTIONS  
GO  
```  
  
 @@CONNECTIONS 関数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが起動されてから行われた接続または接続試行の数を返します。 返された値が、パラメーターとして **sp_user_counter1** ストアド プロシージャに渡されます。  
  
> [!IMPORTANT]  
>  ユーザー カウンターのストアド プロシージャで定義するクエリは、できるだけ単純なものにしてください。 大量の並べ替え操作やハッシュ操作を実行するクエリや大量の I/O を実行するクエリは、メモリを集中的に消費するので、パフォーマンスに影響する可能性があります。  
  
## <a name="permissions"></a>権限  
 **sp_user_counter** はすべてのユーザーが使用できますが、任意のクエリ カウンターに制限することもできます。  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  