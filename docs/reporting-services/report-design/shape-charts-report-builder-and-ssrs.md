---
title: "図形グラフ (レポート ビルダーおよび SSRS) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b8404c1-aa89-4350-8bd6-203bc0446ee4
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 84ee7a9030bb27725994a33860b26b8754034cd9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="shape-charts-report-builder-and-ssrs"></a>図形グラフ (レポート ビルダーおよび SSRS)
  図形グラフでは、全体に占める割合 (パーセント) として値データが表示されます。 図形グラフは、通常、セット内の異なる値間での相対的な比較を示すために使用されます。 カテゴリは、図形の個々のセグメントによって表されます。 セグメントのサイズは、値によって決まります。 図形グラフは円グラフに用途が似ていますが、カテゴリは大きい方から順に並べられます。  
  
 じょうごグラフでは、徐々に面積が小さくなるように値が表示されます。 領域のサイズは、系列値がすべての値の合計に占める割合で決まります。 たとえば、じょうごグラフを使用して、Web サイト閲覧者の傾向を表示できます。 じょうごグラフでは、最上部に広い領域が表示されてホームページのヒット数を示し、他の領域はそれに比例して小さくなります。 じょうごグラフにデータを追加する方法の詳細については、「 [グラフ (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)」を参照してください。  
  
 次の図は、じょうごグラフの例を示しています。  
  
 ![じょうごグラフ](../../reporting-services/report-design/media/rs-funnelchart.gif "じょうごグラフ")  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="variations"></a>バリエーション  
  
-   **ピラミッド**: ピラミッド グラフでは、相対的なデータが表示されるため、グラフはピラミッドのようになります。  
  
## <a name="data-considerations-for-shape-charts"></a>図形グラフのデータに関する注意点  
  
-   図形グラフは、その視覚的な効果が理由で、レポートでよく使用されます。 ただし、図形グラフは、非常に単純な種類のグラフであるため、データを最適に表すことができない場合があります。 7 個以下のデータ ポイントでデータを集計した場合のみ、図形グラフの使用を検討してください。 通常、各データ領域にカテゴリを 1 つだけ表示する場合に、図形グラフを使用します。  
  
-   図形グラフでは、各データ グループがグラフの個別のセグメントとして表示されます。 少なくとも 1 つのデータ フィールドと 1 つのカテゴリ フィールドを追加する必要があります。 複数のデータ フィールドが図形グラフに追加されると、図形グラフでは、両方のデータ フィールドが同じグラフ内に表示されます。  
  
-   図形グラフは、全体に占める比率を整然とした順序で表現したときに最も効果を発揮します。 ただし、一貫性を維持するために、既定では、データセット内の値の並べ替えが行われません。 じょうごグラフやピラミッド グラフでデータをできるだけ正確に表現するには、大きい方から順に値を並べ替えることを検討してください。 詳細については、「[データのフィルター、グループ化、および並べ替え &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。  
  
-   比率を計算する場合、NULL、空、負、および 0 の各値は無効です。 このため、これらの値は図形グラフに表示されません。 このような値をグラフ上に表示する必要がある場合は、グラフの種類を図形グラフ以外のグラフに変更してください。 図形以外のグラフに空のポイントを追加する方法の詳細については、次を参照してください[グラフ &#40; を空のポイントの追加。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/add-empty-points-to-a-chart-report-builder-and-ssrs.md).  
  
-   図形グラフでカスタム パレットを使用して独自の色を定義している場合は、各データ ポイントを独自の色で強調表示するのに十分な色がパレットにあることを確認します。 詳細については、「 [グラフの系列の色の書式設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)をクリックします。  
  
-   図形グラフでは、その他すべてのグラフの種類と異なり、個々のデータ ポイントが凡例に表示されます。個々の系列は表示されません。  
  
-   じょうごグラフでは、値軸およびカテゴリ軸の設定が無視されます。 複数のカテゴリ グループまたは系列グループがある場合は、グラフの凡例にグループのラベルが表示されます。  
  
-   図形グラフは、同じグラフ領域内で他の種類のグラフと組み合わせることはできません。 図形グラフに表示されるデータと、他の種類のグラフに表示されるデータとの比較を示す必要がある場合は、2 つ目のグラフ領域を追加する必要があります。  
  
-   視覚的な効果を高めるために、円グラフおよびドーナツ グラフに追加で描画スタイルを適用できます。 参照してください[グラフ &#40; の系列の色の書式設定レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/formatting-series-colors-on-a-chart-report-builder-and-ssrs.md)詳細についてはします。  
  
## <a name="see-also"></a>参照  
 [グラフと &#40; です。レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)   
 [グラフと &#40; を書式設定レポート ビルダーおよび SSRS &#41; です。](../../reporting-services/report-design/formatting-a-chart-report-builder-and-ssrs.md)   
 [グラフ &#40; 内の空および Null データ ポイントレポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/empty-and-null-data-points-in-charts-report-builder-and-ssrs.md)   
 [円グラフと #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/pie-charts-report-builder-and-ssrs.md)  
  
  