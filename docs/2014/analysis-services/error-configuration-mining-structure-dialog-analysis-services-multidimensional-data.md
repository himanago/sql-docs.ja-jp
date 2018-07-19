---
title: エラーの構成 (マイニング構造 ダイアログ ボックス) (Analysis Services - 多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.miningstructuredialog.general.f1
ms.assetid: d9aa028b-bad9-49c7-a81c-c2150e4dd481
caps.latest.revision: 12
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 73c3627f3861b978a9e539943bcb65777b2f36b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37257408"
---
# <a name="error-configuration-mining-structure-dialog-box-analysis-services---multidimensional-data"></a>[エラーの構成] ([マイニング構造] ダイアログ ボックス) (Analysis Services - 多次元データ)
  **SQL Server Management Studio** で **[マイニング構造のプロパティ]** ダイアログ ボックスの **[エラーの構成]** ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内のマイニング構造のエラー構成プロパティを設定できます。  
  
## <a name="options"></a>および  
 **既定のエラー構成を使用して、**  
 処理操作でオブジェクトに対して既定のエラー構成を使用します。  
  
 **[キー エラー アクション]**  
 参照できない処理の間に新しいキーが検出されたとき、発生するアクションを次の中から 1 つ選択します。  
  
-   **[不明な種類に変換]** は、レコードの情報を不明なメンバーに集計します。  
  
-   **[レコードの破棄]** は、レコードの情報をオブジェクトでの処理から除外します。  
  
 **エラーの数を無視します。**  
 処理中に発生するエラーは、すべて無視します。  
  
 **[エラー時に停止する]**  
 エラーが発生した場合、処理を停止します。 このオプションによって、 **[エラー数]** オプションおよび **[エラー時のアクション]** オプションが有効になります。  
  
 **[エラー数]**  
 処理が停止される前に無視できるエラーの数を入力します。  
  
 **[エラー時のアクション]**  
 エラー数が **[エラー数]** の値を超えたときに行うアクションを次の中から 1 つ選択します。  
  
-   **[処理の停止]** は、処理中の操作を終了します。  
  
-   **[ログ記録の停止]** は、エラーのログ記録を停止しますが、処理中の操作は続行します。  
  
 **[見つからないキー]**  
 オブジェクトの処理の際にキーが見つからなかった場合に行うアクションを次の中から 1 つ指定します。  
  
-   **[エラーを無視する]** は、エラーを無視します。  
  
-   **[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。  
  
-   **[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。  
  
 **[重複キー]**  
 オブジェクトの処理の際に重複キーが見つかった場合に行うアクションを次の中から 1 つ指定します。  
  
-   **[エラーを無視する]** は、エラーを無視します。  
  
-   **[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。  
  
-   **[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。  
  
 **[不明な種類に変換された NULL キー]**  
 オブジェクトの処理の際に NULL メンバー キーが不明なメンバーに追加された場合に行うアクションを次の中から 1 つ指定します。  
  
-   **[エラーを無視する]** は、エラーを無視します。  
  
-   **[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。  
  
-   **[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。  
  
 **[許可されていない NULL キー]**  
 オブジェクトの処理の際に NULL キーが見つかったが許可されていない場合に行うアクションを次の中から 1 つ指定します。  
  
-   **[エラーを無視する]** は、エラーを無視します。  
  
-   **[報告して続行する]** は、エラーを報告して、処理中の操作を続行します。  
  
-   **[報告して停止する]** は、エラーを報告して、処理中の操作を停止します。  
  
 **[エラー ログのパス]**  
 エラー ログ ファイルの完全なパスとファイル名を入力します。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のプロパティ ダイアログ ボックス&#40;Analysis Services - データ マイニング&#41;](mining-structure-properties-dialog-analysis-services-data-mining.md)   
 [一般的な&#40;マイニング構造 ダイアログ ボックス&#41; &#40;Analysis Services - データ マイニング&#41;](general-mining-structure-dialog-box-analysis-services-data-mining.md)  
  
  