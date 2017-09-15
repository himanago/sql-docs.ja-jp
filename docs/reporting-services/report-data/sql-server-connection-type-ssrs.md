---
title: "SQL Server 接続の種類 (SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 957e7091-e08f-48d2-9506-872227ae8b20
caps.latest.revision: 9
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 32279a0b5ded6db08e5d3156474e0c646e15b969
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="sql-server-connection-type-ssrs"></a>SQL Server の接続の種類 (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのデータをレポートに含めるには、種類が [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のレポート データ ソースに基づいたデータセットが必要です。 このビルトイン データ ソースの種類は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ拡張機能に基づいています。 現在のバージョンと以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続してデータを取得するには、このデータ ソースの種類を使用します。  
  
 このデータ拡張機能は、複数の値を持つパラメーター、サーバー集計、および接続文字列とは別に管理される資格情報をサポートしています。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、「 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="Connection"></a> 接続文字列  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続する場合は、サーバー上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータベース オブジェクトに接続します。 データベースには、複数のテーブル、ビュー、およびストアド プロシージャを含むスキーマが複数存在している場合があります。 クエリ デザイナーで、使用するデータベース オブジェクトを指定します。 接続文字列でデータベースを指定しない場合は、データベース管理者によって割り当てられた既定のデータベースに接続されます。  
  
 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 ローカル クライアント上のサンプル データベースを指定する接続文字列の例を次に示します。  
  
```  
Data Source=<server>;Initial Catalog=AdventureWorks  
```  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 クエリの実行、ローカルでのレポートのプレビュー、およびレポート サーバーからのレポートのプレビューには、資格情報が必要です。  
  
 レポートをパブリッシュした後、レポートをレポート サーバーで実行するときに、データを取得するための権限が有効な状態になるように、データ ソースの資格情報を変更する必要が生じる場合があります。  
  
 レポート作成クライアントから、次のオプションを使用して資格情報を指定します。  
  
-   現在の Windows ユーザー (統合セキュリティとも呼ばれます)。  
  
-   保存されているユーザー名とパスワードを使用する。  
  
-   ユーザーに資格情報を要求する。 このオプションでは Windows 統合セキュリティのみがサポートされます。  
  
-   資格情報を必要としない。 このオプションを使用するには、レポート サーバーで自動実行アカウントを構成しておく必要があります。 詳細については、msdn.microsoft.com の [Reporting Services に関するドキュメント](http://go.microsoft.com/fwlink/?linkid=121312)の「[自動実行アカウントの構成 (SSRS 構成マネージャー)](../../reporting-services/install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。  
  
 詳しくは、「[データ接続、データ ソース、および接続文字列 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-data/data-connections-data-sources-and-connection-strings-report-builder-and-ssrs.md)」または「[レポート ビルダーでの資格情報の指定](http://msdn.microsoft.com/library/7412ce68-aece-41c0-8c37-76a0e54b6b53)」を参照してください。  
  
  
##  <a name="Query"></a> クエリ  
 クエリでは、レポート データセット用に取得するデータを指定します。 クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。 レポートによって処理されるのは、クエリから取得された最初の結果セットだけです。  
  
 新しいクエリを作成するか、グラフィカル クエリ デザイナーで表示できる既存のクエリを開く場合、既定でリレーショナル クエリ デザイナーを使用できます。 クエリは、次の方法で指定できます。  
  
-   クエリを対話形式で作成します。 データベース スキーマ別に編成された、テーブル、ビュー、ストアド プロシージャ、およびその他のデータベース アイテムの階層ビューが表示されるリレーショナル クエリ デザイナーを使用します。 テーブルまたはビューから列を選択するか、ストアド プロシージャまたはテーブル値関数を指定します。 フィルター条件を指定して、取得するデータの行数を制限します。 パラメーター オプションを設定してレポートの実行時にフィルターをカスタマイズします。  
  
-   クエリを入力するか、貼り付けます。 テキスト ベースのクエリ デザイナーは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] テキストを直接入力する、クエリ テキストを別のソースから貼り付ける、リレーショナル クエリ デザイナーでは作成できない複雑なクエリを入力する、クエリ ベースの式を入力する、などの場合に使用します。  
  
-   ファイルまたはレポートから既存のクエリをインポートします。 クエリ デザイナーのクエリの **[インポート]** ボタンを使用して、.sql ファイルまたは .rdl ファイルを参照し、クエリをインポートします。  
  
 詳細については、「[リレーショナル クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../../reporting-services/report-data/relational-query-designer-user-interface-report-builder.md)」および「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](../../reporting-services/report-data/text-based-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 次のクエリ モードがサポートされています。  
  
-   [Text](#QueryText) [!INCLUDE[tsql](../../includes/tsql-md.md)] のコマンドを入力します。  
  
-   [StoredProcedure](#QueryStoredProcedure) ストアド プロシージャの一覧から選択します。  
  
###  <a name="QueryText"></a> Text の種類のクエリの使用  
 テキスト ベースのクエリ デザイナーでは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを入力して、データセット内のデータを定義できます。 たとえば、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] クエリでは、マーケティング アシスタントであるすべての従業員の名前を選択します。  
  
```  
SELECT  
  HumanResources.Employee.BusinessEntityID  
  ,HumanResources.Employee.JobTitle  
  ,Person.Person.FirstName  
  ,Person.Person.LastName  
FROM  
  Person.Person  
  INNER JOIN HumanResources.Employee  
    ON Person.Person.BusinessEntityID = HumanResources.Employee.BusinessEntityID  
WHERE HumanResources.Employee.JobTitle = 'Marketing Assistant'   
```  
  
 ツール バーの **[実行]** ボタン (**!**) をクリックすると、クエリが実行され、結果セットが表示されます。  
  
 このクエリをパラメーター化するには、クエリ パラメーターを追加します。 たとえば、WHERE 句を次の構文に変更します。  
  
 `WHERE HumanResources.Employee.JobTitle = (@JobTitle)`  
  
 クエリの実行時に、クエリ パラメーターに対応するレポート パラメーターが自動的に作成されます。 詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。  
  
  
###  <a name="QueryStoredProcedure"></a> StoredProcedure の種類のクエリの使用  
 データセット クエリのストアド プロシージャは、次のいずれかの方法で指定できます。  
  
-   **[データセットのプロパティ]** ダイアログ ボックスで、 **[ストアド プロシージャ]** オプションを設定します。 ドロップダウン リストからストアド プロシージャまたはテーブル値関数を選択します。  
  
-   リレーショナル クエリ デザイナーのデータベース ビュー ペインで、ストアド プロシージャまたはテーブル値関数を選択します。  
  
-   テキスト ベースのクエリ デザイナーで、ツール バーから **[StoredProcedure]** を選択します。  
  
 ストアド プロシージャまたはテーブル値関数を選択したら、クエリを実行できます。 入力パラメーター値の入力を要求されます。 クエリの実行時に、入力パラメーターに対応するレポート パラメーターが自動的に作成されます。 詳細については、このトピックの「 [クエリ パラメーター](#Parameters) 」を参照してください。  
  
 ストアド プロシージャから取得した最初の結果セットだけがサポートされます。 ストアド プロシージャから複数の結果セットが返された場合、最初の結果セットだけが使用されます。  
  
 既定値が指定されたパラメーターがストアド プロシージャに含まれている場合、パラメーターの値として DEFAULT キーワードを使用してその値にアクセスできます。 クエリ パラメーターがレポート パラメーターにリンクされている場合は、レポート パラメーターの入力ボックスで DEFAULT キーワードを入力または選択できます。  
  
 詳細については、msdn.microsoft.com にある [SQL Server オンライン ブック](http://go.microsoft.com/fwlink/?linkid=98335) の「ストアド プロシージャ (データベース エンジン)」を参照してください。  
  
  
##  <a name="Parameters"></a> パラメーター  
 入力パラメーターを含むクエリ変数またはストアド プロシージャがクエリ テキストに含まれている場合、対応するデータセットのクエリ パラメーターとレポートのレポート パラメーターが自動的に生成されます。 クエリ テキストには、各クエリ変数の DECLARE ステートメントを含めないでください。  
  
 たとえば、次の SQL クエリでは、 **EmpID**という名前のレポート パラメーターが作成されます。  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 レポート パラメーターは、既定のプロパティ値を使用して作成されます。この既定のプロパティ値は、変更が必要になることがあります。 例:  
  
-   各レポート パラメーターの既定のデータ型は **Text**です。 基になるデータのデータ型が異なる場合は、パラメーターのデータ型を変更する必要があります。  
  
-   複数値パラメーターのオプションを選択した場合は、クエリを手動で変更し、 **IN** 演算子を使用して値がセットの一部かどうかをテストする必要があります ( `WHERE EmployeeID IN (@EmpID)`など)。  
  
 詳細については、msdn.microsoft.com の [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)のレポート データ ソースに基づいたデータセットが必要です。  
  
  
##  <a name="Remarks"></a> 解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースからのデータの取得は、OLE DB または ODBC のデータ ソースの種類を使用して行うこともできます。 詳細については、「[OLE DB の接続の種類 &#40;SSRS&#41;](../../reporting-services/report-data/ole-db-connection-type-ssrs.md)」または「[ODBC の接続の種類 &#40;SSRS&#41;](../../reporting-services/report-data/odbc-connection-type-ssrs.md)」を参照してください。  
  
###### <a name="platform-and-version-information"></a>プラットフォームおよびバージョン情報  
 プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md)」を参照してください。  
  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続を追加および確認する (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](../../reporting-services/report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットと &#40; にフィルターを追加します。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義しカスタマイズし使用する手順が説明されています。  
  
 [レポート データセット &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [データ接続、データ ソース、およびレポート ビルダーでの接続文字列](http://msdn.microsoft.com/library/7e103637-4371-43d7-821c-d269c2cc1b34)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットおよび共有データセット &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクションと &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース (SSRS)](../../reporting-services/report-data/data-sources-supported-by-reporting-services-ssrs.md) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312)の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ドキュメント)  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
  
## <a name="see-also"></a>参照  
 [レポート パラメーターと &#40; です。レポート ビルダーおよびレポート デザイナーと &#41; です。](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md)   
 [フィルター、グループ、およびデータを並べ替える &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式と &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)  
  
  