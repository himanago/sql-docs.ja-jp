---
title: "レポート サーバーにパブリッシュするレポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/01/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- production environments [Reporting Services]
- report projects [Reporting Services]
- Debug configuration [Reporting Services]
- report publishing [Reporting Services]
- publishing reports [Reporting Services]
- report properties [Reporting Services]
- Report Designer [Reporting Services], deploying reports
- Production configuration [Reporting Services]
- publishing reports [Reporting Services], production environments
- DebugLocal configuration [Reporting Services]
- deploying [Reporting Services], reports
- Report Designer [Reporting Services], publishing reports
ms.assetid: bd7aa5e0-61ce-43fd-8f74-5d1aeed078bb
caps.latest.revision: 47
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7f7e44b6527c90419e5ae220260ab08a706c2372
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="publishing-reports-to-a-report-server"></a>レポート サーバーへのレポートのパブリッシュ
  1 つまたは複数のレポートのデザインおよびテストが完了したら、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の組み込みのデプロイ機能を使用してレポート サーバーにレポートをパブリッシュします。 個々のレポート、または複数のレポートとデータ ソースを含めることができるレポート サーバー プロジェクトを発行することができます。 複数のレポートをパブリッシュする最も簡単な方法は、レポート サーバー プロジェクトをパブリッシュする方法です。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、" *パブリッシュ*" の代わりに、" *配置*" という用語が使用されます。 この 2 つの用語は同義です。  
  
 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、レポートのパブリッシュを管理するためのプロジェクト構成が提供されます。 構成では、レポート サーバーの場所、レポート サーバーにインストールされている SQL Server Reporting Services のバージョンのほか、レポートにパブリッシュされたデータ ソースは上書きされるかどうかなどが指定されます。 たとえば、"デバッグ" 構成を "リリース" 構成とは別のサーバーにパブリッシュできます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] が提供する構成を使用する他に、構成を追加作成することもできます。  
 
## <a name="requirements-to-publish"></a>パブリッシュの要件
この権限は、レポート サーバー管理者が定義するロールベースのセキュリティによって決まります。 パブリッシュ操作は、通常、 **パブリッシャー ロール**を介して許可されます。  
  
## <a name="project-configurations"></a>プロジェクトの構成  
 ご使用のレポート環境に、複数のレポート サーバーが含まれる場合や異なるバージョンの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がインストールされている場合は、 複数の構成を作成し、配置シナリオに応じて異なる構成を使用できます。 プロジェクト構成には、ビルド レポートを一時的に保存するフォルダー、ビルドの問題の対処方法など、レポートをビルドするためのプロパティが含まれます。 構成には、レポート サーバーの場所やバージョン、レポート サーバー上のフォルダーの指定に使用されるプロパティも含まれます。  
  
 既定で、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、 **DebugLocal**、 **Debug**、 **Release**の 3 つの構成が提供されます。 既定の構成は DebugLocal です。 通常、DebugLocal 構成はローカル プレビュー ウィンドウでのレポートの表示に、Debug 構成はテスト サーバーへのレポートのパブリッシュに、Release 構成は実稼働サーバーへのレポートのパブリッシュに使用できます。 標準ツール バーの [ソリューション構成] ドロップダウン リストには、アクティブな構成が表示されます。 別の構成を使用するには、一覧からその構成を選択します。  
  
 ![ssrs_project_properties](../../reporting-services/reports/media/ssrs-project-properties.png) 
  
 詳細については、以下を参照してください。
 + [[プロパティ ページ] ダイアログ ボックス](../../reporting-services/tools/project-property-pages-dialog-box.md)
 + [Deployment and Version Support in SQL Server Data Tools](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)
 + [配置プロパティを設定する (Reporting Services)](../../reporting-services/tools/set-deployment-properties-reporting-services.md)
  
## <a name="to-publish-all-reports-in-a-project"></a>プロジェクトのすべてのレポートをパブリッシュするには  
  
**ビルド** メニューのをクリックして**展開\<レポート プロジェクト名 >**です。 または、ソリューション エクスプローラーでレポート プロジェクトを右クリックして、 **[配置]**をクリックします。 パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。  
  
レポート サーバー プロジェクトを配置すると、レポート プロジェクトの共有データ ソースも配置されます。 すべてのレポートは、同じプロジェクト構成を使用して同じレポート サーバー、サーバー上の同じフォルダーというように配置されます。 異なるサーバーにレポートを配置するには、これらのレポートを 1 つずつパブリッシュするか、レポート サーバー プロジェクトに必要なレポートのみを含めます。 ソリューションには、複数のレポート サーバー プロジェクトを含めることができます。複数のプロジェクトを使用すると、異なる構成を使用してさまざまなプロジェクトを配置できるため、レポートの配置を簡単に管理できます。 
  
## <a name="to-publish-a-single-report"></a>1 つのレポートをパブリッシュするには  
  
ソリューション エクスプローラーで、レポートを右クリックし、 **[配置]**をクリックします。 パブリッシュ処理の状態が、[出力] ウィンドウに表示されます。  
  
 レポートをパブリッシュするときは、レポートが使用する共有データ ソースを配置する必要もあります。   
 プロジェクト内のすべてのレポートをパブリッシュしない場合、単一のレポートのみのパブリッシュを選択できます。 この操作を行うには、レポートを配置する構成 (たとえば、Release 構成など) を選択し、レポートを右クリックして、 **[配置]**をクリックします。  
  
 レポートが共有データ ソースを使用する場合は、共有データ ソースを配置する必要もあります。共有データ ソースを配置しないと、配置されたレポートが実行されません。 共有データ ソースを右クリックし、 **[配置]**をクリックします。  
  
 レポート サーバーのターゲット サーバー URL を指定する必要があります。レポートおよび共有データ ソースが配置される既定のフォルダーは変更できます。  

  
## <a name="see-also"></a>参照  
 [[プロパティ ページ] ダイアログ ボックス](../../reporting-services/tools/project-property-pages-dialog-box.md)   
 [レポート サーバー コンテンツの管理と &#40; です。SSRS ネイティブ モードと &#41; です。](../../reporting-services/report-server/report-server-content-management-ssrs-native-mode.md)   
 [レポートのアップグレード](../../reporting-services/install-windows/upgrade-reports.md)  
  
  
