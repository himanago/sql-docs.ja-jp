---
title: "Reporting Services レポートのデータ取得に関する問題のトラブルシューティング |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/27/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7680946a-1660-4b59-a03a-c4d474cd8ed3
caps.latest.revision: 4
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3f801ab4a8033d7f457aad0483ead5cb080fd8ed
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="troubleshoot-data-retrieval-issues-with-reporting-services-reports"></a>Reporting Services レポートのデータ取得に関する問題のトラブルシューティング
レポート処理の最初の手順は、データセット クエリを実行して各データセットのレポート データを取得することです。 レポートをローカルでプレビューする場合は、データ ソースの接続と資格情報で十分な権限を使用して、コンピューターにデータを取得する必要があります。 レポートをレポート サーバーで実行する場合は、データ ソースの接続と資格情報で十分な権限を使用して、レポート サーバーでデータを取得する必要があります。 このトピックでは、レポート データの取得に関する問題のトラブルシューティングを行います。   
  
## <a name="i-cannot-create-a-connection-to-a-data-source"></a>データ ソースへの接続を作成できない  
データ ソースの作成、データセット クエリの実行、またはレポートのプレビューの際に、"データ ソース `<data source name>`への接続を作成できません" というメッセージが表示されることがあります。   
    
### <a name="data-source-is-not-available"></a>データ ソースが使用できない  
データ ソースがオフラインであるか、他の何らかの理由で使用できません。   
  
データ ソースへのアクセス権があること、およびデータ ソースが使用できることを確認してください。 たとえば、SQL Server Management Studio を使用してデータ ソースに接続します。 リレーショナル データベースおよび多次元データベースの場合は、 **[接続プロパティ]** ダイアログ ボックスの **[テスト]** ボタンを使用して、データ ソースに対する接続および権限を確認します。   
  
### <a name="data-source-credentials-are-not-valid"></a>データ ソースの資格情報が有効でない  
データ ソースへの接続に使用している資格情報に、クエリで指定されたデータを取得するための十分な権限がありません。  
  
使用している資格情報が正しい資格情報であることを確認してください。 たとえば、テーブルまたはビューからデータを取得するための権限はあっても、特定の列に対する権限がない可能性があります。また、ビューを作成するストアド プロシージャを実行するための十分な権限がない可能性もあります。   
  
> [!NOTE]  
> レポートのプレビュー用のデータの取得に使用する権限は、レポートをレポート サーバーにパブリッシュした後でデータの取得に必要になる権限とは異なる場合があります。   
  
### <a name="not-a-valid-password"></a>有効なパスワードでない  
資格情報が要求されるデータ ソースや、接続文字列で資格情報が指定されたデータ ソースでは、基になるデータ ソースのドライバーにパスワードの文字が渡されます。 パスワードまたは文字列に句読点などの特殊文字が含まれている場合、データ ソースのドライバーによってはその特殊文字を検証することができません。   
  
パスワードに特殊文字が使用されていないことを確認してください。 パスワードを変更できない場合は、データベース管理者と連携して、適切な資格情報をシステム ODBC データ ソース名 (DSN) の一部としてローカルおよびサーバーに格納します。 詳細については、MSDN の .NET Framework SDK ドキュメントの「OdbcConnection.ConnectionString」を参照してください。   
  
> [!NOTE]  
>パスワードなどのログイン情報を接続文字列に追加しないことをお勧めします。 レポート デザイナーでは、 **[データ ソースのプロパティ]** ダイアログ ボックスまたは [[共有データ ソース プロパティ] ダイアログ ボックス](~/reporting-services/report-data/enter-data-source-credentials-dialog-box-report-builder.md) の [[資格情報]](~/reporting-services/report-data/enter-data-source-credentials-dialog-box-report-builder.md) ページから、資格情報を入力できます。 ここで入力した資格情報は、レポート作成コンピューター上に安全に保管されます。  
  
## <a name="why-do-i-see-no-data-when-i-run-my-query-in-the-query-designer"></a>クエリ デザイナーでクエリを実行してもデータが表示されない  
データセットを作成すると、データセット フィールド コレクションがレポート データ ペインに表示されます。 場合によっては、データセット フィールド コレクションが想定どおりに表示されないことがあります。   
  
### <a name="import-query-does-not-import-calculated-fields"></a>クエリのインポートで計算フィールドがインポートされない  
  
レポート定義で計算フィールドが保存されていても、別のレポートからデータセット クエリをインポートする場合はそれらのフィールドは含まれません。 別のレポートからクエリをインポートしてデータセットを作成した場合、データセット クエリで指定されたフィールドのみがレポート データ ペインに表示されます。   
  
レポート データ ペインで計算フィールドを表示するには、フィールドを使用するレポートごとにフィールドを定義する必要があります。   
  
### <a name="some-data-providers-do-not-support-automatic-population-of-the-dataset-field-collection"></a>一部のデータ プロバイダーでデータセット フィールド コレクションの自動設定がサポートされない  
[データセットのプロパティ] ダイアログ ボックスでクエリを定義し、ダイアログ ボックスを閉じると、通常は、データセット フィールド コレクションがレポート データ ペインに表示されます。 データ ソースによっては、データセット フィールド コレクションが自動的に設定されない場合があります。   
  
データセット フィールド コレクションを設定するには、次の操作を行います。  
* データベースからフィールド情報を取得する権限を持っていることを確認します。 データ ソースによっては、データ ソースへのアクセス権を持っていても、テーブルまたは列へのアクセス権を持っていないことがあります。 また、ビューへのアクセス権は持っていても、ビューを作成するストアド プロシージャを実行するための権限を持っていない場合もあります。 データベース内の特定のテーブルまたは列へのアクセスを検証するには、レポート用と同じ権限を使用して、SQL Server Management Studio など、別のアプリケーションでクエリ結果を確認します。 期待したクエリ結果が得られない場合は、システム管理者に問い合わせて、必要なデータにアクセスするための権限を付与してもらいます。   
* **[データセットのプロパティ]** ダイアログ ボックスのクエリ ペインでクエリを実行します。 詳細については、「 [データセットの作成と追加 (レポート ビルダー 3.0 および SSRS)](../../reporting-services/report-data/report-datasets-ssrs.md)」を参照してください。  
* フィールドを手動で追加します。 詳細については、「 [レポート データ ペインでフィールドを追加、編集、更新する方法 (レポート ビルダー 3.0 および SSRS)](../../reporting-services/report-data/add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs.md)」を参照してください。   
  
## <a name="see-also"></a>参照  
[エラーとイベント (Reporting Services)](../../reporting-services/troubleshooting/errors-and-events-reference-reporting-services.md)  
  
  

[!INCLUDE[feedback_stackoverflow_msdn_connect](../../includes/feedback-stackoverflow-msdn-connect.md)]



