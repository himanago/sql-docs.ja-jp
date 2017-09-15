---
title: "サービスをファームに Web フロント エンドの追加のレポートの追加 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7a11bda-ae26-49ac-b071-37d83cae5afe
caps.latest.revision: 11
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: a17e4965637841339d34d7842b0df1bea5f7757f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="add-an-additional-reporting-services-web-front-end-to-a-farm"></a>ファームへの Reporting Services Web フロントエンドの追加
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モードには、アプリケーション サーバーと Web フロントエンド (WFE) サーバーに必要なコンポーネントが含まれています。 このトピックでは、WFE サーバーに必要な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントのインストールに焦点を当てます。これらのコンポーネントには、サブスクリプション、データ警告、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] など、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]機能で使用されるアプリケーション ページが含まれます。 WFE に必要な主要な [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インストールは、SharePoint 2016 製品用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインをインストールすることです。  
  
## <a name="prerequisites"></a>前提条件  
  
-   SQL Server セットアップを実行するには、ローカル管理者である必要があります。  
  
-   コンピューターがドメインに参加する必要があります。  
  
-   SharePoint の構成データベースとコンテンツ データベースをホストしている既存のデータベース サーバーの名前を把握しておく必要があります。  
  
-   データベース サーバーは、リモート データベース接続を許可するように構成されている必要があります。  構成されていない場合は、新しいサーバーが SharePoint 構成データベースに接続できないため、新しいサーバーをファームに参加させることができません。  
  
-   新しいサーバーのバージョンは、現在のファーム サーバーが実行されているインストール済みの SharePoint のバージョンと同じである必要があります。 たとえば、SharePoint 2013 Service Pack 1 (SP1) が既にファームにインストールされている場合は、新しいサーバーをファームに参加させる前に、新しいサーバーにも SP1 をインストールする必要があります。  
  
## <a name="steps"></a>手順  
 このトピックの手順では、SharePoint ファームの管理者がサーバーをインストールして構成すると想定しています。 この図は標準的な 3 層環境を示しています。次に、図の番号付き項目の説明を示します。  
  
-   (1) 複数の Web フロントエンド (WFE) サーバー。 WFE サーバーには、SharePoint 2010 用の [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] アドインが必要です。 次の手順では、この層に 2 つ目のアプリケーション サーバーを追加します。  
  
-   (2) [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] と Web サイトを実行している 2 つのアプリケーション サーバー。たとえば、サーバーの全体管理などです。  
  
-   (3) 2 つの SQL Server データベース サーバー。  
  
-   (4) ソフトウェアまたはハードウェアのネットワーク負荷分散ソリューション (NLB) を表します。  
  
 ![SSRS を新しい SharePoint WFE に追加](../../reporting-services/install-windows/media/rs-sharepointscale-wfe.gif "新しい SharePoint WFE に SSRS の追加")  
  
 次の手順では、管理者がサーバーをインストールして構成すると想定しています。  
  
|手順|説明とリンク|  
|----------|--------------------------|  
|SharePoint サーバーをファームに追加します。|別の Reporting Services アプリケーションをデプロイするには、SharePoint をインストールする必要があります。<br/><br/>SharePoint 2013 の場合は、 [SharePoint Server 2013 での SharePoint サーバーのファームへの追加](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)に関する記事を参照してください。<br/><br/>SharePoint 2016 の場合は、 [SharePoint Server 2016 での SharePoint サーバーのファームへの追加](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)に関する記事を参照してください。|  
|SharePoint 2016 製品用の SQL Server Reporting Services アドインをインストールします。|アドインをインストールするには、いくつかの方法があります。 次の手順では、SQL Server セットアップ ウィザードを使用します。 アドインのインストール方法の詳細については、「 [SharePoint 用 Reporting Services アドインのインストールまたはアンインストール](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)」を参照してください。<br /><br /> 1) SQL Server のインストールを実行します。<br /><br /> 2) **[セットアップ ロール]** ページで、 **[SQL Server 機能のインストール]**を選択します。<br /><br /> 3) **[機能の選択]** ページで、 **[SharePoint 製品用 Reporting Services アドイン]**を選択します。<br /><br /> 4) 次のいくつかのページで **[次へ]** をクリックし、セットアップ オプションを完了します。<br /><br/>[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]のインストールの詳細については、「 [SharePoint モードでの最初のレポート サーバーのインストール](http://msdn.microsoft.com/en-us/b29d0f45-0068-4c84-bd7e-5b8a9cd1b538)」をご覧ください。|  
|新しいサーバーが稼働することを確認します。|1) SharePoint サーバーの全体管理で、 **[システム設定]** の **[このファームのサーバーの管理]** をクリックします。<br /><br /> 2) 新しいサーバーが一覧に含まれていることを確認します。|  
|NLB ソリューションを更新します。|該当する場合は、ハードウェアまたはソフトウェア NLB 環境を更新し、新しいサーバーを環境に含めます。|  

## <a name="next-steps"></a>次の手順

[SharePoint Server 2016 での SharePoint サーバーのファームへの追加](https://technet.microsoft.com/library/cc261752(v=office.16).aspx)  
[SharePoint Server 2013 での SharePoint サーバーのファームへの追加](https://technet.microsoft.com/library/cc261752(v=office.15).aspx)

他に質問しますか。 [Reporting Services のフォーラムで質問してみてください。](http://go.microsoft.com/fwlink/?LinkId=620231)