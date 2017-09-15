---
title: "追加または削除 (レポート ビルダーおよび SSRS) を示すインジケーター |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8b1aac1-53ef-47a4-afc0-8fa866c6c480
caps.latest.revision: 8
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1356d575f58eb36d00f52bcbac1483ce902b1954
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="add-or-delete-an-indicator-report-builder-and-ssrs"></a>インジケーターの追加または削除 (レポート ビルダーおよび SSRS)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 改ページ調整されたレポートのインジケーターは、1 つのデータ値の状態をひとめでわかるようにするための小さなゲージです。 詳細については、「 [インジケーター (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)」を参照してください。  
  
 通常、インジケーターはテーブルまたはマトリックス内のセルに置かれますが、単独で使用したり、ゲージと並べて使用したり、ゲージに埋め込むこともできます。  
  
 インジケーターを最初に追加すると、既定では測定単位としてパーセンテージを使用するように構成されます。 パーセンテージの範囲は、インジケーター セットのメンバー間に均等に配分されます。テーブルやマトリックスなど、インジケーターの親が、インジケーターによって表示される値のスコープです。  
  
 インジケーターの値および状態は、更新することができます。 詳細については、次の各トピックを参照してください。  
  
-   [インジケーター アイコンとインジケーター セットの変更 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/change-indicator-icons-and-indicator-sets-report-builder-and-ssrs.md)  
  
-   [設定および測定単位の構成 &#40; レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/set-and-configure-measurement-units-report-builder-and-ssrs.md)  
  
-   [同期スコープの設定 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/set-synchronization-scope-report-builder-and-ssrs.md)  
  
 インジケーターは、ゲージ パネル内に配置されるため、**[インジケーターのプロパティ]** ダイアログ ボックスまたは**プロパティ** ペインを使用してインジケーターを構成するには、パネルの代わりにインジケーターを選択する必要があります。 次の図は、ゲージ パネルで選択されたインジケーターを示します。  
  
 ![rs_GaugePanelWithIndicator](../../reporting-services/report-design/media/rs-gaugepanelwithindicator.gif "rs_GaugePanelWithIndicator")  
  
> [!NOTE]  
>  列の幅とデータ値の長さにより、テーブル内またはマトリックス セル内のテキストは、折り返されて複数行に表示されることがあります。 そのような場合、インジケーター アイコンが引き伸ばされて形が変わる場合があります。 これにより、インジケーター アイコンが読みにくくなることがあります。 インジケーターは、四角形の中に配置し、アイコンが引き伸ばされないようにしてください。  
  
## <a name="to-add-an-indicator-to-a-table-or-matrix"></a>テーブルまたはマトリックスにインジケーターを追加するには  
  
1.  表示するデータのテーブルおよびマトリックスが含まれる既存のレポートを開くか、新しいレポートを作成します。 詳細については、次を参照してください。[テーブル & #40 です。レポート ビルダーおよび SSRS &#41;](../../reporting-services/report-design/tables-report-builder-and-ssrs.md)または[マトリックス](../../reporting-services/report-design/create-a-matrix-report-builder-and-ssrs.md)です。  
  
2.  テーブルまたはマトリックスに列を挿入します。 詳細については、「[列の挿入または削除 (レポート ビルダーおよび SSRS)](../../reporting-services/report-design/insert-or-delete-a-column-report-builder-and-ssrs.md)」を参照してください。  
  
3.  必要に応じて、**[挿入]** タブで **[四角形]** をクリックし、新しい列のセルをクリックします。  
  
4.  **[挿入]** タブで、 **[インジケーター]**をクリックし、新しい列のセルをクリックします。  
  
     セルに四角形を追加した場合は、そのセルをクリックします。  
  
5.  左側のペインの **[インジケーター スタイルの選択]** ダイアログ ボックスで、目的のインジケーター タイプをクリックし、インジケーター セットをクリックします。  
  
6.  **[OK]**をクリックします。  
  
7.  インジケーターをクリックします。 **ゲージ データ** ペインが開きます。  
  
8.  **[値]** 領域の **[(未指定)]** ドロップダウン リストで、インジケーターとして値を表示するフィールドをクリックします。  
  
     インジケーターは既定値を使用するように構成されています。 既定では、インジケーターは測定単位としてパーセンテージを使用するように構成されており、パーセンテージの範囲は、インジケーターのメンバー間に均等に配分されます。インジケーターが示す値には、最も近いグループのスコープが使用されます。  
  
## <a name="to-delete-an-indicator-to-a-table-or-matrix"></a>テーブルまたはマトリックスからインジケーターを削除するには  
  
1.  削除するインジケーターを右クリックし、 **[削除]**をクリックします。  
  
    > [!NOTE]  
    >  インジケーターは、他のインジケーターまたはゲージを含むゲージ パネル内に配置されている場合があります。 ゲージ パネルに複数の項目が含まれている場合は、ゲージ パネルではなく、削除するインジケーターをクリックするよう注意してください。 ゲージ パネルをクリックして削除すると、ゲージ パネルだけでなく、その中の項目がすべて削除されます。  
  
2.  **[削除]**をクリックします。  
  
## <a name="see-also"></a>参照  
 [インジケーター &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/indicators-report-builder-and-ssrs.md)  
  
  