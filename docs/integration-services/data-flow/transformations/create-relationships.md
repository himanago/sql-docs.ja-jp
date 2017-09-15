---
title: "リレーションシップの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.createrelationships.f1
ms.assetid: 6ebd305f-ffd2-4a1d-b24c-e28c151b94f5
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a9f511b91e0e085c07dcf4dfb7742514ddad6070
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="create-relationships"></a>[リレーションシップの作成]
  **[リレーションシップの作成]** ダイアログ ボックスを使用すると、[あいまい参照変換エディター]、[参照変換エディター]、および [用語参照変換エディター] で設定したソース列と参照テーブル列の間のマッピングを編集できます。  
  
> [!NOTE]  
>  **[リレーションシップの作成]** ダイアログ ボックスを [用語参照変換エディター] から開いた場合、 **[入力列]** と **[参照列]** の一覧のみが表示されます。  
  
 **[リレーションシップの作成]** ダイアログ ボックスを使用した変換の詳細については、「 [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)」、「 [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)」、および「 [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[入力列]**  
 使用できる入力列の一覧から選択します。  
  
 **[参照列]**  
 使用できる参照列の一覧から列を選択します。  
  
 **[マッピングの種類]**  
 あいまい一致と完全一致のどちらかを指定します。  
  
 あいまい一致を使用するときには、すべての列にわたって行が十分に類似している場合に行が重複していると見なされます。 あいまい一致により得られる結果を改善するために、一部の列であいまい一致ではなく完全一致を使用するように指定できます。 たとえば、特定の列にエラーや矛盾がないことがわかっている場合は、その列に対して完全一致を指定できます。この列に同一の値が含まれている行のみ、重複している可能性があると見なされます。 これにより、他の列におけるあいまい一致の正確性が高まります。  
  
 **[比較フラグ]**  
 文字列比較オプションについては、「 [文字列データの比較](../../../integration-services/data-flow/comparing-string-data.md)」を参照してください。  
  
 **[最小類似]**  
 スライダーを使用して、類似のしきい値を列レベルで設定します。 参照元の値と参照先の値が一致すると見なされるためには、この値が 1 に近いほど高い類似性が要求されます。 しきい値を増加させると候補レコードとして処理対象になる数が少なくなるため、一致処理の速度が向上します。  
  
 **[類似出力の別名]**  
 選択された列の類似スコアを格納する、新しい出力列に付ける名前を指定します。 この値を空にした場合、出力列は作成されません。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換エディターと &#40; です。「列」 タブと &#41; です。](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)   
 [参照変換エディター」 (&) &#40; です。「列」 ページと &#41; です。](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [用語参照変換エディターと &#40; です。用語参照」 タブと &#41; です。](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-term-lookup-tab.md)  
  
  