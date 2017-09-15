---
title: "列の変更 (データベース エンジン) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 736b83dffa241040cf08e7f7d9410eaab80649af
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="modify-columns-database-engine"></a>列の変更 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ss2016-all_md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して列のデータ型を変更できます。  
  
> [!WARNING]  
>  既にデータが格納されている列のデータ型を変更すると、既存のデータが新しい型に変換される時点で、それらのデータは完全に失われます。 さらに、変更した列に依存しているコードやアプリケーションも正常に動作しなくなる場合があります。 これには、クエリ、ビュー、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。 このようなエラーは連鎖するので注意が必要です。 たとえば、変更した列に依存しているユーザー定義関数を呼び出すストアド プロシージャは、正常に動作しない可能性があります。 列に対して変更を行う場合は、よく考えてから行う必要があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [セキュリティ](#Security)  
  
-   **列のデータ型を変更する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> アクセス許可  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>列のデータ型を変更するには  
  
1.  **オブジェクト エクスプローラー**で、有効桁数を変更する列が含まれているテーブルを右クリックし、 **[デザイン]**をクリックします。  
  
2.  データ型を変更する列を選択します。  
  
3.  **[列のプロパティ]** タブで、 **[データ型]** プロパティのグリッド セルをクリックし、ドロップダウン リストから新しいデータ型を選択します。  
  
4.  **ファイル** メニューの **table name***の保存*をクリックします。  
  
> [!NOTE]  
>  列のデータ型を変更すると、テーブル デザイナーでは選択したデータ型の既定の長さが適用されます。これは既に別の長さを選択していた場合でも同じです。 データ型の指定後、必要な値を格納できるようにするために、データ型に適切な長さを設定してください。  
  
> [!WARNING]  
>  別のテーブルに関連付けられている列のデータ型を変更しようとすると、別のテーブルの列にも変更が行われることを確認するメッセージがテーブル デザイナーに表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>列のデータ型を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]**をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]**をクリックします。  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
  