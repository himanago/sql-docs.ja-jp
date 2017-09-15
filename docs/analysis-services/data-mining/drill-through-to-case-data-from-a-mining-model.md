---
title: "マイニング モデルからケース データにドリルスルー |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drillthrough [Analysis Services]
ms.assetid: b4d3f350-e543-4ea9-b3a2-b4f7c0a9ae27
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 849c244bdfb40770d8038a78a430faa7ff26b6b8
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="drill-through-to-case-data-from-a-mining-model"></a>マイニング モデルからケース データへのドリルスルー
  モデル ケースへのドリルスルーを許可するようにマイニング モデルが構成されている場合は、モデルの参照時に、モデルの作成に使用されたケースに関する詳細情報を取得できます。 さらに、基になるマイニング構造が、構造ケースへのドリルスルーを許可するように構成されており、ユーザーが適切な権限を持っている場合は、マイニング構造から情報を返すことができます。 これには、マイニング モデルに含まれていない列を含めることもできます。  
  
 基になるデータへのドリルスルーがマイニング構造で許可されておらず、マイニング モデルでは許可されている場合、モデル ケースの情報は表示できますが、マイニング構造の情報は表示できません。  
  
> [!NOTE]  
>  **AllowDrillthrough** プロパティを **True**に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。 ただし、ドリルスルーを有効にした後、ケース データを表示する前にモデルを再処理する必要があります。 詳細については、「 [Enable Drillthrough for a Mining Model](../../analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md)」(マイニング モデルのドリルスルーの有効化) を参照してください。  
  
 使用するビューアーの種類に応じて、次に示す方法で、ドリルスルーするノードを選択できます。  
  
|ビューアー名|ペイン名またはタブ名|選択するノード|  
|-----------------|----------------------|-----------------|  
|**Microsoft ツリー ビューアー**|**[デシジョン ツリー]** タブ|ツリー ノードをクリックします。<br /><br /> **注** **All** ノードにはドリルスルーを使用しないでください。結果が返されるまでに非常に時間がかかることがあります。|  
|**Microsoft クラスター ビューアー**|**クラスター ダイアグラム**|クラスター ノードをクリックします。|  
|**Microsoft クラスター ビューアー**|**クラスターのプロファイル**|クラスター列内の任意の場所をクリックします。|  
|**Microsoft アソシエーション ビューアー**|**[ルール]** タブ|一連のルールを含む行をクリックします。|  
|**Microsoft アソシエーション ビューアー**|**[アイテムセット]** タブ|アイテムセットを含む行をクリックします。|  
|**Microsoft シーケンス クラスター ビューアー**|**[ルール]** タブ|一連のルールを含む行をクリックします。|  
|**Microsoft シーケンス クラスター ビューアー**|**[アイテムセット]** タブ|アイテムセットを含む行をクリックします。|  
  
> [!NOTE]  
>  ドリルスルーを使用できないモデルもあります。 ドリルスルーを使用できるかどうかは、モデルの作成に使用したアルゴリズムによって異なります。 ドリルスルーをサポートするマイニング モデルの種類の一覧については、「 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)に設定することで、既存のマイニング モデルにドリルスルー機能を追加できます。  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a>マイニング モデルからのドリルスルー データを表示するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のマイニング モデルを含むマイニング構造を開きます。  
  
2.  データ マイニング デザイナーで、 **[マイニング モデル ビューアー]** タブをクリックします。  
  
3.  **[マイニング モデル]** ボックスの一覧からモデルを選択します。  
  
4.  **[ビューアー]** ボックスの一覧からビューアーを選択し、特定のノードを右クリックします。  
  
5.  **[ドリルスルー]**を選択してから、 **[モデル列のみ]**または **[モデル列および構造列]** を選択します。 **[ドリルスルー]** ウィンドウが表示されます。  
  
6.  データをクリップボードにコピーするには、テーブル内の任意の行を右クリックして **[すべてコピー]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [ドリルスルー クエリ &#40;データ マイニング&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  