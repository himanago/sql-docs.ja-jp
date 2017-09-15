---
title: "表示部分の合計と非表示部分の合計 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea9d02f2-a668-4547-ade5-e3d077a2e1bd
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ee15de7e61b6ebf53fdbd6cb8f1fb3920c010134
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="visual-totals-and-non-visual-totals"></a>表示部分の合計と非表示部分の合計
  表示部分の合計とは、列または行の最後に表示される合計で、列または行内に表示されるすべてのアイテムを加算したものです。 これは、ほとんどのテーブルが表示されるときの既定の動作です。 ただし、非表示の行を含む行全体の合計を維持しながら、テーブル内の特定の列のみを表示する場合もあります。 これらは、合計が表示部分と非表示部分の両方の値から取得されることから **非表示部分の合計**と呼ばれます。  
  
 次のシナリオは、非表示部分の合計の動作を示します。 最初のステップで表示部分の合計の既定の動作を示します。  
  
 次の例では、製品カテゴリが列、再販業者の業種が行であるテーブルから [Reseller Sales Amount] の数値を取得するための [Adventure Works] のクエリを示します。 次の SELECT ステートメントが発行されると、製品と再販業者の両方について合計が示されることに注意してください。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from [Adventure Works]`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||||  
|-|-|-|-|-|-|  
||**All Products**|**Accessories**|**Bikes**|**Clothing**|**コンポーネント**|  
|**All Resellers**|**$80,450,596.98**|**$571,297.93**|**$66,302,381.56**|**$1,777,840.84**|**$11,799,076.66**|  
|**Specialty Bike Shop**|**$6,756,166.18**|**$65,125.48**|**$6,080,117.73**|**$252,933.91**|**$357,989.07**|  
|**Value Added Reseller**|**$34,967,517.33**|**$175,002.81**|**$30,892,354.33**|**$592,385.71**|**$3,307,774.48**|  
|**Warehouse**|**$38,726,913.48**|**$331,169.64**|**$29,329,909.50**|**$932,521.23**|**$8,133,313.11**|  
  
## <a name="non-visual-on-rows-and-columns"></a>行および列の非表示部分  
 Accessories 製品と Clothing 製品、および Value Added Reseller 再販業者と Warehouse 再販業者のみのデータを含むテーブルを生成する場合、全体的な合計も維持するには、NON VISUAL を使用して次のように記述できます。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0,`  
  
 `{[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 1`  
  
 `from [Adventure Works])`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||**All Products**|**Accessories**|**Clothing**|  
|**All Resellers**|**$80,450,596.98**|**$571,297.93**|**$1,777,840.84**|  
|**Value Added Reseller**|**$34,967,517.33**|**$175,002.81**|**$592,385.71**|  
|**Warehouse**|**$38,726,913.48**|**$331,169.64**|**$932,521.23**|  
  
## <a name="non-visual-on-rows"></a>行の非表示部分  
 列の表示部分の合計を算出するが、行の合計についてはすべての [Category] の実際の合計を示すテーブルを生成するには、次のクエリを実行します。  
  
 `select [Category].members on 0,`  
  
 `[Business Type].members on 1`  
  
 `from NON VISUAL (Select {[Category].Accessories, [Category].Clothing} on 0`  
  
 `from ( Select {[Business Type].[Value Added Reseller], [Business Type].[Warehouse]} on 0`  
  
 `from [Adventure Works])`  
  
 `)`  
  
 `where [Measures].[Reseller Sales Amount]`  
  
 NON VISUAL が [Category] のみに適用されていることに注目してください。  
  
 上記のクエリの結果は、次のようになります。  
  
|||||  
|-|-|-|-|  
||All Products|Accessories|Clothing|  
|All Resellers|$73,694,430.80|$506,172.45|$1,524,906.93|  
|Value Added Reseller|$34,967,517.33|$175,002.81|$592,385.71|  
|Warehouse|$38,726,913.48|$331,169.64|$932,521.23|  
  
 前の結果と比較すると、[All Resellers] 行は [Value Added Reseller] と [Warehouse] の表示値の合計を示していますが、[All Products] 列は表示されていない製品も含むすべての製品の合計額を示していることがわかります。  
  
## <a name="see-also"></a>参照  
 [MDX の主な概念 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/key-concepts-in-mdx-analysis-services.md)   
 [Autoexists](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [メンバー、組、およびセットの操作 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX の基本的なクエリ & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)   
 [クエリおよびスライサー軸 &#40; を使用してクエリを制限します。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-restricting-the-query.md)   
 [クエリ内のキューブ コンテキストの確立 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/establishing-cube-context-in-a-query-mdx.md)  
  
  