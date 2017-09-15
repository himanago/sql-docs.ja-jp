---
title: "データ (Master Data Services) をエクスポートするサブスクリプション ビューを作成 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- subscription views [Master Data Services], creating
- creating subscription views [Master Data Services]
ms.assetid: a5e28961-af16-414a-9845-d2e06aac5214
caps.latest.revision: 10
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4934e49ef7b8e4f6b56439dd3b414fc93d5af832
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-subscription-view-to-export-data-master-data-services"></a>サブスクリプション ビューを作成してデータをエクスポートする (マスター データ サービス)
  サブスクリプション ビューを作成して、マスター データ サービスのデータをサブスクライブ システムにエクスポートします。 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] データベース内のデータのビューを作成します。  
  
## <a name="prerequisites"></a>前提条件  
 この手順を実行するには  
  
-   **[統合管理]** 機能領域にアクセスする権限が必要です。 詳細については、「[機能領域権限 (マスター データ サービス)](../master-data-services/functional-area-permissions-master-data-services.md)」を参照してください。  
  
-   モデル管理者である必要があります。 詳細については、「[Administrators &#40;Master Data Services&#41; (管理者 &#40;マスター データ サービス&#41;)](../master-data-services/administrators-master-data-services.md)」を参照してください。  
  
### <a name="to-create-and-edit-a-subscription-view"></a>サブスクリプション ビューを作成および編集するには  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[統合管理]**をクリックします。  
  
2.  メニュー バーの **[ビューの作成]**をクリックします。  
  
3.  **[サブスクリプション ビュー]** ページで、ビューを作成するには **[追加]** 、ビューを編集するには **[編集]** をクリックします。 右側にパネルが表示されます。  
  
4.  **[サブスクリプション ビューの作成]** ペインで、 **[名前]** ボックスにビューの名前を入力します。  
  
     **[サブスクリプション ビューの編集]** ペインで、 **[名前]** ボックスに更新したビューの名前を入力します。  
  
5.  **[モデル]** ボックスの一覧からモデルを選択します。  
  
6.  **[Include soft-deleted members]**(論理削除済みメンバーを含める) を選択して、論理削除済みメンバーをビューに含めます。  
  
7.  **[バージョンのオプション]** で **[バージョン]** または **[バージョン フラグ]**のいずれかを選択し、対応する一覧から選択します。  
  
    > [!TIP]  
    >  サブスクリプション ビューはバージョン フラグに基づいて作成します。 バージョンをロックするとき、サブスクリプション ビューを更新せずに未処理のバージョンにフラグを割り当て直すことができます。  
  
8.  **[データ ソース]** オプションで **[エンティティ]** または **[派生階層]** のいずれかを選択し、対応する一覧から選択します。  
  
9. **[形式]** ボックスの一覧からサブスクリプション ビュー形式を選択します。  
  
10. **[形式]** ボックスの一覧から **[明示的レベル]** または **[派生レベル]** を選択した場合、ビューに含める階層内のレベル数を入力します。  
  
11. **[保存]**をクリックします。  
  
## <a name="view-information"></a>ビュー情報  
 作成されたビューごとに、10 列の行がグリッドに追加されます。 次の表で各列について説明します。  
  
|列|Description|  
|------------|-----------------|  
|[状態]|ビューの状態。<br /><br /> クリックすると**保存**、![ステータスの更新のアイコン](../master-data-services/media/mds-statusicon-updating.png "ステータスの更新のアイコン")イメージ ビューが更新中であることを示すが表示されます。<br /><br /> 作成またはビューを編集するときにエラーがある場合、![のエラー状態をアイコン](../master-data-services/media/mds-statusicon-error.png "のエラー状態をアイコン")イメージが表示されます。<br /><br /> 状態が [ok] をそれ以外の場合、および![OK ステータス アイコン](../master-data-services/media/mds-statusicon-ok.png "OK ステータス アイコン")イメージが表示されます。|  
|名前|サブスクリプション ビュー名。|  
|[モデル]|モデル名。|  
|[バージョンのオプション]|バージョン名。|  
|[バージョン]|バージョン フラグ名。|  
|[エンティティ]|派生階層名。|  
|[データ ソース]|エンティティ名。|  
|[形式]|ビュー内のデータの型を指定します。|  
|レベル|ビュー内のレベルの数を指定します。明示的レベルまたは派生レベルのビュー形式にのみ使用されます。|  
|Include delete members (削除済みメンバーを含める)|論理削除済みメンバーをビューに含めるかどうかを示します。|  
  
 ビューをクリックすると、次の情報が表示されます。  
  
-   **作成者**: ビューを作成したユーザーの名前。  
  
-   **作成日時**: ビューが作成された日時。  
  
-   **更新者**: ビューを最後に更新したユーザーの名前。  
  
-   **更新日時**: ビューが最後に更新された日時。  
  
## <a name="see-also"></a>参照  
 [概要: データのエクスポート (マスター データ サービス)](../master-data-services/overview-exporting-data-master-data-services.md)   
 [サブスクリプション ビュー &#40; を削除します。マスター データ サービス &#41;](../master-data-services/delete-a-subscription-view-master-data-services.md)   
 [バージョン フラグ &#40; を作成します。マスター データ サービス &#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
  