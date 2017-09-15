---
title: "マスター データ サービスからデータを Excel にエクスポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dd29389b-928c-4e50-995c-c6af27f97805
caps.latest.revision: 16
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7d2303d6a02bbed69b87e45120ee3de51f0278be
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="export-data-to-excel-from-master-data-services"></a>マスター データ サービスから Excel へのデータのエクスポート
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、データを使用するには、MDS リポジトリからデータをエクスポートする必要があります。  
  
 読み込み前にデータセットをフィルター処理する場合は、「[エクスポート前のデータのフィルター処理 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/filter-data-before-exporting-mds-add-in-for-excel.md)」を参照してください。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[エクスプローラー]** 機能領域にアクセスする権限が必要です。  
  
### <a name="to-export-data-from-mds-into-excel"></a>MDS から Excel にデータをエクスポートするには  
  
1.  Excel を開いて、**[マスター データ]** タブで MDS リポジトリに接続します。 詳細については、「[MDS リポジトリへの接続 (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/connect-to-an-mds-repository-mds-add-in-for-excel.md)」を参照してください。  
  
2.  **[マスター データ エクスプローラー]** ペインで、モデルおよびバージョンを選択します。 エンティティの一覧が作成されます。  
  
    -   **[マスター データ エクスプローラー]** ペインが表示されない場合は、 **[接続と読み込み]** グループの **[エクスプローラーの表示]**をクリックします。  
  
    -   **[マスター データ エクスプローラー]** ペインが無効になっている場合は、既存のシートに MDS によって管理されるデータが既に含まれています。 ペインを有効にするには、新しいワークシートを開きます。  
  
3.  **[マスター データ エクスプローラー]** ペインのエンティティの一覧で、読み込むエンティティをダブルクリックします。  
  
    > [!NOTE]  
    >  -   最初の 100 万個のメンバーだけが Excel に読み込まれます。 読み込む前に一覧をフィルター処理するには、リボンの **[接続と読み込み]** グループで、 **[フィルター]**をクリックします。  
    > -   制約リスト (ドメイン ベースの属性) の列では、既定で最初の 25,000 個の値だけが読み込まれます。 この数値は、Excel がインストールされているコンピューターにある、excelusersettings.config ファイルの MaximumDbaEntitySize プロパティで変更できます。 このファイルは C:\Users\\<ユーザー\>\AppData\Local\Microsoft\Microsoft SQL Server\130\MasterDataServices\\ にあります。  
    >   
    >      ドメイン ベースの属性に MaximumDbEntitySize プロパティの設定値を超えている値の数がある場合は、値の一覧は読み込まれません。  
  
    > [!NOTE]  
    >  32 ビットの Excel で Microsoft Excel 用アドインを使用して、テキスト区切りのデータを読み込み、 **[ロードするセル数]** プロパティと **[パブリッシュするセル数]** プロパティの設定が両方とも最大値の 1000 に設定されている場合、メモリ不足エラーが発生します。 **[ロードするセル数]** および **[パブリッシュするセル数]**に最大値を設定するには、64 ビットの Excel を使用する必要があります。  
  
## <a name="next-steps"></a>次の手順  
 [Excel からマスター データ サービスにデータをインポートする (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)  
  
## <a name="see-also"></a>参照  
 [概要: Excel へのデータのエクスポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-exporting-data-to-excel-mds-add-in-for-excel.md)   
 [フィルター ダイアログ ボックス & #40 です。MDS 用のアドインの Excel &#41;](../../master-data-services/microsoft-excel-add-in/filter-dialog-box-mds-add-in-for-excel.md)   
 [概要: Excel からのデータのインポート (Excel 用 MDS アドイン)](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  