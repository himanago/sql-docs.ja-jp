---
title: "テーブル (Master Data Services) からデータをインポート |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad5b83b1-8e40-4ef8-9ba8-4ea17a58b672
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 47c83a225b97e203875f940a03fe52db80525060
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="import-data-from-tables-master-data-services"></a>テーブルからのデータのインポート (マスター データ サービス)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]のモデルに一括でデータの追加および変更を行えます。  
  
 **前提条件**  
  
-   Stg. にデータを挿入する権限が必要\<名前 > _Leaf、stg.\<名前 > _Consolidated、stg.\<名前 > _relationship の各テーブルで、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベース。  
  
-   いずれか、stg.udp_ を実行するアクセス許可が必要\<名前 > _Leaf、stg.udp\_\<名前 > _Consolidated、または、stg.udp\_\<名前 > _relationship の各ストアド プロシージャ、[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]データベース。  
  
-   モデルのステータスが **[コミット済み]**でないことが必須です。  
  
 **[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースに対してデータの追加、更新、および削除を行うには**  
  
1.  必須フィールドの値を指定するなど、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースの適切なステージング テーブルにインポートするメンバーを準備します。 ステージング テーブルの概要については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
    -   リーフ メンバー、テーブルは stg.\<名前 > _Leaf、場所\<名 > は、対応するエンティティを参照します。 必須フィールドの詳細については、「[リーフ メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/leaf-member-staging-table-master-data-services.md)」を参照してください。  
  
    -   統合メンバー、テーブルは stg.\<名前 > _Consolidated です。 必須フィールドの詳細については、「[統合メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/consolidated-member-staging-table-master-data-services.md)」を参照してください。  
  
    -   明示的階層内のメンバーの位置を移動するには、テーブルは stg.\<名前 > _relationship になります。 必須フィールドの詳細については、「[リレーションシップ ステージング テーブル (マスター データ サービス)](../master-data-services/relationship-staging-table-master-data-services.md)」を参照してください。  
  
         明示的階層内のメンバーの移動の概要については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
    -   **[ImportType]** フィールドの値を使用して、メンバーの新規作成、メンバーの非アクティブ化、またはメンバーの削除を行っていることを指定します。 値の詳細については、「[リーフ メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/leaf-member-staging-table-master-data-services.md)」および「[統合メンバー ステージング テーブル (マスター データ サービス)](../master-data-services/consolidated-member-staging-table-master-data-services.md)」を参照してください。  
  
         メンバーの非アクティブ化と削除の概要については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。  
  
2.  [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を開き、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベースのデータベース エンジン インスタンスに接続します。  
  
     詳細については、「 [SQL Server Management Studio](http://msdn.microsoft.com/library/66a6b7b1-de6a-4161-82bd-98ded486947b)」を参照してください。  
  
3.  [ [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインポートおよびエクスポート] ウィザードを使用して、データをステージング テーブルにインポートします。  
  
     詳細については、「 [SQL Server Import and Export Wizard](~/integration-services/import-export-data/welcome-to-sql-server-import-and-export-wizard.md)」を参照してください。  
  
4.  次のいずれかを実行して、ステージング テーブルからデータを [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] テーブルに読み込みます。  
  
    -   データの移動先のステージング テーブルに対応するステージング ストアド プロシージャを実行します。  
  
         ステージング ストアド プロシージャとステージング テーブルの概要については、「[概要: テーブルからのデータのインポート (マスター データ サービス)](../master-data-services/overview-importing-data-from-tables-master-data-services.md)」を参照してください。 ステージング ストアド プロシージャのパラメーターの詳細およびコード例については、「[ステージング ストアド プロシージャ (マスター データ サービス)](../master-data-services/staging-stored-procedure-master-data-services.md)」を参照してください。  
  
    -   マスター データ管理の **[統合管理]** 機能領域 を使用します。  
  
         **[ステージング バッチ]** ページで、ドロップダウン リストでデータの追加先のモデルを選択してから、 **[バッチの開始]**をクリックします。 バッチ処理の状態が、 **[状態]** フィールドに示されます。 状態の詳細については、「[インポート状態 (マスター データ サービス)](../master-data-services/import-statuses-master-data-services.md)」を参照してください。  
  
         ![ステージング バッチ ページでは、マスター データ マネージャー](../master-data-services/media/mds-stagingbatchespage.png "ステージング バッチのマスター データ マネージャー ページ")  
  
         ステージング処理は、 **の** [ステージング バッチの間隔] [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]設定に定められた間隔で開始されます。 詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../master-data-services/system-settings-master-data-services.md)」を参照してください。  
  
5.  ステージング中に発生したエラーを表示します。 詳細については、「[ステージング中に発生したエラーの表示 (マスター データ サービス)](../master-data-services/view-errors-that-occur-during-staging-master-data-services.md)」および「[ステージング処理のエラー (マスター データ サービス)](../master-data-services/staging-process-errors-master-data-services.md)」を参照してください。  
  
6.  ビジネス ルールに対してデータを検証します。  
  
     マスター データ マネージャーで、モデルの **[エクスプ ローラー]** 機能領域に移動してから、データを検証するビジネス ルールを適用します。 詳細については、「[ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)](../master-data-services/validate-specific-members-against-business-rules-master-data-services.md)」を参照してください。 データの検証にはストアド プロシージャを使用することもできます。 詳細については、「[ステージング ストアド プロシージャ (マスター データ サービス)](../master-data-services/validation-stored-procedure-master-data-services.md)」を参照してください。  
  
     ステージング テーブルからデータを読み込む場合、ビジネス ルールに対してデータが自動的に検証されることはありません。 検証とその実施タイミングの詳細については、「[検証 (マスター データ サービス)](../master-data-services/validation-master-data-services.md)」を参照してください。  
  
  
