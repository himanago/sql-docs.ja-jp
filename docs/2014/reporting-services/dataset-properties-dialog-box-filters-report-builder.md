---
title: データセットのプロパティ ダイアログ ボックスのフィルター (レポート ビルダー) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10025"
ms.assetid: 933a6f44-4eb7-4e73-9c40-ac0fd17b23d3
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff8ae37c2caf34432acde8fab2235a3b83b372a6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48172152"
---
# <a name="dataset-properties-dialog-box-filters-report-builder"></a>[フィルター] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)
  **[データセットのプロパティ]** ダイアログ ボックスの **[フィルター]** を選択すると、データセットに対するフィルターを作成できます。  
  
 レポート サーバー上の共有データセット定義の一部であるフィルターは、共有データセットを使用するすべてのレポートに影響を及ぼします。 共有データセットの追加フィルターは、レポートに追加してから指定できます。 これらのフィルターは、フィルターが定義されているレポートのみに影響を及ぼします。  
  
 埋め込みデータセットのフィルターは、フィルターが定義されているレポートのみに影響を及ぼします。  
  
 詳細については、「[データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[追加]**  
 一覧に新しいフィルター句を追加します。  
  
 **削除**  
 選択したフィルター句を一覧から削除します。  
  
 **上矢印**  
 選択したフィルターを一覧内で上に移動します。  
  
 **下矢印**  
 選択したフィルターを一覧内で下に移動します。  
  
 **式**  
 フィルターを適用する式を入力または選択します。 式を編集するには、式 (**[fx]**) ボタンをクリックします。  
  
 **データ型**  
 **[値]** のデータ型を選択します。 可能であれば、 **[式]** のデータ型と一致するデータ型を選択します。  
  
 **[式]** および **[値]** の値は、同じデータ型に評価される必要があります。 たとえば、 **[式]** が System.Int32 データ型のフィールドに設定され、 **[値]** が 7 に設定されている場合、ドロップダウン リストから **Integer**を選択します。  
  
 必要なデータ型のオプションがドロップダウン リストにない場合は、値を正しいデータ型に変換する式を作成します。 詳細については、「[フィルター式の例 &#40;レポート ビルダーおよび SSRS&#41;](report-design/filter-equation-examples-report-builder-and-ssrs.md)」を参照してください。  
  
 **[演算子]**  
 式と値の比較に使用する演算子を選択します。  
  
 **[値]**  
 **[式]** ボックスに指定された式を評価する際に使用する式または値を入力します。 式を編集するには、式 (**[fx]**) ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [レポート パラメーター &#40;レポート ビルダーおよびレポート デザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [データセットにフィルターを追加&#40;レポート ビルダーおよび SSRS&#41;](report-data/add-a-filter-to-a-dataset-report-builder-and-ssrs.md)   
 [レポートで式を使用して&#40;レポート ビルダーおよび SSRS&#41;](report-design/expression-uses-in-reports-report-builder-and-ssrs.md)  
  
  
