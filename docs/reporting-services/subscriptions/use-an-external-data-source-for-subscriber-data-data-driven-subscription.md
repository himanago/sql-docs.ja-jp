---
title: "サブスクライバー データ (データ ドリブン サブスクリプション) の外部データ ソースを使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscriber data sources [Reporting Services]
- subscriptions [Reporting Services], external data sources
- query-based subscriptions [Reporting Services]
- external data sources [Reporting Services]
- data-driven subscriptions
- data sources [Reporting Services], subscriptions
ms.assetid: 1cade8ec-729c-4df8-a428-e75c9ad86369
caps.latest.revision: 43
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a337202cea263001fe810c91a607fa1746219bd6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="use-an-external-data-source-for-subscriber-data-data-driven-subscription"></a>サブスクライバー データに対して外部データ ソースを使用する (データ ドリブン サブスクリプション)
  データ ドリブン サブスクリプションでは、外部データ ソースからデータを取得するクエリまたはコマンドによって、動的サブスクリプション データが提供されます。 サブスクリプション データは、データ ドリブン サブスクリプション処理の要件を満たす、サポートされているデータ ソースから取得できます。 クエリまたはコマンドの構文は、レポート サーバーと一緒にインストールされたデータ処理拡張機能に対して有効である必要があります。  
  
## <a name="data-processing-requirements"></a>データ処理の要件  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] は、データ処理拡張機能を使用して、サブスクリプション データを取得します。 推奨されているデータ ソースには、次の種類があります。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リレーショナル データベース  
  
-   Oracle データベース  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の多次元データ ソースおよびデータ マイニング データ ソース  
  
-   XML データ ソース  
  
     サブスクライバー データ用に XML データ処理拡張機能を使用する場合、サブスクリプションのクエリ タイムアウト設定を大きくしてください。 XML データ処理拡張機能では、秒ではなくミリ秒がクエリ タイムアウト値に使用されています。 タイムアウトの値を大きくしないと、処理時間の不足でサブスクリプションが失敗することがあります。  
  
     サブスクライバー データ ソースへの接続を構成するときに **[資格情報を必要としない]** オプションを使用しないでください。 XML データ処理拡張機能を使用して実行時にサブスクリプション データを取得する場合、保存されている資格情報を使用することをお勧めします。  
  
 サポートされている他の種類のデータ ソースを使用できる場合もありますが、サポートされているすべてのデータ ソースに関して動作が保証されているわけではありません。 たとえば、次のデータ ソースの種類は、サブスクライバー データに使用できません。  
  
-   SAP Netweaver BI データベース  
  
-   レポート モデル  
  
 データ ドリブン サブスクリプションでカスタム データ処理拡張機能を使用する場合は、 <xref:Microsoft.ReportingServices.DataProcessing.IDbCommand> および <xref:Microsoft.ReportingServices.DataProcessing.IDataReader> インターフェイスを実装する必要があります。 データ処理拡張機能では、スキーマのみのクエリ実行をサポートする必要があります。 このクエリは、デザイン時に列のメタデータを取得するために使用します。これにより、サブスクリプション定義の配信オプションおよびレポート パラメーターにユーザーが列をマップできるようになります。 スキーマのみのクエリ実行は、ユーザーによるサブスクリプション定義の初期段階に使用されます。  
  
## <a name="query-requirements"></a>クエリの要件  
 サブスクリプション データを取得するクエリを作成する場合は、次の点に注意してください。  
  
-   サブスクリプションに対して作成できるクエリは 1 つのみです。  
  
-   クエリでは、配信オプションおよびレポート パラメーターの指定に使用するすべての値を返す必要があります。  
  
-   レポート サーバーでは、結果セットの行ごとにレポート配信が作成されます。 結果セットが 300 行の場合、レポート サーバーでは、300 個のレポートについて配信が試行されます。  
  
## <a name="setting-delivery-options-using-variable-data-from-a-subscriber-database"></a>サブスクライバー データベースの変数データを使用した配信オプションの設定  
 サブスクライバー データベースのデータを使用して、各受信者に関する配信オプションをカスタマイズできます。 利用可能なオプションは、使用している配信拡張機能の種類によって決まります。 レポート サーバーの電子メール配信拡張機能を使用している場合、クエリは、各サブスクライバーの電子メール エイリアスを含む必要があります。 ファイル共有配信を使用している場合、サブスクライバー固有のレポート ファイルの作成や配信先の指定に使用できる値をサブスクライバー データに含める必要があります。 詳細については、「 [Reporting Services の電子メール配信](../../reporting-services/subscriptions/e-mail-delivery-in-reporting-services.md)」を参照してください。  
  
## <a name="passing-parameter-values-from-the-subscriber-database-to-the-report"></a>サブスクライバー データベースからレポートへのパラメーター値の受け渡し  
 パラメーター化されたレポート用のデータ ドリブン サブスクリプションを作成する場合、変数パラメーター値を使用して、各レポートの出力をカスタマイズできます。 たとえば、サブスクライバー データベースには、レポート データのフィルター処理に使用できる従業員 ID 番号、雇用日、職種、および勤務地情報が含まれていることがあります。 これらの列データまたは他の使用可能な列データに基づいたパラメーターをレポートが受け取ると、そのパラメーターを適切な列にマップすることができます。  
  
 サブスクライバー フィールドをレポート パラメーターにマップするときは、データ型および列の長さに互換性があることを確認してください。 データ型に不一致がある場合、サブスクリプションの処理中にエラーが発生します。 パラメーター化されたレポートでサブスクライバーのデータの使用に関する詳細については、次を参照してください[データ ドリブン サブスクリプション &#40; を作成する。SSRS チュートリアル &#41;](../../reporting-services/create-a-data-driven-subscription-ssrs-tutorial.md).  
  
## <a name="modifying-the-subscriber-data-source"></a>サブスクライバー データ ソースの変更  
 サブスクライバー データ ソースに以下の変更を加えると、サブスクリプションの実行を防ぐことができます。  
  
-   サブスクリプションで参照されている列の削除  
  
-   データ ソースのテーブル構造の変更  
  
-   データ型およびその他の列プロパティの変更  
  
 これらの変更のいずれかを行う場合は、サブスクリプションを更新する必要があります。  
  
## <a name="see-also"></a>参照  
 [データ ドリブン サブスクリプションを作成、変更、および削除する](../../reporting-services/subscriptions/create-modify-and-delete-data-driven-subscriptions.md)   
 [データ ドリブン サブスクリプション](../../reporting-services/subscriptions/data-driven-subscriptions.md)   
 [サブスクリプションと配信 & #40 です。Reporting Services &#41;](../../reporting-services/subscriptions/subscriptions-and-delivery-reporting-services.md)  
  
  