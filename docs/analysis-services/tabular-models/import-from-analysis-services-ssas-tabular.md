---
title: "Analysis Services (SSAS テーブル) からのインポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9a21b23-3a06-4ef8-bc06-9c79cdc54870
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 81cee939240fd9379f2c521443272ae478de6243
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="import-from-analysis-services-ssas-tabular"></a>Analysis Services からのインポート (SSAS テーブル)
  このトピックでは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のサーバーからインポート プロジェクト テンプレートを使用して既存の表形式モデルからメタデータをインポートし、新しい表形式モデル プロジェクトを作成する方法を説明します。  
  
## <a name="create-a-new-model-by-importing-metadata-from-an-existing-model-in-analysis-services"></a>Analysis Services の既存のモデルからのメタデータのインポートによる新しいモデルの作成  
 Analysis Services サーバーの既存のテーブル モデルからメタデータをコピーして、新しいテーブル モデル プロジェクトを作成するには、サーバーからインポート プロジェクト テンプレートを使用します。 新しいプロジェクトは、インポート元のモデルと同じデータ ソース接続、テーブル、リレーションシップ、メジャー、KPI、ロール、階層、パースペクティブ、およびパーティションを使用して作成されます。 ただし、データは既存のモデルから新しいモデル ワークスペースにコピーされません。 インポート プロセスが完了し、新しいモデル プロジェクトが作成された後、[すべて処理] を実行し、データ ソースから新しいモデル プロジェクト ワークスペース データベースにデータを読み込む必要があります。  
  
#### <a name="to-create-a-new-model-by-importing-metadata-from-an-existing-model"></a>既存のモデルからのメタデータのインポートによって、新しいモデルを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]**をクリックし、 **[プロジェクト]**をクリックします。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]**で **[ビジネス インテリジェンス]**をクリックし、 **[サーバーからインポート]**をクリックします。  
  
3.  **[名前]**でプロジェクトの名前を入力し、場所とソリューション名を指定してから **[OK]**をクリックします。  
  
4.  **[Analysis Services からのインポート]** ダイアログ ボックスの **[サーバー名]**で、インポートするモデル メタデータを含む Analysis Services サーバーの名前を指定します。  
  
5.  **[データベース名]**で、インポートするモデル メタデータを含むテーブル モデル データベースを選択し、 **[OK]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [プロジェクトのプロパティ &#40;SSAS テーブル&#41;](../../analysis-services/tabular-models/project-properties-ssas-tabular.md)  
  
  