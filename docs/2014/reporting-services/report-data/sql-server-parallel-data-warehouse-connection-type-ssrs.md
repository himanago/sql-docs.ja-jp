---
title: SQL Server 並列データ ウェアハウスの接続の種類 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3925fd3d-2aa1-4768-96ad-cfc2c0ba9283
caps.latest.revision: 10
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 6b1b12938e2043ee126c81313fc955454742bcde
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149413"
---
# <a name="sql-server-parallel-data-warehouse-connection-type-ssrs"></a>SQL Server 並列データ ウェアハウスの接続の種類 (SSRS)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] 超並列処理によってパフォーマンスとスケーラビリティを提供するスケーラブルなデータ ウェアハウス アプライアンスです。 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] 使用して[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]分散処理とデータ ストレージ用のデータベース。  
  
 このアプライアンスでは、複数の物理ノードにわたる大規模なデータベース テーブルを分割し、各ノードが独自の [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を実行するようにします。 レポートが [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] に接続してレポート データを取得するときには、クエリの処理を管理する、 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] アプライアンス内の管理ノードに接続します。 接続が確立すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 環境内にある [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] のインスタンスに対する操作と、この環境外にある  のインスタンスに対する操作の区別が付かなくなります。  
  
 データを含めるに[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]レポートでは、型のレポート データ ソースに基づいているデータセットが必要[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Parallel Data Warehouse。 このビルトイン データ ソースの種類がに基づいて、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Parallel Data Warehouse のデータ拡張機能。 このデータ ソースの種類を使用して、[!INCLUDE[ssDW](../../../includes/ssdw-md.md)] からのデータに接続し、そのデータを取得します。  
  
 このデータ拡張機能は、接続文字列とは個別に管理される、複数の値を持つパラメーター、サーバー集計、および資格情報をサポートしています。  
  
 詳細については、「 [SQL Server 2008 R2 並列データ ウェアハウス](http://go.microsoft.com/fwlink/?LinkId=150895)」の Web サイトを参照してください。  
  
 このトピックの情報を使用して、データ ソースを構築してください。 手順については、次を参照してください。[データ接続またはデータ ソース追加および確認&#40;レポート ビルダーおよび SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)します。  
  
##  <a name="Connection"></a> 接続文字列  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)]に接続する場合、 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] アプライアンス内のデータベース オブジェクトに接続します。 クエリ デザイナーで、使用するデータベース オブジェクトを指定します。 接続文字列でデータベースを指定しない場合は、管理者によって割り当てられた既定のデータベースに接続されます。 データ ソースへの接続に使用する接続情報および資格情報については、データベース管理者に問い合わせてください。 次の接続文字列の例は、サンプル データベースを指定**CustomerSales**の[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]アプライアンス。  
  
```  
HOST=<IP address>; database= CustomerSales; port=<port>  
```  
  
 また、 **[データ ソースのプロパティ]** ダイアログ ボックスを使用して、ユーザー名やパスワードなどの資格情報を入力します。 `User Id` オプションと `Password` オプションは、接続文字列に自動的に付加されます。これらを接続文字列の一部として入力する必要はありません。 ユーザー インターフェイスは、内の管理ノードの IP アドレスを指定するオプションも用意されています。、[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]アプライアンスとポート番号。 既定のポート番号は 17000 です。 ポートは管理者が変更できるので、接続文字列で別のポート番号を使用することもあります。  
  
 接続文字列の例の詳細については、「 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)」を参照してください。  
  
##  <a name="Credentials"></a> [資格情報]  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] には、ユーザー名とパスワードを実装および保存するための独自のセキュリティ技術が用意されています。 Windows 認証は使用できません。 Windows 認証を使用して [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] に接続しようとすると、エラーが発生します。  
  
 データベースにアクセスするには、十分な資格情報が必要です。 クエリによっては、他の権限 (テーブルやビューにアクセスするために必要な権限など) が必要な場合があります。 外部データ ソースの所有者は、十分な資格情報を構成して、ユーザーが必要とするデータベース オブジェクトに対する読み取り専用アクセスを提供する必要があります。  
  
 レポート作成クライアントから、次のオプションを使用して資格情報を指定します。  
  
-   保存されているユーザー名とパスワードを使用する。 レポート データを格納するデータベースがレポート サーバーとは別のサーバーに存在する場合に発生するダブル ホップに対処するには、資格情報を Windows 資格情報として使用するオプションを選択します。 データ ソースに接続した後に、認証されているユーザーの権限を借用するオプションもあります。  
  
-   資格情報を必要としない。 このオプションを使用するには、レポート サーバーで自動実行アカウントを構成しておく必要があります。 詳細については、msdn.microsoft.com で [Reporting Services に関するドキュメント](http://go.microsoft.com/fwlink/?linkid=121312)の「[自動実行アカウントの構成 &#40;SSRS 構成マネージャー&#41;](../install-windows/configure-the-unattended-execution-account-ssrs-configuration-manager.md)」を参照してください。  
  
 詳細については、次を参照してください。[データ接続、データ ソース、および Reporting Services の接続文字列](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)または[レポート ビルダーでの資格情報の指定](../specify-credentials-in-report-builder.md)します。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Query"></a> クエリ  
 クエリでは、レポート データセット用に取得するデータを指定します。  
  
 クエリの結果セットの列には、データセットのフィールド コレクションが設定されます。 クエリで複数の結果セットが返された場合にレポートによって処理されるのは、クエリから取得された最初の結果セットだけです。 新しいクエリを作成するか、グラフィカル クエリ デザイナーで表示できる既存のクエリを開く場合、既定でリレーショナル クエリ デザイナーを使用できます。 クエリは、次の方法で指定できます。  
  
-   クエリを対話形式で作成します。 データベース スキーマ別に編成された、テーブル、ビュー、およびその他のデータベース アイテムの階層ビューが表示されるリレーショナル クエリ デザイナーを使用します。 テーブルまたはビューから列を選択します。 フィルター条件、グループ化、および集計を指定して、取得するデータの行数を制限します。 パラメーター オプションを設定してレポートの実行時にフィルターをカスタマイズします。  
  
-   クエリを入力するか、貼り付けます。 テキスト ベースのクエリ デザイナーを使用して入力[!INCLUDE[DWsql](../../../includes/dwsql-md.md)]を貼り付ける、リレーショナル クエリ デザイナーを使用して作成できない複雑なクエリを入力するか、クエリ ベースの式を入力する別のソースからクエリ テキストを直接テキスト。  
  
-   ファイルまたはレポートから既存のクエリをインポートします。 クエリ デザイナーの **[クエリのインポート]** ボタンを使用して、.sql ファイルまたは .rdl ファイルを参照し、クエリをインポートします。  
  
 詳細については、「[リレーショナル クエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](relational-query-designer-user-interface-report-builder.md)」および「[テキストベースのクエリ デザイナーのユーザー インターフェイス &#40;レポート ビルダー&#41;](text-based-query-designer-user-interface-report-builder.md)」を参照してください。  
  
 テキスト ベースのクエリ デザイナーでは、[Text](#QueryText) モードをサポートしています。このモードで、データ ソースからデータを選択する [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] コマンドを入力します。  
  
-   [Text](#QueryText)  
  
 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] では [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] を使用し、 [!INCLUDE[tsql](../../../includes/tsql-md.md)] では [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を使用します。 SQL 言語のこの 2 つの言語仕様はよく似ています。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ ソースの接続の種類に対して作成されたクエリは、通常、[!INCLUDE[ssDWCurrentFull](../../../includes/ssdwcurrentfull-md.md)] データ ソースの接続の種類に使用できます。  
  
 大規模なデータベース ([!INCLUDE[ssDW](../../../includes/ssdw-md.md)] などのデータ ウェアハウスを含む) からレポート データを取得するクエリでは、データを集計および集約してクエリから返される行数を減らさない限り、行数の非常に多い結果セットが生成されることがあります。 集計やグループ化を含むクエリは、グラフィカルまたはテキストベースのクエリ デザイナーを使用して作成できます。  
  
 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] データを集計するクエリ デザイナーを提供する句、キーワード、および集計をサポートします。  
  
 [!INCLUDE[ssDW](../../../includes/ssdw-md.md)] で使用されるグラフィカル クエリ デザイナーには、要約データのみを取得するクエリの作成に役立つグループ化と集計のサポートが組み込まれています。 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)]言語機能は、: GROUP BY 句、DISTINCT キーワード、および SUM や COUNT などの集計。 テキスト ベースのクエリ デザイナーには、完全にサポートが用意されています、 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] 、グループ化と集計を含む言語。  
  
 [!INCLUDE[tsql](../../../includes/tsql-md.md)] の詳細については、msdn.microsoft.com の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?LinkId=141687)にある「[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference)」を参照してください。  
  
###  <a name="QueryText"></a> Text の種類のクエリの使用  
 テキスト ベースのクエリ デザイナーでは、 [!INCLUDE[DWsql](../../../includes/dwsql-md.md)] コマンドを入力して、データセット内のデータを定義します。 クエリからデータを取得するために使用[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]はのインスタンスからデータを取得するを使用するものと同じ[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]内で実行されていない、[!INCLUDE[ssDW](../../../includes/ssdw-md.md)]アプリケーション。 たとえば、次[!INCLUDE[DWsql](../../../includes/dwsql-md.md)]クエリは、マーケティング アシスタントであるすべての従業員の名前を選択します。  
  
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
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Parameters"></a> パラメーター  
 入力パラメーターを含むクエリ変数またはストアド プロシージャがクエリ テキストに含まれている場合、対応するデータセットのクエリ パラメーターとレポートのレポート パラメーターが自動的に生成されます。 クエリ テキストには、各クエリ変数の DECLARE ステートメントを含めないでください。  
  
 たとえば、次の SQL クエリでは、`EmpID` という名前のレポート パラメーターが作成されます。  
  
```  
SELECT FirstName, LastName FROM HumanResources.Employee E INNER JOIN  
       Person.Contact C ON  E.ContactID=C.ContactID   
WHERE EmployeeID = (@EmpID)  
```  
  
 レポート パラメーターの既定のデータ型は Text です。各レポート パラメーターには自動的に作成されたデータセットが設定され、使用可能な値のドロップダウン リストで使用されます。 レポート パラメーターを作成した後に、既定値の変更が必要になる場合があります。 詳細については、「[レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Remarks"></a> 解説  
  
###### <a name="platform-and-version-information"></a>プラットフォームおよびバージョン情報  
 プラットフォームおよびバージョン サポートの詳細については、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブック](http://go.microsoft.com/fwlink/?linkid=121312)にある [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメントの「[Reporting Services でサポートされるデータ ソース (SSRS)](../create-deploy-and-manage-mobile-and-paginated-reports.md)」を参照してください。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="HowTo"></a> 操作方法に関するトピック  
 データ接続、データ ソース、およびデータセットを操作する手順について説明します。  
  
 [データ接続またはデータ ソース追加および確認&#40;レポート ビルダーおよび SSRS&#41;](add-and-verify-a-data-connection-report-builder-and-ssrs.md)  
  
 [共有データセットまたは埋め込みデータセットの作成 (レポート ビルダーおよび SSRS)](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)  
  
 [データセットへのフィルターの追加 (レポート ビルダーおよび SSRS)](add-a-filter-to-a-dataset-report-builder-and-ssrs.md)  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
##  <a name="Related"></a> 関連項目  
 次に示すセクションでは、レポート データの概念が詳細に説明されているほか、データに関連するレポートのパーツを定義しカスタマイズし使用する手順が説明されています。  
  
 [レポートにデータを追加&#40;レポート ビルダーおよび SSRS&#41;](report-datasets-ssrs.md)  
 レポートのデータへのアクセスの概要について説明します。  
  
 [レポート ビルダーでのデータ接続、データ ソース、および接続文字列](../data-connections-data-sources-and-connection-strings-in-report-builder.md)  
 データ接続とデータ ソースについて説明します。  
  
 [レポート埋め込みデータセットと共有データセット (レポート ビルダーおよび SSRS)](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)  
 埋め込みデータセットと共有データセットについて説明します。  
  
 [データセット フィールド コレクション (レポート ビルダーおよび SSRS)](dataset-fields-collection-report-builder-and-ssrs.md)  
 クエリによって生成されるデータセット フィールド コレクションについて説明します。  
  
 [Reporting Services でサポートされるデータ ソース &#40;SSRS&#41;](../create-deploy-and-manage-mobile-and-paginated-reports.md) ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [オンライン ブックの [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ドキュメント](http://go.microsoft.com/fwlink/?linkid=121312))。  
 各データ拡張機能のプラットフォームおよびバージョン サポートに関する詳細な情報です。  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../2014-toc/media/uparrow16x16.gif "[トップに戻る] リンクで使用される矢印アイコン") [トップに戻る](#BackToTop)  
  
## <a name="see-also"></a>参照  
 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](../report-design/report-parameters-report-builder-and-report-designer.md)   
 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)   
 [式 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/expressions-report-builder-and-ssrs.md)  
  
  