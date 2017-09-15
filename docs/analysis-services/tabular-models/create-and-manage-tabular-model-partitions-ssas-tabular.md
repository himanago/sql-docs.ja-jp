---
title: "作成し、テーブル モデル パーティション (SSAS テーブル) を管理する |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dab72cf0-95bc-4b63-95dc-505b5cd881c1
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 09a6acec0d1ee91c553d748a334733faff36bc08
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-and-manage-tabular-model-partitions"></a>テーブル モデル パーティションの作成および管理

[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  パーティションは、テーブルを論理的な部分に分割します。 各パーティションは、他のパーティションとは個別に処理 (更新) できます。 モデル作成時にあるモデルのために定義されたパーティションが、配置済みモデルで複製されます。 いったん配置されると、 **の** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ダイアログ ボックスまたはスクリプトを使用して、それらのパーティションを管理できます。 このトピックで説明するタスクで、配置済みモデル用のパーティションを作成、管理する方法を示します。  
  
  > [!NOTE]  
>  1400 互換性レベルで作成された表形式モデルでパーティションを定義するには、M クエリ ステートメントを使用します。 詳細については、次を参照してください。 [M 参照](https://msdn.microsoft.com/library/mt211003.aspx)です。 
>
  
## <a name="tasks"></a>処理手順  
 配置済みテーブル モデル データベース用のパーティションを作成、管理するには、 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを使用します。 **で** [パーティション] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]ダイアログ ボックスを表示するには、任意のテーブルを右クリックし、 **[パーティション]**をクリックします。  
  
###  <a name="bkmk_create_new"></a> 新しいパーティションを作成するには  
  
1.  **[パーティション]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  **[パーティション名]**にパーティションの名前を入力します。 既定では、既定のパーティション名に番号が付き、新しいパーティションを作成するたびにその番号が増加します。  
  
3.  **クエリ ステートメント**を入力するか、列と、クエリ ウィンドウに、パーティションに含める句を定義する、SQL または M のクエリ ステートメントを貼り付けます。  
  
4.  このステートメントを検証するため、 **[構文の確認]**をクリックします。  
  
###  <a name="bkmk_copy"></a> パーティションをコピーするには  
  
1.  **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、コピーするパーティションを選択し、 **[コピー]** をクリックします。  
  
2.  **[パーティション名]**にパーティションの新しい名前を入力します。  
  
3.  **クエリ ステートメント**、クエリ ステートメントを編集します。  
  
###  <a name="bkmk_merge"></a> 2 つ以上のパーティションをマージするには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、マージするパーティションを Ctrl キーを押しながらクリックして選択し、 **[マージ]** をクリックします。  
  
> [!IMPORTANT]  
>  パーティションをマージしても、パーティションのメタデータは更新されません。 処理操作がマージされたパーティションのすべてのデータを処理かどうかを確認する結果として得られるパーティションに、SQL または M のステートメントを編集する必要があります。  
  
###  <a name="bkmk_delete"></a> パーティションを削除するには  
  
-   **[パーティション]** ダイアログ ボックスの **[パーティション]** ボックスの一覧で、削除するパーティションを選択し、 **[削除]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [テーブル モデル パーティション](../../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)   
 [テーブル モデル パーティションの処理](../../analysis-services/tabular-models/process-tabular-model-partitions-ssas-tabular.md)  
  
  
