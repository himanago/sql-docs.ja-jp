---
title: Microsoft Excel へのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 74f726fc-2167-47af-9093-1644e03ef01f
caps.latest.revision: 24
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 9c72123024fff48604919df0804694e0cd6ec480
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37152103"
---
# <a name="exporting-to-microsoft-excel-report-builder-and-ssrs"></a>Exporting to Microsoft Excel (Report Builder and SSRS)
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Excel 表示拡張機能は、レポートを [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] 2007-2010 のネイティブ形式で表示します。 Excel 表示拡張機能を使用すると、レポートの列の幅は、より正確に Excel の列の幅に反映されます。  
  
 形式は、Office Open XML です。 このレンダラーによって生成されるファイルのコンテンツ タイプは **application/vnd.openxmlformats-officedocument.spreadsheetml.sheet** で、ファイル拡張子は .xlsx です。  
  
 デバイス情報設定を変更することによって、このレンダラーの既定の設定の一部を変更することができます。 詳細については、「 [Excel Device Information Settings](../excel-device-information-settings.md)」を参照してください。  
  
> [!IMPORTANT]  
>  10 MB よりも大きいレポートを Excel にエクスポートするときにエラー メッセージが表示されないようにするには、[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の最新のサービス パックをインストールします。 この問題は SP2 で修正されています。  
>   
>  問題の詳細については、 [「修正: SSRS 2012 で 10 MB を超えるレポートを Excel 形式にエクスポートでない」](http://go.microsoft.com/fwlink/p/?LinkId=402513)を参照してください。  
>   
>  最新サービス パックを入手する[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]を参照してください[SQL Server 2012 の最新サービス パックを入手する方法](http://go.microsoft.com/fwlink/p/?LinkId=402512)  
  
> [!IMPORTANT]  
>  型のパラメーターを定義するとき`String`、任意の値を使用できるテキスト ボックスで、ユーザーが表示されます。 クエリ パラメーターと関連付けられていないレポート パラメーターがあり、このパラメーター値がレポートに含まれていると、レポート ユーザーが、式の構文、スクリプト、または URL をパラメーター値に入力して、このレポートを Excel に変換することも可能になります。 別のユーザーがこのレポートを表示して、表示されたパラメーター コンテンツをクリックすると、悪意のあるスクリプトまたはリンクが意図せず実行されてしまう可能性があります。  
>   
>  悪意のあるスクリプトを誤って実行するリスクを軽減するためには、信頼されたソースのレポートしか開かないようにする必要があります。 レポートのセキュリティ保護の詳細については、「 [レポートとリソースの保護](../security/secure-reports-and-resources.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="ExcelLimitations"></a> Excel の制限  
 [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] では、Excel の機能とそのファイル形式により、エクスポートされたレポートに制限が適用されます。 最も重要な制限は、次のとおりです。  
  
-   最大列幅は 255 文字または 1726.5 ポイントです。 レンダラーでは、列幅がこの制限を下回っているかどうかは検証されません。  
  
-   行の高さの最大値は 409 ポイントです。 行の内容が多すぎて行の高さが 409 ポイントを超えた場合、Excel のセルには最大 409 ポイントまでのテキストの部分が表示されます。 セルの内容の残りの部分は、セル内にまだあります(Excel の最大文字数である 32,767 まで)。

-   行の高さの最大値は 409 ポイントなので、レポートで定義されているセルの高さが 409 ポイントより大きい場合は、セルの内容が複数の行に分割されます。 
  
-   セル内の最大文字数は 32,767 文字に制限されています。 この制限を超えた場合は、レンダラーによってエラー メッセージが表示されます。  
  
    > [!NOTE]  
    >  Excel 2003 では、Excel のワークシートでセルに表示される文字数は約 1,000 文字ですが、最大文字数に達していない限り、数式バーでの編集は可能です。 この制限は、Excel 2007-2010 には該当しません。  
  
-   Excel には最大ワークシート数が定義されていませんが、メモリやディスクの空き容量など、外部的な要因によって制限が適用される場合もあります。  
  
-   Excel では、アウトラインの入れ子が 7 レベルまで許容されます。  
  
-   他のアイテムの表示と非表示を制御するレポート アイテムが、前後の行または列に存在しない場合、アウトラインも無効化されます。  
  
### <a name="sizes-of-excel-2003-files"></a>Excel 2003 ファイルのサイズ  
 レポートを最初にエクスポートして Excel 2003 に保存するときは、Excel で *.xls ブック ファイルに自動的に適用されるファイル最適化のメリットを得ることはできません。 ファイル サイズが大きくなると、電子メール サブスクリプションと添付ファイルに関する問題が生じる可能性があります。 エクスポートしたレポートの \*.xls ファイルのサイズを小さくするには、その \*.xls ファイルを開いてからブックを再保存します。 ブックを再保存することで、通常はファイル サイズが 40 ～ 50 パーセント縮小します。  
  
### <a name="text-boxes-and-text"></a>テキスト ボックスとテキスト  
 テキスト ボックスとテキストには、次の制限事項が適用されます。  
  
-   テキスト ボックスの値が式である場合、その値は Excel の数式には変換されません。 各テキスト ボックスの値は、レポートの処理時に評価されます。 評価された式は、Excel の各セルのコンテンツとしてエクスポートされます。  
  
-   テキスト ボックスは 1 つの Excel セル内に表示されます。 Excel セル内部の個々のテキストでサポートされている書式設定は、フォント サイズ、フォント フェイス、装飾、およびフォント スタイルです。  
  
-   "上線" のテキスト効果は Excel ではサポートされません。  
  
-   Excel では、セルの左右に約 3.75 ポイントの既定の余白が追加されます。 テキスト ボックスの余白設定が 3.75 ポイント未満で、かろうじてテキストを表示するだけの幅を保っている場合、Excel ではそのテキストが折り返される場合があります。  
  
    > [!NOTE]  
    >  この問題を回避するには、レポートのテキスト ボックスの幅を大きくしてください。  
  
### <a name="images"></a>画像  
 画像には、次の制限事項が適用されます。  
  
-   レポート アイテムの背景画像は無視されます。Excel では、セルごとの背景イメージはサポートされていません。  
  
-   Excel 表示拡張機能では、レポート本文の背景画像のみがサポートされます。 レポート本文の背景画像をレポートに表示する際は、画像がワークシートの背景画像としてレンダリングされます。  
  
### <a name="rectangles"></a>四角形  
 四角形には、次の制限事項が適用されます。  
  
-   レポート フッターの四角形は Excel にエクスポートされません。 ただし、レポート本文、Tablix セルなどの四角形は、Excel のセル範囲としてレンダリングされます。  
  
### <a name="report-headers-and-footers"></a>レポートのヘッダーとフッター  
 レポートのヘッダーとフッターには、次の制限事項が適用されます。  
  
-   Excel のヘッダーとフッターでサポートされる最大文字数は 256 文字 (マークアップを含む) です。 文字列は、表示拡張機能により 256 文字で切り捨てられます。  
  
-   [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] は、レポートのヘッダーとフッターにおける余白をサポートしていません。 Excel へのエクスポート時に、これらの余白の値はゼロに設定され、複数行のデータを含むヘッダーやフッターは、プリンターの設定によっては複数行に印刷されない場合があります。  
  
-   ヘッダーやフッターのテキスト ボックスは、Excel へのエクスポート時にその書式が維持されますが、配置は維持されません。 これは、レポートが Excel にレンダリングされる際に先頭と末尾のスペースが切り捨てられるためです。  
  
### <a name="merging-cells"></a>セルの結合  
 セルの結合には、次の制限事項が適用されます。  
  
-   セルが結合されている場合、右端で折り返す機能は正常に機能しません。 AutoSize プロパティが設定されたテキスト ボックスが表示される行に結合セルが存在している場合、自動調整は適切に機能しません。  
  
 Excel レンダラーは、主にレイアウト レンダラーとして機能します。 その目的は、表示レポートのレイアウトを Excel ワークシートにできる限り忠実にレプリケートすることであり、その結果として、レポートのレイアウトを維持するためにセルが結合される場合があります。 Excel で並べ替えが適切に機能するためには、非常に特殊な方法でセルを結合する必要があるので、結合セルが問題となる可能性があります。 たとえば、Excel での並べ替えには、結合範囲のセルが同じサイズであることが必要です。  
  
 Excel ワークシートにエクスポートするレポートを並べ替えできるようにすることが重要である場合、Excel ワークシートで結合セルの数を減らすために、次の説明を参照してください。これは、Excel での並べ替え機能が複雑になる一般的な原因について説明したものです。  
  
-   レポート アイテムの左右の位置が揃っていないことが、結合セルが生じる最も一般的な原因となっています。 すべてのレポート アイテムの左右の位置を揃えるようにしてください。 レポート アイテムの位置を揃えて幅を等しくすることにより、多くの場合、この問題が解決します。  
  
-   すべてのレポート アイテムの位置を揃えても、一部の列が引き続き結合される場合があります。 この状態は、Excel ワークシートのレンダリング時に、Excel 内での単位変換と端数処理が原因で生じることがあります。 レポート定義言語 (RDL) では、インチ、ピクセル、センチメートル、ポイントなどのさまざまな測定単位で位置とサイズを指定できます。 ただし、Excel 内で使用する単位はポイントです。 変換の実行、およびインチやセンチメートルをポイントに変換する際の端数処理に伴う精度のずれを最小限に抑えるために、すべての測定値を整数単位のポイントで指定して、変換を経由しない直接的な結果が得られるようにすることを考慮してください。 1 インチは 72 ポイントです。  
  
### <a name="report-row-groups-and-column-groups"></a>レポートの行グループと列グループ  
 レポートに行グループまたは列グループが含まれている場合、レポートを Excel にエクスポートするときに空のセルが挿入されます。 たとえば、あるレポートで、販売ルートと郵便番号によって行をグループ化するとします。 各販売ルートには多数の郵便番号が含まれており、各郵便番号には多数の店舗名がリストされています。 次の図に、このレポートを示します。  
  
 ![rs_ExportExcelRpt](../media/rs-exportexcelrpt.gif "rs_ExportExcelRpt")  
  
 このレポートを Excel にエクスポートした場合、郵便番号の列の 1 つのセルにしか郵便番号が表示されません。 値は、レポート内でのテキストの配置 (上、中央、または下) に応じて、最初、中央、または最後のセルに表示されます。 その他のセルは空になります。 店舗名が格納されている列のセルは空になりません。 次の図に、Excel にエクスポートされた後のレポートを示します。 赤色のセル罫線は、強調のために追加されたもので、 エクスポートされたレポートには含まれません。  
  
 ![rs_ExportExcelBefore](../media/rs-exportexcelbefore.gif "rs_ExportExcelBefore")  
  
 このため、行グループまたは列グループが含まれているレポートを Excel にエクスポートしてピボット テーブルで表示する場合は、レポートの変更が必要です。 ワークシートをすべてのセルに値が設定されたフラット テーブルにするには、データが欠落しているセルにグループ値を追加する必要があります。 次の図に、更新したワークシートを示します。  
  
 ![rs_ExportExcelAfter](../media/rs-exportexcelafter.gif "rs_ExportExcelAfter")  
  
 レポート データを詳しく分析するために Excel にエクスポートするという特定の目的でレポートを作成した場合、レポートに行グループまたは列グループを含めないことを検討してください。  
  
## <a name="excel-renderer"></a>Excel レンダラー  
  
### <a name="excel-2007-2010-renderer"></a>Excel 2007-2010 レンダラー  
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]、既定の Excel レンダラーは、バージョンと互換性のある[!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)]2007-2010。 これは、レポート マネージャーおよび SharePoint リストの **[エクスポート]** メニューに用意されている **[Excel]** オプションです。  
  
 以前の Excel 2003 レンダラーの代わりに既定の Excel レンダラーを使用すると、Word/Excel/PowerPoint 用 Microsoft Office 互換機能パックをインストールして、エクスポートされたファイルを開くことができます。  
  
### <a name="excel-2003-renderer"></a>Excel 2003 レンダラー  
  
> [!IMPORTANT]  
>  [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] 2003 表示拡張機能の使用は推奨されません。 詳細については、次を参照してください。 [SQL Server 2014 における SQL Server Reporting Services の非推奨機能](../deprecated-features-in-sql-server-reporting-services-ssrs.md)します。  
  
 Excel 2003 と互換性のある Excel レンダラーの以前のバージョンは、Excel 2003 という名前になり、この名前がメニューに表示されます。 このレンダラーで生成されるファイルのコンテンツ タイプは **application/vnd.ms-excel** で、ファイル名の拡張子は .xls です。  
  
 既定では、 **[Excel 2003]** メニュー オプションは表示されません。 管理者が RSReportServer 構成ファイルを更新することで、特定の環境でこのメニュー オプションが表示されるようにできます。 Excel 2003 レンダラーを使用して [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] からレポートをエクスポートするには、RSReportDesigner 構成ファイルを更新します。  
  
 **[Excel 2003]** メニュー オプション拡張機能は、次のシナリオでは表示されません。  
  
-   レポート ビルダーが切断モードのときにレポート ビルダーでレポートをプレビューした場合。 RSReportServer 構成ファイルはレポート サーバー上に存在しているため、レポートをエクスポートするツールまたは製品が構成ファイルを読み取るためにレポート サーバーに接続されている必要があります。  
  
     これは、どちらも、[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]およびレポート ビルダーのスタンドアロン バージョンです。  
  
-   レポート ビューアー Web パーツがローカル モードで、SharePoint ファームが [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] レポート サーバーと統合されていない場合。 詳細については、「[レポート ビューアーでのローカル モードと接続モードのレポート &#40;Reporting Services の SharePoint モード&#41;](../local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)  
  
 **[Excel 2003]** メニュー オプション レンダラーが表示されるように構成されている場合は、Excel と Excel 2003 の両方のオプションが次の状況で使用可能になります。  
  
-   レポート マネージャー (Reporting Services がネイティブ モードでインストールされている場合)。  
  
-   SharePoint サイト (Reporting Services が SharePoint 統合モードでインストールされている場合)。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] でレポートをプレビューする場合。  
  
-   レポート ビルダーがレポート サーバーに接続されている場合。 これを[!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]またはレポート ビルダーのスタンドアロン バージョンです。  
  
-   リモート モードのレポート ビューアー Web パーツ。  
  
 次の XML は、RSReportServer 構成ファイルと RSReportDesigner 構成ファイルの 2 つの Excel 表示拡張機能の要素を示します。  
  
 `<Extension Name="EXCELOPENXML" Type="Microsoft.ReportingServices.Rendering.ExcelOpenXmlRenderer.ExcelOpenXmlRenderer,Microsoft.ReportingServices.ExcelRendering"/>`  
  
 `<Extension Name="EXCEL" Type="Microsoft.ReportingServices.Rendering.ExcelRenderer.ExcelRenderer,Microsoft.ReportingServices.ExcelRendering" Visible="false"/>`  
  
 EXCELOPENXML 拡張機能は Excel 2007-2010 用の Excel レンダラーを定義します。 EXCEL 拡張機能は、Excel 2003 バージョンを定義します。 `Visible = “false”` は、Excel 2003 レンダラーが非表示であることを示します。 詳細については、次を参照してください。 [RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md)と[RSReportDesigner Configuration File](../report-server/rsreportdesigner-configuration-file.md)します。  
  
### <a name="differences-between-the-excel-2007-2010-and-excel-2003-renderers"></a>Excel 2007-2010 レンダラーと Excel 2003 レンダラーの違い  
 Excel レンダラーまたは Excel 2003 レンダラーを使用して表示されるレポートは通常は同じですが、まれに 2 つの形式が異なる場合があります。 Excel レンダラーと Excel 2003 レンダラーの比較を次の表に示します。  
  
|プロパティ|Excel 2003|[エクスポート]|  
|--------------|----------------|-----------|  
|ワークシートあたりの最大列数|256|16,384|  
|ワークシートあたりの最大行数|65,536|1,048,576|  
|ワークシート内で使用できる色の数|56 (パレット)<br /><br /> レポートに使用されている色数が 56 色を超えている場合、必要な色が、あらかじめカスタム パレットに定義されている 56 色のいずれかと対応付けられます。|約 1,600 万色 (24 ビット カラー)|  
|ZIP 圧縮ファイル|なし|ZIP 圧縮|  
|既定のフォント ファミリ|Arial|Calibri|  
|既定のフォント サイズ|10 pt|11 pt|  
|既定の行の高さ|12.75 pt|15 pt|  
  
 レポートでは行の高さが明示的に設定されるため、既定の行の高さは、Excel へのエクスポート時にサイズが自動的に設定される行だけに作用します。  
  
##  <a name="ReportItemsExcel"></a> Excel のレポート アイテム  
 四角形、サブレポート、レポート本文、およびデータ領域は、Excel のセル範囲としてレンダリングされます。 テキスト ボックス、画像、グラフ、データ バー、スパークライン、マップ、ゲージ、およびインジケーターは、必ず単一の Excel セル内にレンダリングされます。レポートの他の部分のレイアウトによっては、セルが結合される場合もあります。  
  
 画像、グラフ、スパークライン、データ バー、マップ、ゲージ、インジケーター、および線は、単一の Excel セル内で、セル グリッドの一番上に来るように配置されます。 線はセル罫線としてレンダリングされます。  
  
 グラフ、スパークライン、データ バー、マップ、ゲージ、およびインジケーターは画像としてエクスポートされます。 グラフの値やメンバー ラベルなど、これらのアイテムが表すデータそのものは一緒にエクスポートされず、レポート内のデータ領域の列または行に含まれていない限り、Excel ブックでは使用できません。  
  
 グラフ、スパークライン、データ バー、マップ、ゲージ、およびインジケーターのデータを操作する場合は、レポートを .csv ファイルにエクスポートするか、レポートから Atom 準拠のデータ フィードを生成します。 詳細については、「[CSV ファイルへのエクスポート &#40;レポート ビルダーおよび SSRS&#41;](exporting-to-a-csv-file-report-builder-and-ssrs.md)」および「[複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](generating-data-feeds-from-reports-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="page-sizing"></a>ページのサイズ設定  
 Excel 表示拡張機能では、ページの高さ設定と幅設定を使って、Excel ワークシートで定義する用紙設定が決定されます。 まず、PageHeight プロパティと PageWidth プロパティの設定が、最も一般的ないずれかの用紙サイズと比較されます。  
  
 一致するものが見つからなかった場合は、プリンターの既定のページ サイズが使用されます。 用紙方向は、ページの幅が高さよりも小さければ [縦] に、それ以外の場合は [横] に設定されます。  
  
##  <a name="WorksheetTabNames"></a> ワークシートのタブ名  
 レポートを Excel ファイルにエクスポートすると、改ページによって生じたレポートの各ページが別々のワークシートにエクスポートされます。 レポートの最初のページ名を指定した場合、既定では、その Excel ワークブックの各ワークシートにこの名前が使用されます。 名前は、ワークシートのタブに表示されます。ただし、ワークブック内の各ワークシートは一意の名前を使用する必要があるため、追加のワークシートごとに 1 から開始され昇順に 1 ずつ増加する整数値がワークブック名に追加されます。 たとえば、最初のページ名が **"会計年度ごとの売り上げレポート"** である場合、2 番目のワークシート名は **"会計年度ごとの売り上げレポート1"**、3 番目のワークシート名は **"会計年度ごとの売り上げレポート2"** となります。  
  
 改ページによって生じたすべてのレポート ページに新しいページ名がある場合は、各ワークシートには関連するページ名が付けられます。 ただし、これらのページ名が一意でない場合があります。 ページ名が一意でない場合、ワークシートには最初に説明したページ名と同じ方法で名前が付けられます。 たとえば、2 つのグループのページ名が **"東北部の売り上げ"** である場合、1 つのワークシートに **"東北部の売り上げ"** という名前が付けられ、もう一方のワークシートには **"東北部の売り上げ1"** という名前が付けられます。  
  
 レポートに、最初のページ名も改ページに関連付けられたページ名もない場合、ワークシートのタブには、**"シート1"**、**"シート2"** と順番に続く既定の名前が使用されます。  
  
 Reporting Services には、ユーザーが指定する方法で Excel にエクスポートできるレポートの作成を支援するために、レポート、データ領域、グループ、および四角形に設定するプロパティが用意されています。 詳細については、「 [Reporting Services の改ページ (レポート ビルダーおよび SSRS)](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)」を参照してください。  
  
##  <a name="DocumentProperties"></a> ドキュメント プロパティ  
 Excel レンダラーでは、次のメタデータが Excel ファイルに書き込まれます。  
  
|レポート要素のプロパティ|Description|  
|-------------------------------|-----------------|  
|Created|レポート実行の日付と時刻 (ISO 形式の日付/時刻値)。|  
|Author|Report.Author|  
|Description|Report.Description|  
|LastSaved|レポート実行の日付と時刻 (ISO 形式の日付/時刻値)。|  
  
##  <a name="PageHeadersFooters"></a> ページ ヘッダーとページ フッター  
 デバイス情報の SimplePageHeaders 設定に応じて、ページ ヘッダーは、ページ ヘッダーを各ワークシートのセル グリッドの上部に表示するか、または実際の Excel ワークシートのヘッダー セクションに表示するという、2 つの方法で表示可能です。 既定では、ヘッダーが Excel ワークシートのセル グリッドにレンダリングされます。  
  
 ページ フッターは、SimplePageHeaders 設定の値に関係なく、常に Excel ワークシートの実際のフッター セクションにレンダリングされます。  
  
 Excel のヘッダー セクションとフッター セクションでサポートされる最大文字数は 256 文字 (マークアップを含む) です。 この制限を超えた場合、Excel レンダラーは、文字数の合計を減らすために、ヘッダー文字列またはフッター文字列の終端位置を起点として、マークアップ文字を削除します。 マークアップ文字をすべて削除しても最大文字数を超えていた場合、文字列が右側から切り詰められます。  
  
### <a name="simplepageheader-settings"></a>SimplePageHeader の設定  
 既定では、デバイス情報の SimplePageHeaders 設定に設定`False`。 したがって、ページ ヘッダーは、Excel ワークシート領域にレポート内の行として表示されます。 ヘッダーが格納されるワークシートの行はロックされます。 Excel のウィンドウ枠は固定することも、固定を解除することもできます。  
  
> [!NOTE]  
>  Excel の **[印刷タイトル]** オプションが選択されている場合、すべてのワークシート ページについて、これらのヘッダーが印刷されるように自動的に設定されます。  
>   
>  Excel の [ページ レイアウト] タブの **[印刷タイトル]** オプションが選択されている場合、ページ ヘッダーは、ドキュメント マップの表紙を除く、ブック内のすべてのワークシートの最上部に表示されます。  
  
 [レポート ヘッダーのプロパティ] ダイアログ ボックスまたは [レポート フッターのプロパティ] ダイアログ ボックスで、 **[最初のページに印刷する]** オプションまたは **[最後のページに印刷する]** オプションが選択されていなかった場合、最初または最後のページにはヘッダーが追加されません。  
  
 ページ フッターは、Excel のフッター セクションにレンダリングされます。  
  
 Excel の制限により、Excel のヘッダー/フッター セクションにレンダリングできるレポート アイテムはテキスト ボックスだけです。  
  
##  <a name="Interactivity"></a> 対話性  
 Excel では、いくつかの対話型要素がサポートされています。 具体的な動作について説明します。  
  
### <a name="show-and-hide"></a>表示/非表示  
 [!INCLUDE[ofprexcel](../../../includes/ofprexcel-md.md)] には、表示と非表示の切り替えができるレポート アイテムの、エクスポート時の扱いに関して制限があります。 表示と非表示の切り替えが可能なレポート アイテムを含んだグループ、行、および列は、Excel のアウトラインとしてレンダリングされます。 アウトラインでは、行全体または列全体を展開したり折りたたんだりできますが、それが原因で、意図していないレポート アイテムまで折りたたんで表示されてしまうことがあります。 また、アウトラインが重なり合うことによって、Excel のアウトライン記号が散在し、わかりにくくなってしまう場合もあります。 Excel 表示拡張機能では、こうした問題を解消するために、アウトラインに関して次の規則が適用されます。  
  
-   左上隅に存在する、表示と非表示の切り替えが可能なレポート アイテムは、Excel でも引き続き表示と非表示の切り替えができます。 表示と非表示の切り替えが可能なレポート アイテムが左上隅にあり、そのレポート アイテムと水平方向または垂直方向の領域を共有して、表示と非表示の切り替えが可能な別のレポート アイテムがある場合、後者のレポート アイテムについては、Excel での表示と非表示の切り替えができなくなります。  
  
-   データ領域の折りたたみを行方向とするか、列方向とするかを決定するために、切り替えを制御するレポート アイテムの位置と、切り替え対象であるレポート アイテムの位置が判定されます。 切り替えを制御しているアイテムが、切り替え対象であるアイテムよりも前にある場合、そのアイテムには行方向の折りたたみが適用されます。 それ以外の場合は、列方向の折りたたみが適用されます。 切り替え対象となる領域に対して、切り替えを制御しているアイテムの位置が、等しく横でも上でもある場合、そのアイテムのレンダリングには、行方向の折りたたみが適用されます。  
  
-   表示拡張機能は、レンダリングしたレポートのどこに小計を配置するかを決定するために、最初に出現する動的メンバーを調べます。 そのすぐ上に、対応する静的メンバーがある場合、その動的メンバーは小計であると見なされます。 また、これが集計データであることを示すためのアウトラインが設定されます。 動的メンバーに対応する静的なメンバーが存在しなかった場合、最初の動的メンバーが小計と見なされます。  
  
-   Excel の制限により、アウトラインの入れ子レベルは最大 7 です。  
  
### <a name="document-map"></a>ドキュメント マップ  
 レポートにドキュメント マップ ラベルが存在する場合、そのドキュメント マップがレンダリングされます。 ドキュメント マップは、表紙の Excel ワークシートとして、ブックの最初のタブ位置に挿入され、レンダリングされます。 ワークシートには、**"Document map"** という名前が付けられます。  
  
 ドキュメント マップに表示されるテキストは、レポート アイテムまたはレポート グループの DocumentMapLabel プロパティによって決まります。 ドキュメント マップ ラベルは、先頭列の先頭行を起点とし、レポートにおける出現順に一覧表示されます。 各ドキュメント マップ ラベルのセルは、レポートでの見出しの階層に合わせてインデントされます。 それぞれのインデント レベルは、ラベルを後続の列に配置することによって表現されます。 Excel でサポートされるアウトラインの入れ子レベルは、最大 256 です。  
  
 ドキュメント マップのアウトラインは、折りたたみ可能な Excel アウトラインとしてレンダリングされます。 アウトライン構造は、ドキュメント マップの入れ子構造と一致します。 アウトラインの展開と折りたたみは、第 2 レベルからとなります。  
  
 マップのルート ノードはレポート名 \<*reportname*>.rdl で、これを対話的に操作することはできません。 ドキュメント マップ リンクのフォントは Arial (10 ポイント) です。  
  
### <a name="drillthrough-links"></a>ドリルスルー リンク  
 テキスト ボックス内にあるドリルスルー リンクは、テキストが表示されるセルに Excel ハイパーリンクとしてレンダリングされます。 画像やグラフのドリルスルー リンクは、Excel ハイパーリンクとして、画像上にレンダリングされます。 クリックすると、クライアントの既定のブラウザーが起動し、対象となる HTML が表示されます。  
  
### <a name="hyperlinks"></a>ハイパーリンク  
 テキスト ボックス内にあるハイパーリンクは、テキストが表示されるセルに Excel ハイパーリンクとしてレンダリングされます。 画像やグラフのハイパーリンクは、Excel ハイパーリンクとして、画像上にレンダリングされます。 クリックすると、クライアントの既定のブラウザーが起動し、対象の URL に移動します。  
  
### <a name="interactive-sorting"></a>対話的な並べ替え  
 Excel では、対話的な並べ替えがサポートされません。  
  
### <a name="bookmarks"></a>ブックマーク  
 テキスト ボックス内のブックマーク リンクは、テキストが表示されるセルに Excel ハイパーリンクとしてレンダリングされます。 画像やグラフのブックマーク リンクは、Excel ハイパーリンクとして、画像上にレンダリングされます。 クリックすると、ブックマークが付けられたレポート アイテムの Excel セルに移動します。  
  
##  <a name="ConditionalFormat"></a> 実行時のレポートの変更  
 レポートを複数の形式で表示する必要があるにもかかわらず、必要なすべての形式で目的どおりに表示されるレポート レイアウトを作成することができない場合は、組み込みの RenderFormat グローバルの値を使用して、レポートの外観を実行時に条件に応じて変更するようにしてください。 この方法により、使用するレンダラーに応じてレポート アイテムの表示/非表示を切り替えて、それぞれの形式で最適な結果を得ることができます。 詳細については、「[組み込み Globals および Users 参照 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/built-in-collections-built-in-globals-and-users-references-report-builder.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [さまざまなレポート表示拡張機能の対話機能 &#40;レポート ビルダーおよび SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [レポート アイテムのレンダリング &#40;レポート ビルダーおよび SSRS&#41;](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  