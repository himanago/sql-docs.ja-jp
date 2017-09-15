---
title: "CRI の変換 ダイアログ ボックス (レポート ビルダー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- "10008"
helpviewer_keywords:
- CRI
- custom report items
ms.assetid: 2a3f2ac6-667e-4498-8b73-9c40beb993f5
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 37ba742708ded98cd5728a3051a2e7a76b9fa99f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="convert-cri-dialog-box-report-builder"></a>[CRI の変換] ダイアログ ボックス (レポート ビルダー)
  このレポートにはサポートされていない機能を持つカスタム レポート アイテム (CRI) が含まれています。 CRI は、レポートにデータを表示するカスタム オブジェクトをサポートするレポート定義言語 (RDL) の拡張機能です。 CRI には、サードパーティのソフトウェア ベンダーによって提供されるデザイン時コンポーネントおよび実行時コンポーネントが含まれます。  
  
> [!NOTE]  
>  システム管理者は、レポート サーバーでカスタム レポートをサポートするかどうかを選択します。 レポートで CRI を表示するには、CRI コンポーネントをレポートのプレビューのためにレポート作成クライアントに、およびパブリッシュまたはアップロードされたレポートを表示するためにレポート サーバーにインストールする必要があります。  
  
 新しいレポート定義形式のレポート アイテムに変換できる CRI もあります。 レポートを開くときに、アップグレードするかどうかを確認するメッセージが表示されます。 次の情報に従って、このレポートの CRI を変換するかどうかを決定します。  
  
-   **[する]** 可能であればレポート内のすべての CRI を変換する場合に、 **[する]** を選択します。 CRI でサポートされていない機能はアップグレードできません。レポート定義ファイルから削除されます。 サポートされていない機能の一覧については、「 [レポートのアップグレード](../../reporting-services/install-windows/upgrade-reports.md)」を参照してください。 レポートを表示すると、CRI がレポートに表示される方法に違いが見られます。  
  
-   **[しない]** レポートの CRI を変換しない場合に **[しない]** を選択します。 現在のバージョンでは、レポート プロセッサはこれらの CRI を表示できません。 システム管理者が、サードパーティのソフトウェア ベンダーから新しいレポート定義形式と互換性のある CRI の新しいバージョンのインストールを計画している場合、 **しない**を選択する必要があります。 新しいバージョンが使用可能になるまで、CRI はレポート内で赤い X のある空白テキスト ボックスとして表示されます。  
  
 どちらの場合、レポートは、新しいレポート定義形式にアップグレードされ、として、元のレポートのバックアップ コピーを保存*\<レポート名 >* `-` Backup.rdl です。 レポート作成ツールにレポートを保存する場合、新しいレポート定義形式でアップグレードされたレポートを保存することになります。 レポートをパブリッシュする場合、レポートはまずコンピューターに保存され、それからレポート サーバーにパブリッシュされます。 レポートのアップグレード バージョンをレポート サーバーにパブリッシュします。  
  
 レポートを保存しない場合、元のレポートは変更されません。 ただし、 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降のバージョンの [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] か、このレポート定義形式を使用するレポート作成環境では、このレポートは編集できません。 レポート マネージャーを使用して [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーにアップロードすることで、レポートの元のバージョンを継続して実行できます。 詳細については、「[ファイルまたはレポートのアップロード &#40;レポート マネージャー&#41;](../../reporting-services/reports/upload-a-file-or-report-report-manager.md)」を参照してください。  
  
 レポートをレポート サーバーにパブリッシュする代わりに、アップロードする場合、レポート プロセッサはそのレポートを最初の使用時にアップグレードできるかどうかを決定します。 アップグレードできないレポートは下位互換性モードで処理され、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]の以前のバージョンと同じように表示されます。 詳細については、「 [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md)」を参照してください。  
  
 レポート、レポート サーバー、またはレポート作成環境の現在のレポート定義形式を特定するには、「[Find the Report Definition Schema Version (SSRS)](../../reporting-services/reports/find-the-report-definition-schema-version-ssrs.md)」(レポート定義スキーマのバージョンを確認する (SSRS)) を参照してください。  
  
## <a name="see-also"></a>参照  
 [レポート ビルダー ダイアログ ボックス、ペイン、およびウィザードに関するヘルプ](http://msdn.microsoft.com/en-us/2da24891-0b6d-4d3c-8b18-81b98752642f)  
  
  