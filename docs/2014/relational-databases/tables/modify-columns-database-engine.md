---
title: 列の変更 (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- modifying data types
- column data types [SQL Server]
- data types [SQL Server], columns
ms.assetid: b67b95c5-61ef-4bd8-9a3e-1640eb7583ac
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4d98b8de8e4ced15291684ba304bfd04c6c62b7c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48161162"
---
# <a name="modify-columns-database-engine"></a>列の変更 (データベース エンジン)
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して列のデータ型を変更できます。  
  
> [!WARNING]  
>  既にデータが格納されている列のデータ型を変更すると、既存のデータが新しい型に変換される時点で、それらのデータは完全に失われます。 さらに、変更した列に依存しているコードやアプリケーションも正常に動作しなくなる場合があります。 これには、クエリ、ビュー、ストアド プロシージャ、ユーザー定義関数、およびクライアント アプリケーションが含まれます。 このようなエラーは連鎖するので注意が必要です。 たとえば、変更した列に依存しているユーザー定義関数を呼び出すストアド プロシージャは、正常に動作しない可能性があります。 列に対して変更を行う場合は、よく考えてから行う必要があります。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **列のデータ型を変更する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>列のデータ型を変更するには  
  
1.  **オブジェクト エクスプローラー**で、有効桁数を変更する列が含まれているテーブルを右クリックし、 **[デザイン]** をクリックします。  
  
2.  データ型を変更する列を選択します。  
  
3.  **[列のプロパティ]** タブで、 **[データ型]** プロパティのグリッド セルをクリックし、ドロップダウン リストから新しいデータ型を選択します。  
  
4.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
> [!NOTE]  
>  列のデータ型を変更すると、テーブル デザイナーでは選択したデータ型の既定の長さが適用されます。これは既に別の長さを選択していた場合でも同じです。 データ型の指定後、必要な値を格納できるようにするために、データ型に適切な長さを設定してください。  
  
> [!WARNING]  
>  別のテーブルに関連付けられている列のデータ型を変更しようとすると、別のテーブルの列にも変更が行われることを確認するメッセージがテーブル デザイナーに表示されます。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-modify-the-data-type-of-a-column"></a>列のデータ型を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    CREATE TABLE dbo.doc_exy (column_a INT ) ;  
    GO  
    INSERT INTO dbo.doc_exy (column_a) VALUES (10) ;  
    GO  
    ALTER TABLE dbo.doc_exy ALTER COLUMN column_a DECIMAL (5, 2) ;  
    GO  
  
    ```  
  
 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。  
  
  
