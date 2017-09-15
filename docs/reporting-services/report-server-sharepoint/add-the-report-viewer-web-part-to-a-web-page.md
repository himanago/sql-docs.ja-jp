---
title: "Web ページにレポート ビューアー Web パーツを追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SharePoint integration [Reporting Services], viewing reports
- Web Parts [Reporting Services]
- SharePoint integration [Reporting Services], Web Parts
- Report Viewer Web Part [Reporting Services]
ms.assetid: cac75345-2380-467d-a394-0a2140908a5a
caps.latest.revision: 13
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 0fd8adf79a7eeccb66b5efd6fc90e1312020973a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="add-the-report-viewer-web-part-to-a-web-page"></a>レポート ビューアー Web パーツを Web ページに追加する
  レポート ビューアー Web パーツを使用することで、SharePoint 統合モード用に構成されているレポート サーバーで実行されるレポートを表示できます。 この Web パーツでは、レポート ビルダーまたはレポート デザイナーで作成してライブラリにアップロードしたレポート定義ファイル (.rdl) を表示できます。  
  
 Web ページにレポート ビューアー Web パーツを追加することで、Web ページにレポートを埋め込むことができます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインによってインストールされるレポート ビューアー Web パーツと、RSWebParts.cab ファイルに含まれているレポート ビューアー Web パーツは、名前は同じでも異なるものです。 このトピックでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインを使用してインストールされるレポート ビューアー Web パーツを利用するための手順について説明します。  
  
 Web パーツを Web ページに追加するには、サイト レベルでの "ページの追加とカスタマイズ" 権限が必要です。 既定のセキュリティ設定を使用する場合、この権限はフル コントロール レベルの権限を持つ **所有者** グループのメンバーに与えられます。  
  
### <a name="to-embed-a-report-in-a-web-page"></a>Web ページにレポートを埋め込むには  
  
1.  Web パーツ ページまたはダッシュボードを開くか、作成します。  
  
2.  **[サイトの操作]**の **[ページの編集]**をクリックします。  
  
3.  **[Web パーツの追加]**をクリックします。  
  
4.  Web パーツ カテゴリの一覧で、 **[その他]** カテゴリをクリックし、 **[SQL Server Reporting Services レポート ビューアー]**をクリックします。  
  
5.  **[追加]**をクリックします。 Web パーツが、ゾーンの一番上に追加されます。 Web パーツは、ドラッグして、領域内の別の場所に移動できます。  
  
6.  ビューアー内で、 **[ツール ペインを開くにはここをクリックします]**をクリックします。  
  
7.  参照ボタン (**[...]**) をクリックして、現在のサイト コレクションの任意のライブラリにあるレポートを選択します。 レポートの URL を入力することもできます。 レポートの URL を調べるには、レポートを右クリックし、 **[プロパティ]**をクリックします。 レポートの横にある下向きの矢印アイコンはクリックしないでください。アイテムの [プロパティの表示] ページでは、レポートの URL は表示されません。 **[プロパティ]** ダイアログ ボックスで URL をコピーし、貼り付ける場合には、URL 内の "%20" をスペースに置き換えてください (たとえば、"Company%20Sales" は "Company Sales" にします)。  
  
    > [!NOTE]  
    >  1 つのレポート ビューアー Web パーツには、1 つのレポートが格納されます。 URL は、現在の SharePoint サイト、または同じ Web アプリケーションやファーム内のサイト上のレポートへの完全修飾パスで指定する必要があります。 この URL は、ドキュメント ライブラリとして解決されるか、ドキュメント ライブラリ内でレポートが格納されるフォルダーとして解決される必要があります。 レポート URL には、ファイル拡張子 .rdl を含める必要があります。 レポートがモデル ファイルまたは共有データ ソース ファイルに依存している場合、URL でそのファイルを指定する必要はありません。 必要なファイルへの参照は、レポートに含まれています。  
  
8.  開いているツール ペインでプロパティを設定し、既定の外観とレイアウトを変更します。  
  
9. ツール ペインの下部で **[適用]** をクリックし、 **[OK]** をクリックしてペインを閉じます。  
  
## <a name="see-also"></a>参照  
 [SharePoint サイトのレポート ビューアー Web パーツ](../../reporting-services/report-server-sharepoint/report-viewer-web-part-on-a-sharepoint-site.md)   
 [レポート ビューアー Web パーツをカスタマイズします。](../../reporting-services/report-server-sharepoint/customize-the-report-viewer-web-part.md)   
 [SharePoint サイト上のレポート サーバー アイテムに対する権限の許可](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)   
 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)  
  
  